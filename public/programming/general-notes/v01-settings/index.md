# VSCode: Settings


```json
{

//-- Part 1. Stata-specific settings 
"code-runner.executorMapByFileExtension": {
    ".do": "D:/APP/Stata18/VSCodeSetup/rundolines51/rundolines.exe"
},
"code-runner.runInTerminal": true,
"code-runner.temporaryFileName": "zCodeRunnerFile",
"[stata]": {
    "editor.quickSuggestions": {
        "other": true,
        "comments": true,
        "strings": true
    },
    "editor.tabSize": 4,
    "editor.wordBasedSuggestions": "allDocuments",
},

//-- Part 2. Latex-specific settings 
"[latex]": {
    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": false,
    },
    "editor.wordBasedSuggestions": "allDocuments",
    "editor.tabCompletion": "off",
    "editor.tabSize": 4,
},
// "latex-workshop.latex.autoBuild.run": "never",
"[bibtex]": {
    "editor.tabSize": 2,
    "editor.insertSpaces": true
},
"[bibtex-style]": {
    "editor.tabSize": 2
},

//-- Part 3. Python-specific settings
//!! p-3-1. editor and formatting
"[python]": {
    "editor.quickSuggestions": {
        "other": true,
        "comments": true,
        "strings": true
    },
    "editor.wordBasedSuggestions": "allDocuments",
    "editor.rulers": [79],
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnType": true,
    "editor.formatOnSave": true,
},
"black-formatter.args": [
    "--line-length=79"
],
"black-formatter.showNotifications": "always",
//!! p-3-2. terminal
"python.terminal.activateEnvironment": true,
"python.analysis.typeCheckingMode": "standard",
"interactiveWindow.collapseCellInputCode": "never",
"interactiveWindow.executeWithShiftEnter": true,
"jupyter.notebookFileRoot": "${workspaceFolder}",
"jupyter.interactiveWindow.creationMode": "multiple",
"jupyter.interactiveWindow.textEditor.executeSelection": true,
//!! p-3-3. notebook
"jupyter.askForKernelRestart": false,
"notebook.output.textLineLimit": 100,
"notebook.output.wordWrap": true,
"notebook.lineNumbers": "on",
"output.smartScroll.enabled": true,
// "jupyter.widgetScriptSources": [
//     "jsdelivr.com",
//     "unpkg.com"
// ],
// "dataWrangler.outputRenderer.pagination.defaultSize": 50,

//-- Part 4. R-specific setttings
"[r]": {
    // !! suggestions
    "editor.quickSuggestions": {
        "other": true,
        "comments": true,
        "strings": true
    },
    "editor.wordBasedSuggestions": "allDocuments",
    "editor.rulers": [79],
    "editor.tabSize": 2,
},

//-- Part 5. Other language-specific settings
//!! p-5-1. Quarto 
"[.qmd]": {
    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": false
    },
    "editor.wordBasedSuggestions": "matchingDocuments",
},
"quarto.visualEditor.spellingDictionary": "en_US",
//!! p-5-2. Markdown
"[markdown]": {
    "editor.tabSize": 2,
    "editor.unicodeHighlight.ambiguousCharacters": false,
    "editor.unicodeHighlight.invisibleCharacters": false,
    "diffEditor.ignoreTrimWhitespace": false,
    "editor.wordWrap": "on",
    "editor.quickSuggestions": {
        "comments": "on",
        "strings": "on",
        "other": "on"
    },
    "cSpell.fixSpellingWithRenameProvider": true,
    "cSpell.advanced.feature.useReferenceProviderWithRename": true,
    "cSpell.advanced.feature.useReferenceProviderRemove": "/^#+\\s/"
},
//!! p-5-3. Fortran 
"[FortranFreeForm]": {
    // !! suggestions
    "editor.quickSuggestions": {
        "other": true,
        "comments": true,
        "strings": true
    },
    "editor.wordBasedSuggestions": "allDocuments",
    "editor.rulers": [132],
    "editor.tabSize": 2,
},
//!! p-5-4. html
"[html]": {
    "editor.tabSize": 2,
},

//-- Part a. General settings
//!! p-a-1. general appearance
"workbench.iconTheme": "material-icon-theme",
"workbench.colorTheme": "GitHub Light Default",
"files.autoSave": "off",
"explorer.confirmDragAndDrop": false,
"explorer.sortOrder": "default",
"explorer.openEditors.visible": 1,
"git.openRepositoryInParentFolders": "always",
"workbench.startupEditor": "none",
"workbench.colorCustomizations": {
    "editorBracketHighlight.foreground1": "#e20505",
    "editorBracketHighlight.foreground2": "#1230da",
    "editorBracketHighlight.foreground3": "#e710bc",
    "editorBracketHighlight.foreground4": "#e6ae08",
    "editorBracketHighlight.foreground5": "#662e0b",
    "editorBracketHighlight.foreground6": "#11cdab",
    "editor.background": "#f6f8fa"
    // "editorBracketHighlight.unexpectedBracket.foreground": "#db6165"
},
"workbench.editorAssociations": {
    "*.copilotmd": "vscode.markdown.preview.editor",
    "*.pdf": "latex-workshop-pdf-hook"
},
//!! p-a-2. terminal
"terminal.integrated.fontFamily": "JetBrainsMono Nerd Font Propo SemiBold",
"terminal.integrated.cursorStyle": "line",
"terminal.integrated.cursorBlinking": false,
"terminal.integrated.cursorWidth": 2,
"terminal.integrated.shellIntegration.enabled": true,
//!! p-a-3. editor
"editor.renderWhitespace": "all",
"editor.wordWrap": "on",
"editor.fontSize": 14,
"editor.insertSpaces": true,
"editor.detectIndentation": false,
"editor.minimap.enabled": false,
"editor.fontFamily": "Cascadia Code Regular", // Fira Code Medium"
"editor.fontLigatures": true,
"editor.fontWeight": 550,
"editor.bracketPairColorization.enabled": true,
"editor.tokenColorCustomizations": {
    "textMateRules": [
            {
                "scope": [
                    "comment", 
                    "comment.block", 
                    "comment.line", 
                    "comment.block.documentation",
                ],
                "settings": {
                    "fontStyle": "bold",
                    "foreground": "#46b3c6",
                }
            },
    ],

    "[GitHub Light Default]": {
        "textMateRules": [
            {
                "scope": ["string.quoted.single", "string.quoted.double"],
                "settings": {
                    "fontStyle": "underline",
                    "foreground": "#1C9AA0",
                }
            },
            {
                "scope": "string.quoted.docstring.multi.python",
                "settings": {
                    "fontStyle": "bold",
                    "foreground": "#41aee5",
                }
            },
            {
                "scope": "variable.parameter",
                "settings": {
                    "foreground": "#dd16e7f8",
                    // "fontStyle": ""
                }
            },
            {
                "scope": ["entity.name.function"],
                "settings": {
                    "foreground": "#e66a18",
                    // "fontStyle": "italic"
                }
            },
        ]
    }
},
//!! p-a-4. spell check 
"cSpell.enabled": true,
"cSpell.language": "en",
"cSpell.caseSensitive": false,
"cSpell.diagnosticLevel": "Warning",
"cSpell.allowCompoundWords": true,
"cSpell.customDictionaries": {
    "MyWords": {
        "name": "MyWords",
        "path": "~/Dictionary/my-words.txt",
        "scope": "user",
        "addWords": true
    },
},
"cSpell.enabledFileTypes": {
    "*": true,
    ".do": true
},
//!! p-a-5. other packages
"indentRainbow.indicatorStyle": "classic",
"indentRainbow.lightIndicatorStyleLineWidth": 15,
"indentRainbow.colors": [
    // "#F0F3F3",
    "#EEE9F2",
    "#F5F0EC",
    "#F2E8E2",
    "#e8d6fd"
],
"indentRainbow.errorColor": "#545D71",
"codesnap.shutterAction": "save",
"bookmarks.sideBar.expanded": true,
"bookmarks.wrapNavigation": false,
"ProjectTree.loadIgnore": false,
"ProjectTree.ignoreFolders": ["codes/__pycache__", ".vscode", "cSpell"],

//-- Part b. More preferred customizations
//!! p-b-1. file and folder icon
"material-icon-theme.opacity": 1, 
"material-icon-theme.folders.associations": {
    ".cspell": "Vscode",
    ".vscode": "Vscode",
    "stata_libraries": "Lib",
    "python_env": "Lib",
    "__pycache__": "Lib",
    "util": "Lib",
    "codes": "Coverage",
    "output": "Coverage",
    "log": "Coverage",
    "data": "Coverage",
    "reports": "Coverage",
    "clean": "Tools",
    "analysis": "Tasks",
    "a_raw_data": "Target",
    "b_temp_data": "Target",
    "c_final_data": "Target",
    "v1_codes": "Core",
    "v1_paper": "Core",
    "v1_output": "Core",
    "v1_referee_reports": "Mock",
    "v2_codes": "Mock",
    "v2_replication": "Mock",
    "v2_paper": "Mock",
    "v2_output": "Mock",
    "v2_codes_review": "Mock",
    "v2_referee_reports": "Mock",
    "v2_zdocuments": "Mock",
},
"material-icon-theme.files.associations": {
    "*.do": "../../icons/stata",
    "*.gph": "../../icons/stata",
    "*.dta": "../../icons/statadta",
    "*.aux": "../../icons/temptex",
    "*.bbl": "../../icons/temptex",
    "*.blg": "../../icons/temptex",
    "*.bcf": "../../icons/temptex",
    "*.toc": "../../icons/temptex",
    "*.nav": "../../icons/temptex",
    "*.synctex.gz": "../../icons/temptex",
    "*.fdb_latexmk": "../../icons/temptex",
    "*.fls": "../../icons/temptex",
    "*.snm": "../../icons/temptex",
    "*.log": "../../icons/texlog",
    "*.out": "../../icons/texlog",
    "*.bib": "Tex",
    "*.tex": "Tex",
    "*.bst": "Tex",
    "*.sty": "Tex",
},


//!! p-b-2. more comments styles
"better-comments.multilineComments": true,
"better-comments.highlightPlainText": true,
"better-comments.tags": [
    {
        "tag": "--",
        "color": "#ff2c2c",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "transparent",
        "bold": true,
        "italic": false
    },
    {
        "tag": "!!",
        "color": "#037bab",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "transparent",
        "bold": true,
        "italic": false
    },
    {
        "tag": "&&",
        "color": "#037153",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "transparent",
        "bold": true,
        "italic": false
    },
    {
        "tag": "todo",
        "color": "#720000",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "#ffe100",
        "bold": true,
        "italic": true
    },
    {
        "tag": "impt",
        "color": "#720000",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "#ffe100",
        "bold": true,
        "italic": false
    },
    {
        "tag": "tocheck",
        "color": "#720000",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "#CBC3E3",
        "bold": true,
        "italic": false
    },
    {
        "tag": "&?",
        "color": "#B16139",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "transparent",
        "bold": true,
        "italic": false
    },
    {
        "tag": "Returns",
        "color": "#037153",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "#ffe100",
        "bold": true,
        "italic": false
    },
    {
        "tag": "Parameters",
        "color": "#037153",
        "strikethrough": false,
        "underline": false,
        "backgroundColor": "#ffe100",
        "bold": true,
        "italic": false
    },
],


//-- copilot
"github.copilot.enable": {
    "*": false,
    "quarto": false,
    "plaintext": false,
    "markdown": false,
    "scminput": false
},

"settingsSync.ignoredSettings": [
    "code-runner.executorMapByFileExtension",
    "latex-workshop.latex.tools",
    "latex-workshop.latex.recipes",
],

}
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/general-notes/v01-settings/  

