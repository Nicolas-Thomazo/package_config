# 🌱 Visual Studio Code config
> Configure you vscode

<p align="center">
<img src="img/vscode.png" alt="Description de l'image" width="400">
<p>

## Interactive notebook

## Config
At the root of your project, add a folder name .vscode if it doesn't exist and then add a file name settings.json and add the following dict in the file 
 
```json
{
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
 
