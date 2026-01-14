# Template: Standard Environments for Mathematics


## Standard mathematical environments in `amsthm`

The `amsthm` package also includes three standard styles that do not require `\newtheoremstyle` to use: `definition`, `plain`, and `remark`. In what follows, I use these standard styles for common mathematical environments.

More explanations:
- It is possible to count an environment within sections. This is achieved by e.g., `\newtheorem{definition}{Definition}[section]` or `\newtheorem{theorem}{Theorem}[section]`.
- It is possible for two environments to share the same counter, e.g., `\newtheorem{lemma}[theorem]{Lemma}`.
- It is possible to suppress the numbering for an environment, e.g., `\newtheorem*{remark}{Remark}`

```
\theoremstyle{definition}
\newtheorem{definition}{Definition}[section]
\newtheorem{theorem}{Theorem}
\newtheorem{lemma}{Lemma}
\newtheorem{proposition}{Proposition}
\newtheorem{corollary}{Corollary}
\newtheorem{assumption}{Assumption}

\theoremstyle{remark}
\newtheorem*{remark}{Remark}
```

## The prime version of an environment

The following codes define a new environment: `assumptionp` that is a prime version of some base assumptions.

```
\newtheorem{assumption}{Assumption}
\newtheorem{innerassumption}{Assumption}
\newenvironment{assumptionp}[1]{
    \renewcommand\theinnerassumption{\ref*{#1}'}
    \innerassumption
}{
    \endinnerassumption
}
```

The usage of this environment is as follows.

```
\begin{assumption}[Assumption]\label{base}
    Here is a basic assumption.
\end{assumption}

\begin{assumptionp}{base} \label{prime}
    Here is its prime version.
\end{assumptionp}

\begin{assumption}
    Here is a new assumption with counter value 2.
\end{assumption}

This is Assumption \ref{prime}.
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s01-standard-math-environments/  

