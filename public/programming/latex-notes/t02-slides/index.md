# Template: Slides


## 1. Favorite beamer style

```latex {name="MyBeamerStyle.sty"}
%-- part 1. necessary packages

%!! p-1-1. general packages
\usepackage{graphicx,array,helvet,booktabs,pgfpages}
\usepackage{amsmath,multimedia,multirow,bbm,dcolumn}
\newcolumntype{d}[0]{D{.}{.}{5}}
\usepackage[space]{grffile}
\usepackage{threeparttable,booktabs,adjustbox}
\usepackage{epstopdf,float,soul}
\usepackage[position=top]{subfig} 
\usepackage{comment}
\vfuzz=30pt 
\hfuzz=30pt

%!! p-1-2. packages for colors
\usepackage{xcolor}
\definecolor{blue}{RGB}{0,114,178}
\definecolor{red}{HTML}{E85637}
\definecolor{darkgreen}{HTML}{2B3422}
\definecolor{yellow}{HTML}{FCDA6E}
\definecolor{MyBlue}{rgb}{0,0.2,0.6}
\definecolor{MyRed}{HTML}{D2042D}
\definecolor{MyGreen}{rgb}{0,0.4,0}
\definecolor{MyPink}{HTML}{E50379}
\definecolor{MyOrange}{HTML}{CC5500}
\definecolor{MyPurple}{HTML}{BF40BF}
\definecolor{MyYellow}{HTML}{c2ac1e}
\newcommand{\highlightO}[1]{{{\color{MyOrange}{#1}}}}
\newcommand{\highlightPP}[1]{{{\color{MyPurple}{#1}}}}
\newcommand{\highlightY}[1]{{{\color{MyYellow}{#1}}}}
\newcommand{\highlightB}[1]{{\emph{\color{MyBlue}{#1}}}}
\newcommand{\highlightP}[1]{{\emph{\color{MyPink}{#1}}}}
\newcommand{\highlightR}[1]{{\emph{\color{MyRed}{#1}}}} 

%!! p-1-3. fonts
% \usepackage[default]{lato}
% \usepackage{mathpazo}
\usepackage[T1]{fontenc}
\usepackage{inputenc}
\usepackage{libertine}
\usepackage[scale=0.88]{plex-mono}

%-- part 2. bibliography

%!! p-2-1. general settings
\usepackage[citestyle=authoryear-comp, bibstyle=authoryear-comp, maxbibnames=5, minbibnames=1, maxcitenames=2, minnames=1, datezeros=false, date=long, isbn=false, url=false, doi=false, eprint=false]{biblatex}
\renewcommand*{\nameyeardelim}{\addcomma\space}
\setbeamercolor*{bibliography entry author}{fg=black}
\addbibresource{\CiteReference}
\usepackage{hyperref}
\hypersetup{
    colorlinks = true,
    linkbordercolor = {white},
    linkcolor = {black},
    citecolor = {gray}
}
\renewbibmacro{in:}{}
\setbeamertemplate{bibliography item}{}
\setbeamerfont{bibliography entry author}{size=\footnotesize}
\setbeamercolor{bibliography entry author}{fg = black}
\setbeamercolor{bibliography entry title}{fg = black}
\setbeamerfont{bibliography entry title}{size=\footnotesize}
\setbeamerfont{bibliography entry note}{size=\footnotesize}
\setbeamercolor{bibliography entry note}{fg = black}

%!! p-2-2. author-year as a whole for hyperlink
\DeclareFieldFormat{citehyperref}{%
\DeclareFieldAlias{bibhyperref}{noformat}% Avoid nested links
\bibhyperref{#1}}
\DeclareFieldFormat{textcitehyperref}{%
    \DeclareFieldAlias{bibhyperref}{noformat}% Avoid nested links
    \bibhyperref{%
    #1%
    \ifbool{cbx:parens}
        {\bibcloseparen\global\boolfalse{cbx:parens}}
        {}
    }
}
\savebibmacro{cite}
\savebibmacro{textcite}
\renewbibmacro*{cite}{%
\printtext[citehyperref]{%
\restorebibmacro{cite}%
\usebibmacro{cite}}}
\renewbibmacro*{textcite}{%
\ifboolexpr{
( not test {\iffieldundef{prenote}} and
    test {\ifnumequal{\value{citecount}}{1}} )
or
( not test {\iffieldundef{postnote}} and
    test {\ifnumequal{\value{citecount}}{\value{citetotal}}} )
}
{\DeclareFieldAlias{textcitehyperref}{noformat}}
{}%
\printtext[textcitehyperref]{%
\restorebibmacro{textcite}%
\usebibmacro{textcite}}}
\newcommand{\referencefontsize}[1]{{\footnotesize {#1}}}

%-- part 3. set up overall template

%!! p-3-1. overall appearance
\usetheme{Boadilla}
\usefonttheme{professionalfonts}
\setbeamersize{text margin left=1em, text margin right=1em}
\setbeamertemplate{enumerate items}[default]
\setbeamertemplate{frametitle}{\vspace{6pt} \insertframetitle \par}
% \setbeamertemplate{frametitle}{
%     \begin{centering}
%         \vspace{5pt}
%         \scshape\insertframetitle\par
%     \end{centering}
% }
\setbeamertemplate{navigation symbols}{}
\setbeamercovered{} 
\useinnertheme{circles}
\setbeamertemplate{footline} [frame number]
\setbeamertemplate{caption}[numbered]
\usecolortheme{default}
\setbeamercolor{background canvas}{bg=black!2}
\setbeamercolor{button}{bg=white, fg=MyBlue}
\setbeamercolor{button border}{bg=white, fg=MyBlue}
\setbeamercolor{structure}{fg=MyBlue}
\setbeamercolor{caption name}{fg=black}

% %!! p-3-2. optional (table of contents only before new sections)
% \AtBeginSection[]
% {
%     \begin{frame}{Outline}
%         \tableofcontents[currentsection]
%     \end{frame}
% }

%!! p-3-2 table of conetents are presented before new subsections 
\newif\ifoutlineshown
\outlineshownfalse

\AtBeginSection[]{
    \outlineshowntrue
    \begin{frame}
    \frametitle{Outline}
    \tableofcontents[currentsection]
    \end{frame}
}

\AtBeginSubsection[]{
    \ifoutlineshown
    \outlineshownfalse
    \else
    \begin{frame}
        \frametitle{Outline}
        \tableofcontents[currentsection,currentsubsection]
    \end{frame}
    \fi
}

%!! p-3-3. appendix
\usepackage{appendixnumberbeamer}
\pdfstringdefDisableCommands{%
        \def\translate#1{#1}%
}

%-- part 4. self-defined commands 

%!! p-4-1. highlight results in regression tables
\usepackage[beamer,customcolors]{hf-tikz}
\usetikzlibrary{calc}
\usetikzlibrary{fit,shapes.misc}

\newcommand\marktopleft[1]{%
    \tikz[overlay,remember picture] 
        \node (marker-#1-a) at (0,1.5ex) {};%
}
\newcommand\markbottomright[1]{%
    \tikz[overlay,remember picture] 
        \node (marker-#1-b) at (1.5ex,0) {};%
    \tikz[MyPink, ultra thick, overlay, remember picture, inner sep=4pt]
        \node[draw, rectangle, fit=(marker-#1-a.center) (marker-#1-b.center)] {};%
}

%!! p-4-2. item levels 
\newenvironment{firstitemize}{\itemize\addtolength{\itemsep}{10pt}}{\enditemize}
\newenvironment{seconditemize}{\itemize\addtolength{\itemsep}{3pt}}{\enditemize}
```

## 2. The usage of the beamer style specification file

```latex
% !Tex encoding = UTF8
\documentclass[aspectratio=169, 11pt]{beamer}

% ?? project-specific setups: paths specification and custom commands
\newcommand{\CiteReference}{references.bib}
\newcommand{\ResultsLocation}{Results}

\input{MyBeamerStyle.sty}

%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--
%-- title information
%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--

\title{{Title}}
\author{{Author}}

\date{\today}

\begin{document}

\frame{\titlepage}

%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--
%-- appendix
%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--

\appendix 
\section{Appendix: References}

%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--
%-- references
%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--%--

\begin{frame}[allowframebreaks]{References}
    \nocite{*}
    \footnotesize
    \printbibliography[heading=none]
\end{frame}

\end{document}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/t02-slides/  

