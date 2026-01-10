# Snippets: Inserting Figures


## Package area: Useful commands
```latex 
\newcommand{\ResultsLocation}{./Figures}
```

Two useful commands used in the main text:
```latex
\renewcommand{\thefigure}{\arabic{section}.\arabic{figure}}
\setcounter{figure}{0}

\renewcommand{\thefigure}{Table \arabic{figure}}
\setcounter{figure}{0}
```

## Inserting a figure 
```latex
\begin{figure}[H]
    \centering
    \noindent\caption{}
    \resizebox{0.5\textwidth}{!}{\includegraphics{fig6.png}}
    \label{fig6}
\end{figure}
```

## Inserting a figure with notes
```latex
\begin{figure}[H]
    \centering
    \noindent\caption{}
    \resizebox{1\textwidth}{!}{\includegraphics{\ResultsLocation/fig1.png}}
    \begin{minipage}{\textwidth}
        {\footnotesize Notes. }
    \end{minipage}
    \label{fig1}
\end{figure}
```

## Inserting a figure with multiple panels 
```latex
\begin{figure}[H]
    \setcounter{subfigure}{0}
    \centering
    \noindent\caption{}
    \subfloat[Panel1]{\includegraphics[width=0.48\textwidth]{fig1.png}}
    \subfloat[Panel2]{\includegraphics[width=0.48\textwidth]{fig2.png}}
    \label{fig}

    \begin{minipage}{\textwidth}
        {\footnotesize Notes.}
    \end{minipage}
\end{figure}
```

```latex
\begin{figure}[H]
    \setcounter{subfigure}{0}
    \centering
    \noindent\caption{}
    \subfloat[Title1]{\resizebox{0.7\textwidth}{!}{\includegraphics{fig1.png}}} \\

    \subfloat[Title2]{\resizebox{0.7\textwidth}{!}{\includegraphics{fig2.png}}}
    \label{fig2}
\end{figure}
```

## Inserting two subfigures under one figure caption
```latex
\begin{figure}[H]
    \centering
    \noindent\caption{}
    \begin{minipage}{0.5\textwidth}
        \includegraphics[width=1\textwidth]{fig1.png}
    \end{minipage}%
    \begin{minipage}{0.5\textwidth}
        \includegraphics[width=1\textwidth]{fig2.png}
    \end{minipage}
\end{figure}
```

## Inserting a figure in slides
### Putting figure notes under the figure
```latex
\begin{figure}
    \centering
    \noindent\caption{}
    \includegraphics[width=7cm]{fig1.png}

    \begin{itemize}
        \item Description1.
        \item Description2.
    \end{itemize}
\end{figure}
```

### Putting figure notes on the right side of the figure 
```latex
\begin{minipage}{.5\textwidth}
    \begin{figure}
        \centering
        \noindent\caption{}
        \includegraphics[width=1\textwidth]{fig1.png} 
    \end{figure}
\end{minipage}%
\begin{minipage}{.5\textwidth}
    \begin{itemize}
        \item Description1.
        \item Description2.
    \end{itemize}
\end{minipage}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s02-insert-figures/  

