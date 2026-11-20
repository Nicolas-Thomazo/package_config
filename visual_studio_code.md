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
    // Formatage et sauvegarde automatiques
    "editor.formatOnSave": true,
    "files.autoSave": "afterDelay",
    "editor.linkedEditing": true,
    "editor.cursorBlinking": "phase",
    // Comportement du terminal intégré (copier à la sélection, coller au clic droit)
    "terminal.integrated.rightClickBehavior": "paste",
    "terminal.integrated.copyOnSelection": true,
    "terminal.integrated.commandsToSkipShell": [
        "-workbench.action.quickOpen"
    ],
    "terminal.integrated.defaultProfile.linux": "zsh",
    // Interface et disposition des panneaux (barre latérale à droite pour éviter le décalage du code)
    "debug.toolBarLocation": "docked",
    "workbench.editor.enablePreview": false,
    "workbench.editor.tabCloseButton": "right",
    "workbench.editor.tabSizing": "shrink",
    "workbench.editor.tabActionLocation": "right",
    "workbench.panel.defaultLocation": "right",
    "workbench.settings.editor": "json",
    "workbench.sideBar.location": "right",
    // Synchronisation du défilement entre l'éditeur Markdown et l'aperçu (Ctrl+Shift+V)
    "markdown.preview.scrollEditorWithPreview": true,
    "markdown.preview.scrollPreviewWithEditor": true,
    // Python : Ruff comme formateur par défaut, correction du lint et tri des imports à la sauvegarde
    "[python]": {
        "editor.formatOnSave": true,
        "editor.defaultFormatter": "charliermarsh.ruff",
        "editor.codeActionsOnSave": {
            "source.fixAll.ruff": "explicit",
            "source.organizeImports.ruff": "explicit"
        }
    },
    // Python : analyse du code et exécution des tests avec pytest
    "python.analysis.extraPaths": [
        "./src"
    ],
    "python.testing.pytestArgs": [
        "tests"
    ],
    "python.testing.unittestEnabled": false,
    "python.testing.pytestEnabled": true,
    "esbonio.sphinx.confDir": "",
    // Extension Vim : laisser VS Code gérer Ctrl+P (Quick Open) et Ctrl+W (fermer l'onglet)
    "vim.handleKeys": {
        "<C-p>": false,
        "<C-w>": false,
    }
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
 - Ruff [astral.sh]: To replace Flake8 (plus dozens of plugins), Black, isort, pyupgrade
 - ty [astral.sh]
 
