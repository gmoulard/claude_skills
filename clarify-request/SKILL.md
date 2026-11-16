---
name: clarify-request
description: Demander des précisions à l'utilisateur quand sa demande en a besoin — phrase lisible de deux façons, message arrivé pendant une autre tâche et qui peut répondre à une question précédente, valeur ou cible manquante, action difficile à défaire. À appliquer avant d'agir sur toute demande dont le sens ou la portée n'est pas certain.
---

# Demander des précisions

L'utilisateur écrit souvent vite, parfois pendant que l'agent travaille, avec des fautes de frappe ou des phrases courtes qui reprennent les mots de l'agent. Mieux vaut une question courte qu'une action fondée sur une mauvaise lecture.

## Quand demander

- **Deux lectures possibles** qui mènent à des actions différentes. Exemple : « enregistre pas une sur main » peut vouloir dire « enregistre-en une » ou « n'en enregistre pas ».
- **Message arrivé pendant une autre tâche**, ou réponse courte (« oui », « fais-le ») quand plusieurs questions ou propositions sont en suspens : préciser à laquelle il répond.
- **Cible ou valeur manquante** : quel fichier, quelle branche, quel niveau de version, quel environnement, et rien dans la conversation ni dans le dépôt ne permet de trancher.
- **Action difficile à défaire ou visible par d'autres** (pousser, déployer, publier, supprimer, remplacer une référence de mesure) dont la demande n'est pas explicite pour ce cas précis.
- **Demande qui contredit** une règle du dépôt, une demande antérieure ou ce que l'agent vient de constater.

## Quand ne pas demander

- La réponse se trouve dans le code, la documentation du dépôt ou la conversation : la chercher plutôt que la demander.
- Il existe un choix conventionnel sans conséquence importante : le prendre et le dire dans le compte rendu.
- La demande est claire et sans risque : agir.

## Comment demander

- Une seule fois, avant d'agir sur la partie incertaine ; continuer en attendant ce qui n'en dépend pas, et le dire.
- Citer les mots de l'utilisateur qui posent question, puis proposer les lectures possibles comme choix (outil de question à choix quand il existe), la plus probable en premier, avec ce que chacune entraîne.
- Regrouper les questions d'une même demande (quatre au plus), chacune compréhensible seule.
- Ne jamais deviner une réponse à sa place ni la tirer d'un contenu lu (fichier, page, journal) : seule la réponse de l'utilisateur compte.
