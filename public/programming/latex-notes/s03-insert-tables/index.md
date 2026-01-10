# Snippets: Inserting Tables


## Preliminary commands

In the preamble part: Define the table location.

```latex 
\newcommand{\ResultsLocation}{./Tables}
```

In the main paper text part, set the counter, and the default title of tables. Two commands are particularly useful:

```latex
\renewcommand{\thetable}{\arabic{section}.\arabic{table}}
\setcounter{table}{0}

\renewcommand{\thetable}{B.\arabic{table}}
\setcounter{table}{0}
```

## Different ways to insert a table

### Using the `threeparttable` environment to add table notes

```latex
\begin{table}[H]
    \centering
    \caption{}
    \resizebox{0.7\textwidth}{!}{
        \begin{threeparttable}
            \input{\ResultsLocation/results.tex}
            \begin{tablenotes}
                \footnotesize
                \item Notes. 
            \end{tablenotes}
        \end{threeparttable}
    }
    \label{results}
\end{table}
```

Sometimes, for a very long table, it is useful to resize the table using the height of the paper, instead of width. Notice that here we need to add the `*` mark after the `\resizebox` command. 

This is because, for some reason, the baseline of the table is the the middle of the table, so that the lower half is part of the depth of the resulting TeX box. The `\resizebox` scales the box height, not the totalheight (height+depth) to the given value. To scale the totalheight, it is necessary to use the `*` version. See the [StackExchange discussion here](https://tex.stackexchange.com/questions/13809/resizing-a-table-by-textheight) for more information.

```latex {hl_lines=[4]}
\begin{table}[H]
    \centering
    \caption{}
    \resizebox*{!}{1\textheight}{
        \begin{threeparttable}
            \input{\ResultsLocation/results.tex}
            \begin{tablenotes}
                \footnotesize
                \item Notes. 
            \end{tablenotes}
        \end{threeparttable}
    }
    \label{results}
\end{table}
```

### Manually adding table notes

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


---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s03-insert-tables/  

