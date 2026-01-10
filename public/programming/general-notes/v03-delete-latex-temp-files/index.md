# VSCode Task: Deleting Auxiliary Files for LaTex Compilation in the Paper Folder


```json
{
    "version": "1.0.0",
    "tasks": [
        {
            "label": "Delete LaTeX auxiliary files in paper folder",
            "type": "shell",
            "command": "powershell",
            "args": [
                "-NoProfile",
                "-Command",
                "Get-ChildItem -Path paper -Recurse -Include *.aux,*.bbl,*.blg,*.bcf,*.toc,*.nav,*.synctex.gz,*.fdb_latexmk,*.fls,*.snm,*.log,*.out | Remove-Item -Force"
            ],
            "group": {
                "kind": "build",
                "isDefault": false
            }
        }
    ]
}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/general-notes/v03-delete-latex-temp-files/  

