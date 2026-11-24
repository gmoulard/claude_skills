# Skills Claude

Skills pour [Claude Code](https://claude.com/claude-code), écrits en français et génériques : rien de propre à un dépôt dans les skills eux-mêmes.

## Skills

| Skill | Description |
|-------|-------------|
| [`code-style`](code-style/SKILL.md) | Règles d'écriture du code pour un dépôt en « vibe coding » (code écrit et relu par des agents) : pas de commentaires sauf les pièges « NE PAS » et l'en-tête de licence, pas de code mort, recherche avant suppression, marqueurs de conflit, robustesse, pièges d'édition. |
| [`spec-sync`](spec-sync/SKILL.md) | Garder la spécification fonctionnelle, ses traductions, ses schémas d'architecture et le README alignés sur le code. |
| [`debug-frontend`](debug-frontend/SKILL.md) | Reproduire et diagnostiquer un bug d'interface web (JS, HTML, CSS) avec Playwright et Chromium headless, en production ou sur une version locale servie en statique. |
| [`release`](release/SKILL.md) | Publier une version : choisir le niveau (patch/minor/major) avec l'utilisateur, incrémenter le numéro, compléter l'historique, regrouper les commits, tagger et pousser. |
| [`deploy-production`](deploy-production/SKILL.md) | Mettre en production en poussant la branche principale vers une branche de production dédiée, suivre le déploiement et le vérifier ; aussi republier une ancienne version. |
| [`todo`](todo/SKILL.md) | Créer et tenir la feuille de route `TODO.md` selon le modèle maison (actions `TODO-x.y`, états `[ ]` `[~]` `[!]` `[x]`, dépendances, critères d'acceptation, `Todo-done.md`, boîte de réception) ; modèles et filtres du site dans [`todo/template/`](todo/template/). |
| [`clarify-request`](clarify-request/SKILL.md) | Demander des précisions quand une demande peut se lire de deux façons, répond peut-être à une question précédente, manque d'une valeur ou porte sur une action difficile à défaire ; ne pas demander ce que le dépôt ou la conversation disent déjà. |

## Agents

Sous-agents pour Claude Code, dans [`agents/`](agents/). Un sous-agent travaille dans son propre contexte et ne renvoie qu'un compte rendu court à la session principale : il ménage ses tokens.

| Agent | Description |
|-------|-------------|
| [`todo-lot`](agents/todo-lot.md) | Réalise un lot du TODO (`LOT-n`, groupe d'actions cohérent défini par le skill [`todo`](todo/SKILL.md)) : une action = un commit poussé ; rend les questions qui attendent une décision de l'utilisateur. Lancement : « Réalise LOT-3 avec l'agent todo-lot ». |

## Paramètres propres au dépôt

Chaque skill lit ses valeurs propres au dépôt (fichier de version, branches, commandes de tests, adresse de production, sélecteurs, etc.) dans une section « Paramètres des skills » du `CLAUDE.md` du dépôt qui l'utilise. Un sous-titre par skill, par exemple :

```markdown
## Paramètres des skills

- **`release`** :
  - fichier de version : `app/version.py` (`VERSION = "x.y.z"`) ;
  - branche principale : `main` ;
  - tests : `python -m unittest discover -s tests`.
- **`todo`** :
  - TODO : `docs/TODO.md` ; actions réalisées : `docs/Todo-done.md` ; boîte de réception : `docs/Todo-ithem-for-todo.md` ;
  - spécification : `docs/specification.md` ;
  - filtres : oui (site GitHub Pages, `docs/_layouts/default.html`).
- **`deploy-production`** :
  - branche de production : `production` ;
  - workflow : « Deploy » (`.github/workflows/deploy.yml`).
```

Une valeur absente : le skill la demande à l'utilisateur plutôt que de la deviner.

## Installation

Un skill est un dossier contenant un `SKILL.md`. Le placer :

- dans `~/.claude/skills/` pour tous les projets ;
- dans `.claude/skills/` d'un projet pour ce seul projet (versionné avec lui).

Copie :

```bash
git clone git@github.com:gmoulard/claude_skills.git
cp -r claude_skills/release ~/.claude/skills/
```

Lien symbolique, pour suivre les mises à jour avec un simple `git pull` :

```bash
ln -s "$PWD/claude_skills/release" ~/.claude/skills/release
```

Sous Windows (PowerShell, mode développeur ou administrateur) :

```powershell
New-Item -ItemType SymbolicLink -Path "$HOME\.claude\skills\release" -Target "$PWD\claude_skills\release"
```

Les agents s'installent de la même façon, fichier par fichier, dans `~/.claude/agents/` (tous les projets) ou `.claude/agents/` (un projet) :

```bash
ln -s "$PWD/claude_skills/agents/todo-lot.md" ~/.claude/agents/todo-lot.md
```

Les skills et agents installés apparaissent dans Claude Code au démarrage suivant de la session.
