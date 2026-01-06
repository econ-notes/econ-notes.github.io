---
title: 'VSCode task: Deleting zCodeRunnerFile files'
date: '2025-12-19'
---

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