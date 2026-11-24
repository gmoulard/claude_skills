---
name: todo
description: Créer et tenir la feuille de route d'un dépôt (TODO.md) selon le modèle maison — actions numérotées TODO-x.y, états [ ] [~] [!] [x], « Dépend de : », critères d'acceptation, actions validées déplacées dans Todo-done.md, demandes de l'utilisateur relevées dans Todo-ithem-for-todo.md. À utiliser pour créer un TODO, et dans le même changement que tout travail qui avance, bloque ou termine une action.
---

# Feuille de route (TODO)

Les chemins (TODO, actions réalisées, boîte de réception, spécification) et l'usage des filtres sont dans la section « Paramètres des skills » du `CLAUDE.md` du dépôt. Valeurs par défaut : `docs/TODO.md`, `docs/Todo-done.md`, `docs/Todo-ithem-for-todo.md`, pas de filtres.

## Créer le TODO

Copier les fichiers de [`template/`](template/) et remplir les `<…>` :

- `TODO.md` : légende, puis une section numérotée par étape, dans l'ordre de construction de la spécification ; `## 0. Ménage du dépôt` et `## 1. Décisions` toujours présentes ;
- `Todo-done.md` : mêmes sections, actions déjà réalisées et validées ;
- `Todo-ithem-for-todo.md` : vide ; l'utilisateur y note ses demandes en vrac ;
- `todo-filter.js` et `todo-filter.css` : seulement si le TODO est publié sur un site (GitHub Pages) ; charger le script dans la mise en page (`<script src="…/todo-filter.js" defer></script>`), ajouter le CSS, et vérifier que le contenu Markdown rendu est dans un élément `.prose` (sinon adapter le sélecteur du script). Sans site, supprimer le bloc `<div id="todo-filters">` du TODO.

Dans le `CLAUDE.md` du dépôt : dire que le TODO se lit avant toute modification fonctionnelle et se met à jour dans le même changement, et ajouter les paramètres de ce skill.

## Format d'une action

```markdown
- [ ] **TODO-2.4**: <action> (<section de la spec>). Dépend de : TODO-2.1, TODO-1.3.
  - Critères d'acceptation : <ce qui doit être constaté pour cocher [x]>.
  - [ ] <sous-point>
```

- **Numéro** `TODO-<section>.<n>` : jamais réutilisé ni renuméroté, même après déplacement ou abandon. Nouvelle action : numéro suivant le plus grand de la section, y compris ceux de `Todo-done.md`.
- **États** : `[ ]` à faire ; `[~]` fait mais pas encore validé (dire ce qui reste à vérifier) ; `[!]` bloqué (dire « Bloqué par : » quoi) ; `[x]` réalisé et validé.
- **Une action ouverte** porte toujours « Dépend de : » (`aucune` s'il n'y a rien) et ses critères d'acceptation, vérifiables.
- **Une action abandonnée** : barrée (`~~…~~`), cochée `[x]`, avec la date et la raison (« Retiré le AAAA-MM-JJ : … »).
- Une décision de l'utilisateur se note avec sa date (« Tranché le AAAA-MM-JJ : … ») et se reporte dans la spécification.

## Faire avancer

1. Avant de travailler : lire `Todo-ithem-for-todo.md`. Chaque demande devient une action numérotée (ou complète une action existante) dans la bonne section, puis est retirée de ce fichier.
2. Fonction réalisée : la dire dans la spécification, passer l'action en `[~]` avec ce qui est fait et ce qui reste à vérifier.
3. Critères d'acceptation remplis (vérifiés, pas supposés) : cocher `[x]`, réduire l'action à une ligne, la déplacer dans `Todo-done.md` à la même section. Une action dont un sous-point reste ouvert reste dans le TODO.
4. Section entièrement réalisée : la garder dans le TODO avec « Tout est réalisé : voir [Actions réalisées](Todo-done.md). »
5. Ne jamais cocher `[x]` une action dont un critère n'a pas été constaté : laisser `[~]` et dire ce qui manque.

## Vérifier

- Numéros en double : `grep -ohE 'TODO-[0-9]+\.[0-9]+\*\*' <TODO> <done> | sort | uniq -d` (doit être vide).
- Chaque action ouverte a ses critères : `grep -A1 -E '^\s*- \[[ ~!]\] \*\*TODO-' <TODO> | grep -c "Critères d'acceptation"` égale le nombre d'actions ouvertes.
- `Todo-ithem-for-todo.md` est vide en fin de travail.
