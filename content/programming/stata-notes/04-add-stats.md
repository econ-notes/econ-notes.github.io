---
title: 'Regression tables: Adding more statistics'
date: '2025-12-21'
---

## 1. Putting statistics after the coefficients region

- This is achieved by `estadd` command.
  - For a scalar statistic, use `estadd scalar`.
  - For a qualitative statistic, e.g., whether the regression contains certain control variables, use `estadd local`.
- After storing the specific statistics, when producing the regression table, use `stats()` option to control which statistics to present, their labels, and their formats.

```stata
summarize var if treatment==0
    local cmean = r(mean)

areg outcome treatment1 treatment2 controls, absorb(fixed_effects) cluster(clusterid)
    eststo model1
    estadd scalar cmean = `cmean'
    estadd local FixedEffects "\multicolumn{1}{c}{Y}"
    test _b["treatment1"] = _b["treatment2"]
    estadd scalar diff_p = r(p)

global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles       "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2}  & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_file         "${Results}/test.tex"

esttab reg1 reg2 reg3 reg4 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(4) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(treatment1 treatment2) order(treatment1 treatment2) varlabels(treatment1 "label1" treatment2 "label2") ///
    stats(r2 cmean N diff_p FixedEffects, labels("R-squared" "Control Mean" "Obs" "\midrule treatment1=treatment2" "\midrule Fixed Effects") fmt(%9.3f %9.3f %9.0g %9.3f %9.0f)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}") ///
    posthead("${latex_numbers}" "${latex_titles}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}" "\begin{tablenotes}" "\footnotesize" "\item" "Notes." "\end{tablenotes}")
```

## 2. Reporting transformed statistics in the coefficients region

Sometimes, in a regression of outcome $y$ against three regressors: $x_1$, $x_2$, and $x_3$. 
However, In the regression table, we may with to report the estimated coefficient on $x_1$ an on $x_3 - x_2$.
This functionality is achieved by the `xlincom` package.

### 2.1. Estimating the equations
Notes:
- We must add the `post` option to the `xlincom` command.
- Depending on the location of the transformed coefficients, the resulting coefficients will be named as `lc_1`, `lc_2`, etc.
- We should save the results after running the `xlincom` command.

```stata
local i = 1
foreach y in $var_list {

    reghdfe `y' x1 x2 x3, absorb(${controls}) cluster(clusterid)
        local r_squared = e(r2)
        summarize `y' if e(sample)==1 & x1==1
            local cmean = r(mean)
        xlincom (x1) (x3-x2), post
            eststo reg`i'
            estadd scalar cmean = `cmean'
            estadd scalar r_squared = `r_squared'

    local i = `i' +1
}
```

### 2.2. Producing the regression table

Notes:
- The only change to the `esttab` command is the coefficients to be reported.
- We can use the additional `varlabels()` option to attach variable labels to the transformed coefficients.

```stata {hl_lines=14}
global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles       "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2}  & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_file         "${Results}/test.tex"

esttab reg1 reg2 reg3 reg4 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(4) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(lc_1 lc_2) order(lc_1 lc_2) varlabels(lc_1 "label1" lc_2 "label2") ///
    stats(cmean r_squared N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}") ///
    posthead("${latex_numbers}" "${latex_titles}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}")
```