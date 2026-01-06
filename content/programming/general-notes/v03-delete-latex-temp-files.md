---
title: 'VSCode task: Deleting auxiliary files for LaTex compilation in the paper folder'
date: '2025-12-20'
---

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