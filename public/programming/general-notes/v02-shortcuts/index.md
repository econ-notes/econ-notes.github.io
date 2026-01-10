# VSCode: Keyboard Shortcuts


```json
[
//-- comments using ctrl + r
{
    "key": "ctrl+r",
    "command": "-workbench.action.openRecent"
},
{
    "key": "ctrl+r",
    "command": "-workbench.action.reloadWindow",
    "when": "isDevelopment"
},
{
    "key": "ctrl+r",
    "command": "editor.action.blockComment",
    "when": "editorTextFocus && !editorReadonly"
},
{
    "key": "shift+alt+a",
    "command": "-editor.action.blockComment",
    "when": "editorTextFocus && !editorReadonly"
},
{
    "key": "ctrl+r",
    "command": "editor.action.commentLine",
    "when": "editorTextFocus && !editorReadonly"
},
{
    "key": "ctrl+/",
    "command": "-editor.action.commentLine",
    "when": "editorTextFocus && !editorReadonly"
},

//-- special treatment to run selected python codes in ipython console
{ 
    "key":"alt+enter",
    "command":"python.execSelectionInTerminal",
    "when":"editorFocus && !findInputFocussed && !replaceInputFocussed && editorLangId == 'python'"
},
{
    "key":"alt+shift+enter",
    "command":"workbench.action.terminal.sendSequence",
    "args":{ "text": "\u000d" }
},
{
    "key": "ctrl+shift+h",
    "command": "workbench.action.terminal.runSelectedText"
},

//-- r assignment operator
{
    "key": "alt+-",  // or whatever keybinding you want
    "command": "workbench.action.terminal.sendSequence",
    "args": {
        "text": " <- "
    },
    "when": "terminalFocus && !terminalTextSelected"
},
{
    "key": "alt+-",
    "command": "type",
    "when": "editorLangId == r && editorTextFocus || editorLangId == qmd && editorTextFocus",
    "args": {"text": " <- "}
},
//-- editor operators
{
    "key": "ctrl+d",
    "command": "editor.action.copyLinesDownAction",
    "when": "editorTextFocus && !editorReadonly"
},
{
    "key": "shift+alt+down",
    "command": "-editor.action.copyLinesDownAction",
    "when": "editorTextFocus && !editorReadonly"
},
{
    "key": "ctrl+alt+d",
    "command": "editor.action.addSelectionToNextFindMatch",
    "when": "editorFocus"
},

]
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/general-notes/v02-shortcuts/  

