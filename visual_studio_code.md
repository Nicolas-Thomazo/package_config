# 🌱 Visual Studio Code config
> Configure you vscode

<p align="center">
<img src="img/vscode.png" alt="Description de l'image" width="300">
<p>

## Interactive notebook

## Config
At the root of your project, add a folder name .vscode if it doesn't exist and then add a file name settings.json and add the following dict in the file 
 
```json
{
    "terminal.integrated.rightClickBehavior": "paste",
    "terminal.integrated.copyOnSelection": false
    //Color of side and top bar
    "workbench.colorCustomizations": {
        "titleBar.activeBackground": "#bc6c25",
        "activityBar.background": "#bc6c25"
    },
    "files.autoSave": "afterDelay",
    "python.formatting.provider": "black",
    "editor.linkedEditing": true,
    "debug.toolBarLocation": "docked",
    //Location of side bar to avoid jump in code when opening and closing it
    "workbench.editor.enablePreview": false,
    "workbench.editor.tabCloseButton": "right",
    "workbench.editor.tabSizing": "shrink",
    "workbench.panel.defaultLocation": "right",
    "workbench.settings.editor": "json",
    "workbench.sideBar.location": "right",
    //When scrolling in coding markdown windows, scroll also in priew ctrl+shift+v to get preview
    "markdown.preview.scrollEditorWithPreview": true,
    "markdown.preview.scrollPreviewWithEditor": true,
    "editor.cursorBlinking": "phase",
    "python.testing.pytestArgs": [
        "tests"
    ],
    "python.testing.unittestEnabled": false,
    "python.testing.pytestEnabled": true,
    "esbonio.sphinx.confDir": "",
    "python.analysis.extraPaths": [
        "./src"
    ],
}
```

You can also add a keybindings.json file at the root folder. This will enable the stopping of current command when hitting cmd+c (and you still have the copy with cmd+c)

```json
// Place your key bindings in this file to override the defaults
[
    {
        "key": "cmd+c",
        "command": "workbench.action.terminal.sendSequence",
        "args": { "text": "\u0003" },
        "when": "terminalFocus && terminalTextSelected == false"
    },
    {
        "key": "cmd+7",
        "command": "workbench.action.terminal.new"
    },
]
```
  
  
## SSH connection

## Extensions
 
 - autoDocstring [Nils Werner] : generate docstring automatically
 - GitLens [GitKraken]
 - Jupyter [ms-toolsai]
 - Python [Microsoft]
 - Rainbow Brackets [2gua]
 - indent-rainbow [oderwat]
 - Pylance [Microsoft]
 - Git Graph [mhutchie]
 - Rainbow CSV [mechatroner]
 - Gitignore [codezombie]
 - Vim [vscodevim] : vim emulator
 - ErrorLens [Alexander]: highlight error in vscode terminal
 
