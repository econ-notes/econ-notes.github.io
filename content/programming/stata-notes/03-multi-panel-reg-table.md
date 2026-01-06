---
title: 'Regression tables: Prodcing a multiple-panel regression table'
date: '2025-12-23'
---

## 1. Two-panel regression tables

```stata
global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles_A     "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2}  & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_titles_B     "& \multicolumn{1}{c}{outcome5} & \multicolumn{1}{c}{outcome6}  & \multicolumn{1}{c}{outcome7} & \multicolumn{1}{c}{outcome8} \\"
global latex_panel_A      "\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (a): Panela}} \\ [7pt]"
global latex_panel_B      "\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (b): Panelb}} \\ [7pt]"
global latex_file         "${Results}/test.tex"

esttab reg1 reg2 reg3 reg4 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(3) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}" "${latex_panel_A}") ///
    posthead("${latex_numbers}" "${latex_titles_A}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_midrule}")

esttab reg9 reg10 reg11 reg12 using "${latex_file}", ///
    append style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(3) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_panel_B}") ///
    posthead("${latex_numbers}" "${latex_titles_B}" "${latex_midrule}") ///
    prefoot("") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}")
```
## 2. Three-panel regression tables

```stata
global latex_star         "\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}"
global latex_begintabular "\begin{tabular}{lcccc}"
global latex_endtabular   "\end{tabular}"
global latex_toprule      "\toprule"
global latex_midrule      "\midrule"
global latex_bottomrule   "\bottomrule"
global latex_numbers      "& \multicolumn{1}{c}{(1)} & \multicolumn{1}{c}{(2)} & \multicolumn{1}{c}{(3)} & \multicolumn{1}{c}{(4)} \\"
global latex_titles_A     "& \multicolumn{1}{c}{outcome1} & \multicolumn{1}{c}{outcome2}  & \multicolumn{1}{c}{outcome3} & \multicolumn{1}{c}{outcome4} \\"
global latex_titles_B     "& \multicolumn{1}{c}{outcome5} & \multicolumn{1}{c}{outcome6}  & \multicolumn{1}{c}{outcome7} & \multicolumn{1}{c}{outcome8} \\"
global latex_titles_C     "& \multicolumn{1}{c}{outcome9} & \multicolumn{1}{c}{outcome8}  & \multicolumn{1}{c}{outcome7} & \multicolumn{1}{c}{outcome6} \\"
global latex_panel_A      "\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (a): Panela}} \\ [7pt]"
global latex_panel_B      "\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (b): Panelb}} \\ [7pt]"
global latex_panel_C      "\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (c): Panelc}} \\ [7pt]"
global latex_file         "${Results}/test.tex"

esttab reg1 reg2 reg3 reg4 using "${latex_file}", ///
    replace style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(3) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_star}" "${latex_begintabular}" "${latex_toprule}" "${latex_toprule}" "${latex_panel_A}") ///
    posthead("${latex_numbers}" "${latex_titles_A}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_midrule}")

esttab reg5 reg6 reg7 reg8 using "${latex_file}", ///
    append style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(3) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_panel_B}") ///
    posthead("${latex_numbers}" "${latex_titles_B}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_midrule}" )

esttab reg9 reg10 reg11 reg12 using "${latex_file}", ///
    append style(tex) fragment nocons label nofloat nobaselevels nonumbers noobs nomtitles collabels(,none) ///
    b(3) se(3) star(* 0.10 ** 0.05 *** 0.01) ///
    keep(var) ///
    stats(cmean r2 N, labels("Control mean" "R-squared" "N") fmt(%9.3f %9.3f %9.0g)) ///
    prehead("${latex_panel_C}") ///
    posthead("${latex_numbers}" "${latex_titles_C}" "${latex_midrule}") ///
    prefoot("${latex_midrule}") ///
    postfoot("${latex_bottomrule}" "${latex_bottomrule}" "${latex_endtabular}")
```