# Projets

Une vitrine, pas un dépôt de code. Chaque projet listé ici a son propre dépôt, privé : le code appartient à mes clients ou n'est pas prêt à être lu. Ce qui suit décrit le problème traité, l'approche retenue et ce que ça a coûté d'apprendre.

Je suis Samir Benjaddi. J'audite des façons de travailler et j'automatise ce qui mérite de l'être, pour des artisans, des indépendants et des TPE, depuis Martigues. Le reste est sur **[setharkk-growth.fr](https://setharkk-growth.fr)**.

---

## Recherche

Deux paris à long terme sur des architectures qui ne reposent ni sur l'attention ni sur des poids pré-entraînés. Ce sont des travaux de recherche, pas des produits : je les présente comme tels.

### ARIA · Rust

*Geometric Intelligence, a new paradigm beyond transformers.*

ARIA remplace le paradigme transformeur par des **Geometric Function Units**, où la relation entre neurones est une fonction géométrique plutôt qu'une tête d'attention. Aucun bloc transformeur, aucun poids pré-entraîné, tout est construit depuis zéro.

La question posée : la géométrie différentielle peut-elle offrir une base plus expressive et mieux fondée théoriquement que l'attention ? C'est un projet de recherche ouvert, dont l'échec est une issue admise.

### Setharkk Cortex · Rust

*Un cortex causal déterministe.*

Les concepts sont des index `u32` dans des arènes contiguës. Un automate à pile à registres parcourt un graphe discret en suivant des prédicats booléens, jamais un `argmax` sur une distribution. Quand un chemin échoue, un bit d'inhibition est **gravé définitivement** : l'erreur devient une contrainte physique que le processeur rejette en un cycle.

Le graphe se compresse en macros réutilisables, puis en schémas polymorphes. La tranche active du chemin de décision tient sous **2 Mio**, donc en cache CPU. La convergence est prouvée par la théorie des treillis.

Ce projet succède à une version TypeScript d'environ 39 000 lignes qui fonctionnait, mais dont quatre pathologies structurelles ont été diagnostiquées dans le code avant d'être réécrites. La décision d'architecture la plus importante est négative : ne jamais dépendre d'un modèle de langage comme oracle ni comme moteur de secours.

---

## Outils internes

### Harnais de vérité terrain · Python

Mesurer ce qu'un agent de code fait réellement, plutôt que ce qu'on croit qu'il fait.

Chaque tâche est déclarée **avant** la session, avec son critère de réussite figé par empreinte. Tout est ensuite tracé : le brief, chaque intervention humaine, chaque appel d'outil, la durée. À la fin, la tâche reçoit un **verdict externe, jamais écrit par l'agent lui-même**.

Trois courbes hebdomadaires en sortent : taux d'autonomie, interventions par heure, horizon. Chaque message envoyé en cours d'exécution compte comme une intervention, y compris la reprise après une nouvelle session. C'est volontairement sévère : une mesure indulgente ne sert à rien.

Python et SQLite, aucune dépendance réseau, aucune infrastructure. Les traces sont en ajout seul.

C'est le prolongement direct de ce que je vends : on ne peut pas décider quoi automatiser sans mesurer d'abord.

---

## Public

### [Setharkk](https://github.com/Setharkk/Setharkk) · Python

Agent IA autonome tournant **100 % en local** sur un GPU grand public, avec mémoire long terme et graphe de connaissances. Qwen 3.5 9B, Neo4j, PostgreSQL. Aucune API cloud, aucune clé, aucune donnée qui sort. Le code est ouvert.

### [facturation-paie-releases](https://github.com/Setharkk/facturation-paie-releases)

Les versions publiques d'une application de facturation et de paie développée sur mesure pour un client, en Electron et TypeScript. Les binaires sont publics, la source reste privée : c'est le modèle que j'applique au travail client.

---

## Ce que vous ne verrez pas ici

Les projets menés pour des clients ne sont pas listés tant que le client ne l'a pas autorisé, et jamais sous un nom qui permettrait de l'identifier. Les études de cas anonymisées sont sur **[setharkk-growth.fr/realisations](https://setharkk-growth.fr)**.

Si vous voulez lire du code avant de travailler avec moi, demandez : j'ouvre un accès en lecture sur un dépôt privé, au cas par cas.

**contact@setharkk-growth.fr**
