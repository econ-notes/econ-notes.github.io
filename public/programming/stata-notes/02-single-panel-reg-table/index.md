# Regression Tables: Producing a Single-Panel Regression Table


## 0. Useful code snippets

The following are some useful code snippets.

```stata
& \multicolumn{1}{c}{outcome}
& \multicolumn{1}{c}{\shortstack{Long \\ name}} 

\cmidrule(lr){2-3} \cmidrule(lr){4-5}
\addlinespace[10pt]
[7pt]

& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} & \multicolumn{1}{c}{(5)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} & \multicolumn{1}{c}{(5)} & \multicolumn{1}{c}{(6)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} & \multicolumn{1}{c}{(5)} & \multicolumn{1}{c}{(6)} & \multicolumn{1}{c}{(7)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} & \multicolumn{1}{c}{(5)} & \multicolumn{1}{c}{(6)} & \multicolumn{1}{c}{(7)} & \multicolumn{1}{c}{(8)} \\
& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} & \multicolumn{1}{c}{(5)} & \multicolumn{1}{c}{(6)} & \multicolumn{1}{c}{(7)} & \multicolumn{1}{c}{(8)} & \multicolumn{1}{c}{(9)} \\
```

## 1. Basic usage of `esttab` command:
### 1.1. Recommended: Don't include table notes in the Stata file

```stata
global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles       "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2} & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_file         "${Results}/test.tex"

esttab reg1 reg2 reg3 reg4 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(4) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) order(var) varlabels(var1 "var1" var2 "var2") ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}") ///
    posthead("${latex_numbers}" "${latex_titles}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}")
```
### 1.2. Add table notes in the Stata file

```stata
global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles       "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2} & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_file         "${Results}/test.tex"

esttab reg9 reg10 reg11 reg12 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(4) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) order(var) varlabels(var1 "var1" var2 "var2") ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}") ///
    posthead("${latex_numbers}" "${latex_titles}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}" "\begin{tablenotes}" "\footnotesize" "\item" "Notes. Add table notes here." "\end{tablenotes}")
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/stata-notes/02-single-panel-reg-table/  

