# Top 20 des commandes les plus utiles (VSCode Vim)

Voici l'essentiel absolu (la loi des 80/20) pour coder rapidement avec **VSCode Vim**.

## Comprendre les Modes Vim
Contrairement à un éditeur classique, Vim fonctionne par **modes** :
- **Mode Normal** (`Esc`) : Le mode par défaut. Les touches ne tapent pas de texte, elles servent à **naviguer** et **lancer des commandes** (`Action + Cible`, ex: `dw` pour supprimer un mot).
- **Mode Insertion** (`i`, `a`, `o`) : Comme un éditeur normal, tout ce que tu tapes écrit du texte.
- **Mode Visuel** (`v` par caractère, `V` par ligne entière, `Ctrl + v` en bloc/colonne) : Équivalent du **surlignage à la souris**. Tu sélectionnes visuellement une zone en déplaçant le curseur, *puis* tu appliques une action dessus (`y` pour copier, `d` pour couper, `p` pour remplacer la sélection, `>` pour indenter).

---

## 1. Insertion & Sortie (3)
| # | Commande | Action |
| :--- | :--- | :--- |
| **1** | `Esc` | Retourner en **Mode Normal** (la base de tout) |
| **2** | `i` / `A` | Insérer avant le curseur / Insérer tout à la **fin de la ligne** |
| **3** | `o` / `O` | Créer une nouvelle ligne en dessous / au-dessus et passer en mode insertion |

## 2. Navigation ultra-rapide (5)
| # | Commande | Action |
| :--- | :--- | :--- |
| **4** | `w` / `b` | Sauter au début du mot suivant / mot précédent |
| **5** | `0` / `$` | Aller au début / à la fin de la ligne |
| **6** | `f<char>` | Sauter directement sur le caractère `<char>` dans la ligne (`;` pour le suivant) |
| **7** | `gg` / `G` | Aller tout en haut / tout en bas du fichier (`42G` pour aller à la ligne 42) |
| **8** | `%` | Sauter à la parenthèse, l'accolade ou le crochet fermant/ouvrant associé `()[]{}` |

## 3. Édition & Manipulation (6)
| # | Commande | Action |
| :--- | :--- | :--- |
| **9** | `dd` / `yy` | **Couper** (supprimer) / **Copier** la ligne entière |
| **10** | `p` / `P` | **Coller** après le curseur (ou sous la ligne) / avant le curseur (ou en mode Visuel : remplacer la sélection) |
| **11** | `u` / `Ctrl + r` | **Annuler** (*Undo*) / **Rétablir** (*Redo*) |
| **12** | `.` | **Répéter** la toute dernière modification (commande la plus puissante de Vim) |
| **13** | `ciw` | **Changer le mot** sous le curseur (fonctionne aussi avec `diw` pour supprimer, `yiw` pour copier) |
| **14** | `ci"` / `ci(` | **Changer tout l'intérieur** des guillemets `"..."` ou parenthèses `(...)` (marche aussi avec `{`, `[`, `'`) |

## 4. Recherche (2)
| # | Commande | Action |
| :--- | :--- | :--- |
| **15** | `/texte` | Chercher `texte` dans le fichier (puis `n` pour suivant, `N` pour précédent) |
| **16** | `*` | Chercher directement toutes les occurrences du **mot sous le curseur** |

## 5. Super-pouvoirs VSCode Vim (4)
| # | Commande | Action |
| :--- | :--- | :--- |
| **17** | `gcc` | **Commenter / Décommenter** la ligne (ou `gc` sur une sélection visuelle `v`) |
| **18** | `gb` | **Multi-curseur** : sélectionner la prochaine occurrence du mot (équivalent du `Ctrl+D` de VSCode) |
| **19** | `gd` / `gh` | **Go to Definition** (aller à la définition) / Afficher le **Hover** (infobulle de type/doc) |
| **20** | `cs"'` / `ysiw"` | **Surround** : remplacer les `"` entourant un texte par `'` / entourer un mot avec `"` |

---

## Focus : Tout sélectionner, tout copier et coller (`Ctrl+A` / `Ctrl+C` / `Ctrl+V`)

- **Tout sélectionner visuellement (équivalent `Ctrl+A`) puis copier :**
  - **`ggVGy`** :
    1. `gg` amène le curseur à la première ligne
    2. `V` active le **Mode Visuel Ligne**
    3. `G` descend jusqu'à la dernière ligne (tout est surligné)
    4. `y` (*yank*) copie la sélection
- **Tout copier directement en Mode Normal (plus rapide, sans surligner) :**
  - **`ggyG`** (copie du début `gg` jusqu'à la fin `G`) ou **`:%y`** puis `Entrée` (copie tout sans même bouger le curseur).
- **Coller :**
  - **`p`** colle après le curseur (ou remplace tout si tu as d'abord fait `ggVG` dans le fichier cible).
- **Copier vers l'extérieur de VSCode (Presse-papier système) :**
  - Ajoute `"vim.useSystemClipboard": true` dans le `settings.json` de VSCode pour que `y` et `p` utilisent toujours le presse-papier de ton OS (permettant de faire `Ctrl+V` dans ton navigateur ou terminal).
  - Sans cette option, préfixe par **`"+`** : par exemple **`"+yy`** pour copier une ligne vers le système, ou **`ggVG"+y`** pour tout copier vers le système.
