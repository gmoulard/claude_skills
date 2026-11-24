# TODO

Feuille de route de <projet>, dans l'ordre de construction de la [spécification](<chemin de la spécification>). Les numéros entre parenthèses renvoient à ses sections.

États : `[ ]` à faire ; `[~]` en cours ou à vérifier (fait, mais pas encore validé) ; `[!]` bloqué (attend une décision, un accès ou un matériel : la raison est dite) ; `[x]` réalisé et validé. Une action ouverte dit de quoi elle dépend (« Dépend de : ») et ses critères d'acceptation ; elle n'est cochée `[x]` qu'une fois ses critères remplis. Les actions réalisées tiennent sur une ligne ; une fois validées, elles sont déplacées dans [Actions réalisées](Todo-done.md), sauf si un de leurs points reste ouvert.

<!-- Filtres : seulement si le TODO est publié sur un site qui charge todo-filter.js et todo-filter.css ; sinon supprimer ce bloc. -->
<div id="todo-filters" class="todo-filters" role="group" aria-label="Filtrer les actions">
  <label><input id="todo-show-completed" type="checkbox"> Réalisées et validées</label>
  <label><input id="todo-show-progress" type="checkbox" checked> En cours ou à vérifier</label>
  <label><input id="todo-show-pending" type="checkbox" checked> À faire</label>
  <label><input id="todo-show-blocked" type="checkbox" checked> Bloquées</label>
</div>

## 0. Ménage du dépôt

Tout est réalisé : voir [Actions réalisées](Todo-done.md).

## 1. Décisions

- [!] **TODO-1.1**: <question à trancher> (<section>). Dépend de : aucune.
  - Critères d'acceptation : <choix fait par l'utilisateur, écrit dans la spécification (section)>. Bloqué par : décision de l'utilisateur.

## 2. Étape 1 — <nom>

### <Sous-partie> (<section>)

- [ ] **TODO-2.1**: <action>. Dépend de : <TODO-x.y | aucune>.
  - Critères d'acceptation : <ce qui doit être constaté pour cocher `[x]`>.
- [~] **TODO-2.2**: <action réalisée, pas encore validée : ce qui est fait, ce qui reste à vérifier>. Dépend de : <…>.
  - Critères d'acceptation : <…>.
  - [x] <sous-point réalisé>.
  - [ ] <sous-point restant>.
