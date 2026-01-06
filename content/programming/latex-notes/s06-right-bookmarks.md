---
title: 'Snippets: Specifying bookmarks when commands are in section titles'
date: '2025-12-16'
draft: false
toc: true
weight: 10
---

- The pdf bookmarks are wrong if there are math symbols or paper citations in the section titles.
- The way to avoid this issue is the usage of the `\texorpdfstring{}{}` command.
- Examples are listed as follows.

```latex
\texorpdfstring{$\bdsA = \bdsL\bdsU$}{A = LU}
\texorpdfstring{\citet{StrangIntroductionLinearAlgebra2023}}{Strang (2023)}
```