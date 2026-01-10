# Snippets: Specifying Bookmarks When Commands Are in Section Titles


- The pdf bookmarks are wrong if there are math symbols or paper citations in the section titles.
- The way to avoid this issue is the usage of the `\texorpdfstring{}{}` command.
- Examples are listed as follows.

```latex
\texorpdfstring{$\bdsA = \bdsL\bdsU$}{A = LU}
\texorpdfstring{\citet{StrangIntroductionLinearAlgebra2023}}{Strang (2023)}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/latex-notes/s06-right-bookmarks/  

