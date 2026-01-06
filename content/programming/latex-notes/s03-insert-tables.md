---
title: 'Snippets: Inserting tables'
date: '2025-12-19'
---

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
