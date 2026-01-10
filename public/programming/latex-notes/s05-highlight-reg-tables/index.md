# Snippets: Highlighting a Part of Regression Tables


## 1. In the package area
With the help of the following two latex commands `\marktopleft{name}` and `\markbottomright{name}`, it is possible to highlight specific results in the regression table.

```latex
\usepackage[customcolors]{hf-tikz}
\usetikzlibrary{calc}
\usetikzlibrary{fit,shapes.misc}
\newcommand\marktopleft[1]{%
    \tikz[overlay, remember picture]
        \node (marker-#1-a) at (0,1.5ex) {};%
}
\newcommand\markbottomright[1]{%
    \tikz[overlay, remember picture]
        \node (marker-#1-b) at (1.5ex,0) {};%
    \tikz[MyPink, ultra thick, overlay, remember picture, inner sep=4pt]
        \node[draw, rectangle, fit=(marker-#1-a.center) (marker-#1-b.center)] {};%
}
```

## 2. Changes inside the `tabular` environment
```latex {hl_lines=[13, 16]}
\begin{table}[H]
    \centering
    \caption{}
    \resizebox{0.7\textwidth}{!}{
        \begin{tabular}{lcccc}
            \toprule
            \toprule
            & \multicolumn{2}{c}{Full}                            & Urban                    & Rural                    \\
            \cmidrule(lr){2-3} \cmidrule(lr){4-5}            
            & (1)                      & (2)                      & (3)                      & (4)                      \\
            & \multicolumn{1}{c}{Work} & \multicolumn{1}{c}{Work} & \multicolumn{1}{c}{Work} & \multicolumn{1}{c}{Work} \\
            \midrule
            Mother's exposure to LLF   & -0.476***                & \marktopleft{a1} -0.447** & -0.445* & -0.582***   \\
                                    & (0.162)                  & (0.166)  & (0.247) & (0.182)     \\
            Father's exposure to LLF   &                          & -0.228   &         &             \\
                                    &                          & (0.162) \markbottomright{a1} &         &             \\
            \midrule
            Control                           & Y                        & Y        & Y       & Y           \\
            Age and Province FE               & Y                        & Y        & Y       & Y           \\
            Province FE $\times$ Cohort Trend & Y                        & Y        & Y       & Y           \\
            Sample mean                       & 3.296                    & 3.296    & 2.962   & 3.497       \\
            Observations                      & 15,301                   & 15,301   & 5,760   & 9,539       \\
            \bottomrule
            \bottomrule
        \end{tabular}
    }
    \label{results}
    \begin{minipage}{0.7\textwidth}
        \vspace{5pt}
        {\footnotesize Notes.}
    \end{minipage}
\end{table}
```

## 3. The effects of the commands

{{< figure
    src="/images/highlight-reg-tables.jpg"
    caption="Final effects"
    width=500
    class="ma0 w-75"
>}}



---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s05-highlight-reg-tables/  

