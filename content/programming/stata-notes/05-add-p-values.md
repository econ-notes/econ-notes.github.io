---
title: 'Regression tables: Adding more statistics'
date: '2025-12-23'
---

## Add more statistics to the coefficients region

- This is achieved by the `estadd matrix` command.
- Note that the matrix should have the same column names as the variables to which the new statistics should be associated with.

```stata

*&& calculate rip
* Store coefficient-level statistics as a matrix 1 by k matrix with appropriate colnames (they should be the same as the variable name of the regressors) 
randcmdci areg outcome treatment controls, absorb(fixed_effects) cluster(clusterid) groupvar(clusterid) reps(1000) seed(1) treatvars(treatment) testvars(treatment) 
    matrix rip = e(HB)["treatment", "rand-p"]
    matrix colnames rip = "treatment"

*&& the main regression
* Store estimation results, including coefficient-level statistics using estadd matrix  
areg outcome treatment controls, absorb(fixed_effects) cluster(clusterid) 
    eststo model1
    estadd matrix rip

*&& produce the latex table

global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles       "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2} & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_file         "${Results}/test.tex"

esttab model1 model2 model3 model4 using ${latex_file}, ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(4) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(treatment) order(treatment) varlabels(treatment "label") ///
    cells(b(fmt(3)) se(fmt(2) par("(" ")")) p(fmt(3) par("[" "]")) rip(fmt(3) par("\{" "\}"))) ///
    stats(r2 N, labels("R-squared" "Obs") fmt(%9.3f %9.0g)) ///
    prehead("${latex_star}$" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}") ///
    posthead("${latex_numbers}" "${latex_titles}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}")
```



