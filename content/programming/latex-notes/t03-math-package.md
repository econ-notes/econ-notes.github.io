---
title: 'Template: Abbreviated math commands'
date: '2025-12-23'
---

```latex {name="math.sty"}
%-- useful commands

%!! adjust space for brackets specified with \left and \right
\usepackage{mleftright}
\mleftright

%!! brackets
\newcommand{\bc}[1]{\left\lbrace #1 \right\rbrace} 
\newcommand{\bp}[1]{\left( #1 \right)} 
\newcommand{\of}[1]{\left( #1 \right)}
\newcommand{\bs}[1]{\left[ #1 \right]} 
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\norm}[1]{\left\lVert #1 \right\rVert}
\newcommand{\floor}[1]{\left\lfloor #1 \right\rfloor}

%!! accents
\newcommand{\ol}[1]{\overline{#1}}
\newcommand{\undl}[1]{\underline{#1}}
\newcommand{\wh}[1]{\widehat{#1}}
\newcommand{\wt}[1]{\widetilde{#1}}
\newcommand{\bds}[1]{\boldsymbol{#1}}
\newcommand{\pr}{\prime}

%!! convergence symbols
\newcommand{\cvginf}[1]{{#1} \rightarrow \infty}
\newcommand{\cvg}[2]{{#1} \rightarrow {#2}}

%!! derivative symbols
\newcommand{\pdfrac}[2]{\frac{\partial\; {#1}}{\partial\; {#2}}}
\newcommand{\fdfrac}[2]{\frac{d {#1}}{d {#2}}}

%-- operators
\usepackage{xparse}

%!! logarithm
\let\oldln\ln
\RenewDocumentCommand{\ln}{g}{\IfNoValueTF{#1}{\oldln}{{\oldln}{\bp{#1}}}}

%!! exponential
\let\oldexp\exp
\RenewDocumentCommand{\exp}{g}{\IfNoValueTF{#1}{\oldexp}{{\oldexp}{\bp{#1}}}}

%!! indicator
\NewDocumentCommand{\ind}{g}{%
\IfNoValueTF{#1}{\operatorname{\mathbb{I}}}%
{\mathbb{I}{\bp{#1}}}}

%!! trace
\NewDocumentCommand{\tr}{g}{%
\IfNoValueTF{#1}{\operatorname{tr}}%
{{\operatorname{tr}}{\bp{#1}}}}

%!! maximum
\let\oldmax\max
\RenewDocumentCommand{\max}{o g}{%
\IfNoValueTF{#2}{\oldmax\IfValueT{#1}{_{#1}}}%
{{\oldmax\IfValueT{#1}{_{#1}}}{\bc{#2}}}}

%!! argmax
\DeclareMathOperator*{\argmax}{argmax}

%!! minimum
\let\oldmin\min
\RenewDocumentCommand{\min}{o g}{%
\IfNoValueTF{#2}{\oldmin\IfValueT{#1}{_{#1}}}%
{{\oldmin\IfValueT{#1}{_{#1}}}{\bc{#2}}}}

%!! argmin
\DeclareMathOperator*{\argmin}{argmin}

%-- probabilities

%!! expectation
\NewDocumentCommand{\E}{o g}{%
\IfNoValueTF{#2}{\operatorname{\mathbb{E}}\IfValueT{#1}{_{#1}}}%
{\mathbb{E}\IfValueT{#1}{_{#1}}{\bs{\,#2\,}}\,}}

%!! probability
\RenewDocumentCommand{\P}{o g}{%
\IfNoValueTF{#2}{\operatorname{\mathbb{P}}\IfValueT{#1}{_{#1}}}%
{\mathbb{P}\IfValueT{#1}{_{#1}}{\bs{\,#2\,}}\,}}

%!! variance
\NewDocumentCommand{\var}{g}{%
\IfNoValueTF{#1}{\operatorname{var}}%
{{\operatorname{var}}{\bs{\,#1\,}}}}

%!! covariance
\NewDocumentCommand{\cov}{g}{%
\IfNoValueTF{#1}{\operatorname{cov}}%
{{\operatorname{cov}}{\bs{\,#1\,}}}}

%!! correlation
\NewDocumentCommand{\corr}{g}{%
\IfNoValueTF{#1}{\operatorname{corr}}%
{{\operatorname{corr}}{\bs{\,#1\,}}}}

%!! standard deviation
\NewDocumentCommand{\sd}{g}{%
\IfNoValueTF{#1}{\operatorname{sd}}%
{{\operatorname{sd}}{\bs{\,#1\,}}}}

%!! standard error
\NewDocumentCommand{\se}{g}{%
\IfNoValueTF{#1}{\operatorname{se}}%
{{\operatorname{se}}{\bs{\,#1\,}}}}

%!! convergence symbols
\newcommand{\inas}{\overset{a.s.}{\to}}
\newcommand{\indist}{\overset{d}{\to}}
\newcommand{\inprob}{\overset{p}{\to}}
\newcommand{\inrm}{\overset{r.m.}{\to}}
\newcommand{\inlp}{\overset{L_p}{\to}}
\newcommand{\inlt}{\overset{L_2}{\to}}
\newcommand{\inlo}{\overset{L_1}{\to}}
\newcommand{\eqdist}{\stackrel{d}{=}}
\newcommand{\indep}{\perp\!\!\!\!\perp}
\DeclareMathOperator{\plim}{plim}

%!! iid symbols
\newcommand{\iid}{\mathbin{\overset{iid}{\sim}}}

%-- letters

%!! Greek letters
\def\a{\alpha}
\def\b{\beta}
\def\c{\chi}
\def\d{\delta}
\def\D{\Delta}
\def\uD{\upDelta}
\def\e{\epsilon}
\def\ve{\varepsilon}
\def\f{\phi}
\def\vf{\varphi}
\def\F{\Phi}
\def\g{\gamma}
\def\G{\Gamma}
\def\h{\eta}
\def\k{\kappa}
\def\l{\lambda}
\def\L{\Lambda}
\def\m{\mu}
\def\n{\nu}
\def\o{\omega}
\def\O{\Omega}
\def\vp{\varpi}
\def\p{\psi}
\def\r{\rho}
\def\s{\sigma}
\def\vs{\varsigma}
\def\S{\Sigma}
\def\t{\theta}
\def\T{\Theta}
\def\vt{\vartheta}
\def\U{\Upsilon}
\def\x{\xi}
\def\X{\Xi}
\def\z{\zeta}

%!! blackboard letters
\def\R{\mathbb{R}}
\def\N{\mathbb{N}}
\def\Z{\mathbb{Z}}
\def\Q{\mathbb{Q}}
\def\C{\mathbb{C}}
\def\I{\mathbb{I}}

%!! caligraphic letters
\def\Ac{\mathcal{A}}
\def\Bc{\mathcal{B}}
\def\Cc{\mathcal{C}}
\def\Dc{\mathcal{D}}
\def\Ec{\mathcal{E}}
\def\Fc{\mathcal{F}}
\def\Gc{\mathcal{G}}
\def\Hc{\mathcal{H}}
\def\Ic{\mathcal{I}}
\def\Jc{\mathcal{J}}
\def\Kc{\mathcal{K}}
\def\Lc{\mathcal{L}}
\def\Mc{\mathcal{M}}
\def\Nc{\mathcal{N}}
\def\Oc{\mathcal{O}}
\def\Pc{\mathcal{P}}
\def\Qc{\mathcal{Q}}
\def\Rc{\mathcal{R}}
\def\Sc{\mathcal{S}}
\def\Tc{\mathcal{T}}
\def\Uc{\mathcal{U}}
\def\Vc{\mathcal{V}}
\def\Wc{\mathcal{W}}
\def\Xc{\mathcal{X}}
\def\Yc{\mathcal{Y}}
\def\Zc{\mathcal{Z}}

%!! boldsymbol letters
\def\bdsa{\boldsymbol{a}}
\def\bdsb{\boldsymbol{b}}
\def\bdsc{\boldsymbol{c}}
\def\bdsd{\boldsymbol{d}}
\def\bdse{\boldsymbol{e}}
\def\bdsf{\boldsymbol{f}}
\def\bdsg{\boldsymbol{g}}
\def\bdsh{\boldsymbol{h}}
\def\bdsi{\boldsymbol{i}}
\def\bdsj{\boldsymbol{j}}
\def\bdsk{\boldsymbol{k}}
\def\bdsl{\boldsymbol{l}}
\def\bdsm{\boldsymbol{m}}
\def\bdsn{\boldsymbol{n}}
\def\bdso{\boldsymbol{o}}
\def\bdsp{\boldsymbol{p}}
\def\bdsq{\boldsymbol{q}}
\def\bdsr{\boldsymbol{r}}
\def\bdss{\boldsymbol{s}}
\def\bdst{\boldsymbol{t}}
\def\bdsu{\boldsymbol{u}}
\def\bdsv{\boldsymbol{v}}
\def\bdsw{\boldsymbol{w}}
\def\bdsx{\boldsymbol{x}}
\def\bdsy{\boldsymbol{y}}
\def\bdsz{\boldsymbol{z}}

%!! boldsymbol letters
\def\bdsA{\boldsymbol{A}}
\def\bdsB{\boldsymbol{B}}
\def\bdsC{\boldsymbol{C}}
\def\bdsD{\boldsymbol{D}}
\def\bdsE{\boldsymbol{E}}
\def\bdsF{\boldsymbol{F}}
\def\bdsG{\boldsymbol{G}}
\def\bdsH{\boldsymbol{H}}
\def\bdsI{\boldsymbol{I}}
\def\bdsJ{\boldsymbol{J}}
\def\bdsK{\boldsymbol{K}}
\def\bdsL{\boldsymbol{L}}
\def\bdsM{\boldsymbol{M}}
\def\bdsN{\boldsymbol{N}}
\def\bdsO{\boldsymbol{O}}
\def\bdsP{\boldsymbol{P}}
\def\bdsQ{\boldsymbol{Q}}
\def\bdsR{\boldsymbol{R}}
\def\bdsS{\boldsymbol{S}}
\def\bdsT{\boldsymbol{T}}
\def\bdsU{\boldsymbol{U}}
\def\bdsV{\boldsymbol{V}}
\def\bdsW{\boldsymbol{W}}
\def\bdsX{\boldsymbol{X}}
\def\bdsY{\boldsymbol{Y}}
\def\bdsZ{\boldsymbol{Z}}

%!! boldsymbol letters
\def\Ab{\boldsymbol{A}}
\def\Bb{\boldsymbol{B}}
\def\Cb{\boldsymbol{C}}
\def\Db{\boldsymbol{D}}
\def\Eb{\boldsymbol{E}}
\def\Fb{\boldsymbol{F}}
\def\Gb{\boldsymbol{G}}
\def\Hb{\boldsymbol{H}}
\def\Ib{\boldsymbol{I}}
\def\Jb{\boldsymbol{J}}
\def\Kb{\boldsymbol{K}}
\def\Lb{\boldsymbol{L}}
\def\Mb{\boldsymbol{M}}
\def\Nb{\boldsymbol{N}}
\def\Ob{\boldsymbol{O}}
\def\Pb{\boldsymbol{P}}
\def\Qb{\boldsymbol{Q}}
\def\Rb{\boldsymbol{R}}
\def\Sb{\boldsymbol{S}}
\def\Tb{\boldsymbol{T}}
\def\Ub{\boldsymbol{U}}
\def\Vb{\boldsymbol{V}}
\def\Wb{\boldsymbol{W}}
\def\Xb{\boldsymbol{X}}
\def\Yb{\boldsymbol{Y}}
\def\Zb{\boldsymbol{Z}}

%!! underlined letters (for vectors)
\newcommand{\ua}{\undl{a}}
\newcommand{\ub}{\undl{b}}
\newcommand{\uc}{\undl{c}}
\newcommand{\ux}{\undl{x}}
\newcommand{\uy}{\undl{y}}
\newcommand{\uz}{\undl{z}}
\newcommand{\uX}{\undl{X}}
\newcommand{\uQ}{\undl{Q}}
\newcommand{\uU}{\undl{U}}
\newcommand{\uV}{\undl{V}}

%!! underlined greek letters (for vectors)
\newcommand{\uga}{\undl{\alpha}}
\newcommand{\ugb}{\undl{\beta}}
\newcommand{\ugc}{\undl{\chi}}
\newcommand{\ugd}{\undl{\delta}}
\newcommand{\ugD}{\undl{\Delta}}
\newcommand{\uguD}{\undl{\upDelta}}
\newcommand{\uge}{\undl{\epsilon}}
\newcommand{\ugve}{\undl{\varepsilon}}
\newcommand{\ugf}{\undl{\phi}}
\newcommand{\ugvf}{\undl{\varphi}}
\newcommand{\ugF}{\undl{\Phi}}
\newcommand{\ugg}{\undl{\gamma}}
\newcommand{\ugh}{\undl{\eta}}
\newcommand{\ugl}{\undl{\lambda}}
\newcommand{\ugm}{\undl{\mu}}
\newcommand{\ugn}{\undl{\nu}}
\newcommand{\ugo}{\undl{\omega}}
\newcommand{\ugO}{\undl{\Omega}}
\newcommand{\ugvp}{\undl{\varpi}}
\newcommand{\ugp}{\undl{\psi}}
\newcommand{\ugr}{\undl{\rho}}
\newcommand{\ugs}{\undl{\sigma}}
\newcommand{\ugvs}{\undl{\varsigma}}
\newcommand{\ugS}{\undl{\Sigma}}
\newcommand{\ugt}{\undl{\theta}}
\newcommand{\ugT}{\undl{\Theta}}
\newcommand{\ugvt}{\undl{\vartheta}}
\newcommand{\ugx}{\undl{\xi}}
\newcommand{\ugz}{\undl{\zeta}}

```