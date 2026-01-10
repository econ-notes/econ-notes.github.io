# VSCode Task: Deleting ZCodeRunnerFile Files


```json
{
    "version": "1.0.0",
    "tasks": [
        {
            "label": "Delete zCodeRunnerFile files",
            "type": "shell",
            "command": "powershell",
            "args": [
                "-NoProfile",
                "-Command",
                "Get-ChildItem -Path . -Recurse -Filter zCodeRunnerFile.do | Remove-Item -Force"
            ],
            "problemMatcher": [],
            "group": {
                "kind": "build",
                "isDefault": false
            },
            "presentation": {
                "echo": true,
                "reveal": "always",
                "focus": false,
                "panel": "shared"
            }
        }
    ]
}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/general-notes/v04-delete-zcoderunnerfile-files/  

