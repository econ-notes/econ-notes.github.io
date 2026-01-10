# Snippets: Producing Regression Tables


## A one-panel regression table

```latex {name="result.tex"}

\begin{tabular}{lcccc}
    \toprule
    \toprule
    & \multicolumn{2}{c}{Full}                            & Urban                    & Rural       \\
    \cmidrule(lr){2-3} \cmidrule(lr){4-5}            
    & (1)                      & (2)                      & (3)                      & (4)         \\
    & \multicolumn{1}{c}{Work} & \multicolumn{1}{c}{Retired} & \multicolumn{1}{c}{Work} & \multicolumn{1}{c}{Retired} \\
    \midrule
    Mother's exposure to LLF   & -0.476***                & -0.447** & -0.445* & -0.582***   \\
                & (0.162)                  & (0.166)  & (0.247) & (0.182)     \\
    Father's exposure to LLF   &                          & -0.228   &         &             \\
                &                          & (0.162)  &         &             \\
    \midrule
    Control                    & Y                        & Y        & Y       & Y           \\
    Age and Province FE        & Y                        & Y        & Y       & Y           \\
    Province FE $\times$ Cohort Trend & Y                        & Y        & Y       & Y           \\
    Sample mean                & 3.296                    & 3.296    & 2.962   & 3.497       \\
    Observations               & 15,301                   & 15,301   & 5,760   & 9,539       \\
    \bottomrule
    \bottomrule
\end{tabular}
```

There are several principles I should follow:
- About the sequence of the table titles:
  - Classification information, like sample specification.
  - Column numbers.
  - Variable names. If the variable is too long, use the following command to split it into two rows: `\shortstack{Long \\ name}`
- The insertion of horizontal lines:
  - At the beginning of the table, use two `\toprule`.
  - At the end of the table, use two `\bottomrule`.
  - At all other parts of the table (especially when separating main coefficients and regression information, or when separating different panels), use `\midrule`.
  - When adding horizontal lines with breaks between certain columns, use commands `\cmidrule(lr){2-3} \cmidrule(lr){4-5}`.
  - Generally, `\hline` is bad for handling space.
  - There is no need to add `\\` (line separation marks) after these horizontal lines.
- Control vertical space between lines:
  - To control the space between current line and the previous line, use `\addlinespace[5pt]` command at the beginning of current line.
  - To control the space between current line and the next line, use `[5pt]` after the `\\` symbol.
  - There is no need to add `\\` (line separation marks) after specifying the vertical space.

## Insert the regression table

Generally, there are two ways to achieve this:
- The first is to use the `threeparttable` environment.
- The second is to use `minipage` environment, and specify its width such that it aligns with the table width.
- Importantly, when using Stata-generated LaTex codes for regression tables, I should check the following two issues.
  - Make sure it only contains the `tabular` environment.
  - Make sure it has defined the `sym` command for significance stars `\def\sym#1{\ifmmode^{#1}\else\(^{#1}\)\fi}`.

```latex
\begin{table}[H]
    \centering
    \caption{}
    \resizebox{0.7\textwidth}{!}{
    \begin{threeparttable}
        \input{results.tex}
        \begin{tablenotes}
            \footnotesize
            \item Notes. 
        \end{tablenotes}
    \end{threeparttable}
    }
    \label{results}
\end{table}
```

```latex
\begin{table}[H]
    \centering
    \caption{}
    \resizebox{0.7\textwidth}{!}{\input{results.tex}}
    \label{results}
    \begin{minipage}{0.7\textwidth}
        \vspace{5pt}
        {\footnotesize Notes.}
    \end{minipage}
\end{table}
```

## A two-panel regression table

At the very start of each panel, use the following command to add a panel title.
- It is left-aligned.
- It is bold.

```latex
\addlinespace[5pt] \multicolumn{5}{l}{{\bf Panel (a): Extensive margin}} \\ [5pt]
```

## More customization on the table

Suppose we want to manually adjust the space between two columns for a table. This usually happens because the table has too few columns. We can do adjustments when specifying the `tabular` environment. See the attached table as an example.

```latex
\begin{tabular}{l@{\hskip 1.5in}l@{\hskip 1.5in}l}
    \toprule\toprule
    $\E\bs{Y_{it}}$ & $i=A$ & $i=B$ \\
    \midrule
    $t=1$ & $\a_A$ & $\a_B$ \\
    $t=2$ & $\a_A + \b_2 + \tau_{A2}$ & $\a_B + \b_2$ \\
    $t=3$ & $\a_A + \b_3 + \tau_{A3}$ & $\a_B + \b_3 + \tau_{B3}$ \\
    \midrule 
    Event time & $E_A = 2$ & $E_B = 3$ \\ 
    \bottomrule\bottomrule
\end{tabular}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s04-produce-reg-tables/  

