# Template: Paper Notes


Here is a template for making paper notes.

```latex
\documentclass[12pt]{article}

%-- paths
\newcommand{\CiteMathPackage}{math}
\newcommand{\CiteReference}{ref.bib}

%-- packages
\usepackage{setspace,geometry,fancyvrb,rotating,pdflscape}
\usepackage{marginnote,datetime,enumitem}
\usepackage{titlesec,indentfirst}
\usepackage{amsmath,amsfonts,amssymb,amsthm,mathtools,chngcntr}
\usepackage{threeparttable,booktabs,adjustbox,makecell}
\usepackage{graphicx,epstopdf,float,soul,subfig}
\usepackage[toc,page]{appendix}

%-- page setup
\usdate
\geometry{scale=0.8}
\vfuzz=30pt
\hfuzz=30pt
\titleformat{\paragraph}[runin]{\itshape}{}{}{}[.] 
\titlelabel{\thetitle.\;}
\setlength{\parindent}{10pt}
\setlength{\parskip}{10pt}
\setlist[itemize]{topsep=0pt,leftmargin=20pt,itemsep=0pt,parsep=10pt}
\setlist[enumerate,1]{topsep=0pt,leftmargin=30pt,itemsep=0pt,parsep=10pt,label=(\arabic*)}
\setlist[enumerate,2]{topsep=0pt,leftmargin=10pt,itemsep=0pt,parsep=10pt,label=(\alph*)}
\setlist[enumerate,3]{topsep=0pt,leftmargin=10pt,itemsep=0pt,parsep=10pt,label=(\roman*)}
% \usepackage{Alegreya}
% \usepackage[T1]{fontenc}
% \usepackage{palatino}
% \usepackage{fourier}
\usepackage{charter}
\usepackage[english]{babel}
\usepackage[autostyle=true]{csquotes}
\MakeOuterQuote{"}

%-- bibliography
\usepackage{natbib}
% \bibliographystyle{plainnat}
% \bibliographystyle{mystyle}

%-- more customization
\usepackage{fancybox,url,xcolor}
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
\newcommand{\mynotes}[1]{{\color{MyRed}{Notes: #1}}}
\usepackage{hyperref}
\hypersetup{
    bookmarksnumbered=true,
    colorlinks=true,
    linkcolor=MyGreen,
    citecolor=MyGreen,
    filecolor=MyBlue,
    urlcolor=MyGreen
}

%-- math-related setups
%!! environments
\theoremstyle{definition}
\newtheorem{definition}{Definition}[section]
\newtheorem{theorem}{Theorem}
\newtheorem{lemma}{Lemma}
\newtheorem{proposition}{Proposition}
\newtheorem{corollary}{Corollary}
\newtheorem{assumption}{Assumption}
\theoremstyle{remark}
\newtheorem*{remark}{Remark}
%!! numbering
\counterwithin{equation}{section}
\renewcommand{\theequation}{\arabic{section}.\arabic{equation}}

\begin{document}

\title{\bf Title}
\author{Author}
\date{\today}
\maketitle








% \bibliography{\CiteReference}
\end{document}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/t01-paper-notes/  

