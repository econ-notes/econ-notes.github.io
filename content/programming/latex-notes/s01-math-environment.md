---
title: 'Template: Self-defined environments for mathematics'
date: '2025-12-21'
---

## A basic snippet

```latex
\usepackage[most]{tcolorbox}
\tcbuselibrary{skins, breakable}

%-- theorem environment
%!! theorem counter
\newcounter{theorem}
\renewcommand{\thetheorem}{\arabic{chapter}.\arabic{theorem}}
%!! theorem box style
\tcbset{
    theoremstyle/.style={
    breakable,
    colback=gray!15,
    colframe=black,
    colbacktitle=gray!15,
    coltitle=black,
    coltext=MyRed,
    fonttitle=\bfseries,
    title={#1},
    enhanced,
    attach boxed title to top left={yshift=-2mm, xshift=2mm},
    boxed title style={
        colframe=black,
        arc=1mm,
        outer arc=1.5mm,
        boxrule=0.5mm,
    },
    overlay={},
    }
}
%!! theorem environment with name
\NewDocumentEnvironment{theorem}{o}{
    \refstepcounter{theorem}
    \IfNoValueTF{#1}{
    \begin{tcolorbox}[theoremstyle={Theorem \thetheorem.}]
    }{
    \begin{tcolorbox}[theoremstyle={Theorem \thetheorem. #1}]
    }
    \setlength{\parindent}{10pt}
}{
    \end{tcolorbox}
}

\usepackage{chngcntr}
\counterwithin{theorem}{section}
\counterwithin{equation}{section}
```

## Multiple environments with separate numbering

```latex
\usepackage[most]{tcolorbox}
\tcbuselibrary{skins, breakable}

%-- assumption environment
%!! assumption counter
\newcounter{assumption}
\renewcommand{\theassumption}{\arabic{assumption}}
%!! assumption box style
\tcbset{
    assumptionstyle/.style={
    breakable,
    colback=gray!15,
    colframe=black,
    colbacktitle=gray!15,
    coltitle=black,
    coltext=MyOrange,
    fonttitle=\bfseries,
    title={#1},
    enhanced,
    attach boxed title to top left={yshift=-2mm, xshift=2mm},
    boxed title style={
        colframe=black,
        arc=1mm,
        outer arc=1.5mm,
        boxrule=0.5mm,
    },
    overlay={},
    }
}
%!! assumption environment with name
\NewDocumentEnvironment{assumption}{o}{
    \refstepcounter{assumption}
    \IfNoValueTF{#1}{
    \begin{tcolorbox}[assumptionstyle={Assumption \theassumption.}]
    }{
    \begin{tcolorbox}[assumptionstyle={Assumption \theassumption. #1}]
    }
    \setlength{\parindent}{10pt}
}{
    \end{tcolorbox}
}

%-- theorem environment
%!! theorem counter
\newcounter{theorem}
\renewcommand{\thetheorem}{\arabic{theorem}}
%!! theorem box style
\tcbset{
    theoremstyle/.style={
    breakable,
    colback=gray!15,
    colframe=black,
    colbacktitle=gray!15,
    coltitle=black,
    coltext=MyRed,
    fonttitle=\bfseries,
    title={#1},
    enhanced,
    attach boxed title to top left={yshift=-2mm, xshift=2mm},
    boxed title style={
        colframe=black,
        arc=1mm,
        outer arc=1.5mm,
        boxrule=0.5mm,
    },
    overlay={},
    }
}
%!! theorem environment with name
\NewDocumentEnvironment{theorem}{o}{
    \refstepcounter{theorem}
    \IfNoValueTF{#1}{
    \begin{tcolorbox}[theoremstyle={Theorem \thetheorem.}]
    }{
    \begin{tcolorbox}[theoremstyle={Theorem \thetheorem. #1}]
    }
    \setlength{\parindent}{10pt}
}{
    \end{tcolorbox}
}

%-- remark environment
%!! remark counter
\newcounter{remark}
\renewcommand{\theremark}{\arabic{remark}}
%!! remark box style
\tcbset{
    remarkstyle/.style={
    breakable,
    colback=white,
    colframe=black,
    colbacktitle=gray!15,
    coltitle=black,
    coltext=black,
    fonttitle=\bfseries,
    title={#1},
    enhanced,
    attach boxed title to top left={yshift=-2mm, xshift=2mm},
    boxed title style={
        colframe=black,
        arc=1mm,
        outer arc=1.5mm,
        boxrule=0.5mm,
    },
    overlay={},
    }
}
%!! remark environment with name
\NewDocumentEnvironment{remark}{o}{
    \refstepcounter{remark}
    \IfNoValueTF{#1}{
    \begin{tcolorbox}[remarkstyle={Remark \theremark.}]
    }{
    \begin{tcolorbox}[remarkstyle={Remark \theremark. #1}]
    }
    \setlength{\parindent}{10pt}
}{
    \end{tcolorbox}
}

%-- notation environment
%!! notation counter
\newcounter{notation}
\renewcommand{\thenotation}{\arabic{notation}}
%!! notation box style
\tcbset{
    notationstyle/.style={
    breakable,
    colback=white,
    colframe=black,
    colbacktitle=gray!15,
    coltitle=black,
    coltext=black,
    fonttitle=\bfseries,
    title={#1},
    enhanced,
    attach boxed title to top left={yshift=-2mm, xshift=2mm},
    boxed title style={
        colframe=black,
        arc=1mm,
        outer arc=1.5mm,
        boxrule=0.5mm,
    },
    overlay={},
    }
}
%!! notation environment with name
\NewDocumentEnvironment{notation}{o}{
    \refstepcounter{notation}
    \IfNoValueTF{#1}{
    \begin{tcolorbox}[notationstyle={Notations.}]
    }{
    \begin{tcolorbox}[notationstyle={Notations. #1}]
    }
    \setlength{\parindent}{10pt}
}{
    \end{tcolorbox}
}
```