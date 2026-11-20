# Configuration OpenCode (`~/.config/opencode/`)

Documentation minimale pour restaurer la configuration OpenCode sur un autre PC.

---

## 1. Fichier principal : `~/.config/opencode/opencode.jsonc`

C'est le fichier central (modèles locaux vLLM, serveurs MCP et plugins).

```jsonc
{
  // https://opencode.ai/config.json — validation et autocomplétion dans l'éditeur
  "$schema": "https://opencode.ai/config.json",
  // Modèle par défaut (découvert automatiquement sur http://127.0.0.1:8000)
  "model": "vllm/Qwen/Qwen3.5-9B",
  "mcp": {
    "servers": {
      "context7": {
        "type": "remote",
        "url": "https://mcp.context7.com/mcp"
      }
    }
  },
  "providers": {
    "vllm": {
      // Port par défaut : aucune baseURL nécessaire. Décommentez si le serveur
      // écoute ailleurs ou sur une autre machine :
      // "settings": { "baseURL": "http://gpu-host:8000/v1" },
      "models": {
        // L'identifiant du modèle servi est le chemin local passé à vllm serve
        // (`vllm serve /home/nicolas/Documents/models/Qwen3.5-4B`), comme le
        // montre /v1/models. Utiliser "Qwen/Qwen3.5-4B" ne fonctionnerait pas.
        "/home/nicolas/Documents/models/Qwen3.5-4B": {
          "capabilities": {
            "tools": true,
            "input": ["text"],
            "output": ["text"]
          }
        },
        "/home/nicolas/Documents/models/Qwen3.5-9B": {
          "capabilities": {
            "tools": true,
            "input": ["text"],
            "output": ["text"]
          }
        }
      }
    }
  },
  "plugins": [
    "@slkiser/opencode-quota",
    //"opencode-supermemory",
    "@plannotator/opencode",
    "@cortexkit/opencode-magic-context",
    "opencode-context-tui",
    "opencode-dir-tree-tui"
  ],
  "provider": {
    // Detected opencode-go authentication; opencode-quota added this global provider declaration.
    "opencode-go": {}
  }
}
```

---

## 2. Fichiers secondaires (optionnels)

### `~/.config/opencode/cli.json` (Thème CLI/TUI)
```json
{
  "$schema": "https://opencode.ai/v2/cli.json",
  "theme": {
    "name": "opencode"
  }
}
```

### `~/.config/opencode/opencode-quota/settings.jsonc` (Réglages d'affichage du quota)
```jsonc
{
  "version": 6,
  "statusLine": {
    "withSidebar": true,
    "runsOut": true
  }
}
```

### `~/.config/opencode/tui-preferences.jsonc` (Préférences visuelles des plugins TUI)
```jsonc
{
  "magic-context": {
    "collapsed": false
  }
}
```

---

## 3. Explications des extensions (Plugins & MCP)

Les plugins listés dans `"plugins"` sont téléchargés et installés automatiquement par OpenCode au lancement :

### Plugins actifs
- **`@slkiser/opencode-quota`** : Affiche ta consommation, les coûts et les quotas restants de tes fournisseurs d'API (comme `opencode-go`) directement dans la barre de statut du TUI.
- **`@plannotator/opencode`** : Ajoute une interface pour relire et annoter visuellement les plans de l'agent, faire des revues de code (`/plannotator-review`, `/plannotator-annotate`, `/plannotator-last`, `/plannotator-inbox`).
- **`@cortexkit/opencode-magic-context`** : Gestionnaire de contexte et de mémoire long-terme par projet (`ctx_reduce`, `ctx_search`, `ctx_memory`, `ctx_note`). Permet de garder une session active sur la durée en archivant automatiquement l'historique.
- **`opencode-context-tui`** : Widget dans l'interface TUI pour visualiser l'occupation de la fenêtre de contexte en temps réel.
- **`opencode-dir-tree-tui`** : Ajoute un panneau d'arborescence de fichiers (file tree) dans le TUI d'OpenCode.

### Plugin désactivé (en commentaire)
- **`opencode-supermemory`** : Ancien plugin de mémoire inter-sessions (désactivé au profit de `magic-context`). Ses fichiers résiduels (`supermemory.json` et `commands/supermemory-*.md`) sont encore présents mais inutilisés.

### Serveur MCP
- **`context7`** (`https://mcp.context7.com/mcp`) : Permet à l'agent de récupérer à la volée la documentation officielle à jour des librairies et frameworks (React, Python, Next.js, etc.).

---

## 4. Points d'attention lors de la migration sur un autre PC

1. **Chemins des modèles locaux vLLM** :
   - Dans `opencode.jsonc`, les modèles vLLM sont déclarés avec le chemin absolu `/home/nicolas/Documents/models/Qwen3.5-4B` (et `9B`). Si ton nom d'utilisateur ou l'emplacement des modèles change sur l'autre PC, pense à adapter ces clés pour qu'elles correspondent exactement à l'argument passé à `vllm serve`.
2. **Commandes slash auto-générées (`~/.config/opencode/commands/`)** :
   - Les fichiers dans `commands/` (`plannotator-*.md`, `supermemory-*.md`) sont créés par leurs plugins respectifs, tu n'as pas besoin de les copier manuellement.
3. **Authentification** :
   - Ne copie pas `service.json` (généré localement). Sur le nouveau PC, reconnecte simplement ton compte via `opencode auth login`.
