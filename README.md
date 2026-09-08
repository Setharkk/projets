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

## Travail client

Décrit sans nommer personne. Un client apparaît sous son nom seulement s'il l'a autorisé.

**Agent expert HubSpot** · JavaScript
Un agent qui fait le travail d'un expert HubSpot sur une base réelle : enrichissement, scoring, audit. Le principe de sécurité gouverne tout le reste : lecture libre, écriture validée, et les outils qui modifient tournent en simulation par défaut. Étude de cas publique : [setharkk-growth.fr/realisations/agent-hubspot](https://setharkk-growth.fr/realisations/agent-hubspot).

**Agent de saisie pour une plateforme de gestion de formation** · JavaScript
Connecté à une API GraphQL, il fait la saisie administrative à la place de l'humain. Onze outils de lecture, vingt outils d'écriture idempotents avec normalisation par liste blanche et vérification par relecture, validation humaine avant toute écriture, moteur agentique plafonné à quarante étapes. L'OPCO de rattachement est résolu par SIRET via l'API France compétences.

**Application SaaS de facturation et de gestion commerciale** · Python, React
Python 3.13, FastAPI, React 18, TypeScript, PostgreSQL 16.

**Application de facturation, paie et dossiers** · Electron, TypeScript
Livrée en application de bureau. Les binaires publics et le canal de mise à jour sont dans [facturation-paie-releases](https://github.com/Setharkk/facturation-paie-releases), la source reste privée.

**Cockpit de pilotage pour une coach indépendante** · Next.js
Onboarding des clientes automatisé, sur une base Notion. Next.js 16, React 19, Tailwind 4, API Notion, Claude.

**Assistant socratique pour un bootcamp de formation** · TypeScript
Accompagne les participantes sur dix sessions : comprendre la théorie, avancer sur les exercices, valider leurs réponses. Il ne fait pas le travail à leur place et ne valide aucune stratégie, c'est sa contrainte de conception. Escalades avec résolution, récapitulatif automatique, limitation de débit, rétention RGPD. Sept phases livrées et testées en conditions réelles.

**Site du même programme de formation** · Next.js

---

## Outils et expérimentations

**CRM de prospection ciblée** · TypeScript, Python
Passerelle Flask pour les embeddings, l'accès SIRENE et la collecte web. Backend FastAPI pour le CRM et l'assistant. Frontend Next.js. Workflows N8N pour le sourcing SIRENE, les signaux BODACC et l'enrichissement. PostgreSQL et Neo4j en lecture seule pour les hypothèses.

**Moteur de marketing comportemental B2B** · TypeScript
Un graphe métier Neo4j d'environ 310 nœuds répartis sur onze domaines, un frontend Next.js 15, un sidecar FastAPI pour les embeddings et le traitement du langage, le SDK Anthropic pour les agents.

**Playbook commercial** · Cypher
Le playbook lui-même, écrit en Cypher sur Neo4j : les règles sont des requêtes, pas un document.

**Le site setharkk-growth.fr** · HTML
Cinquante et une pages sans aucun framework. Un validateur maison en Python vérifie à chaque poussée les liens internes morts, le parsage des JSON-LD, la correspondance mot pour mot entre les questions du `FAQPage` et le texte visible, l'unicité du H1, la cohérence du sitemap et une liste de tournures interdites. Il tourne en intégration continue et bloque la fusion.

**BrainrotArena** · Lua
Un jeu Roblox, avec un flux de travail Rojo et Git. Pour le plaisir.

---

## Ce que vous ne verrez pas ici

Aucun nom de client, aucune marque cliente, aucun chiffre d'affaires. Un client n'est nommé que s'il l'a autorisé. Les études de cas anonymisées sont sur **[setharkk-growth.fr/realisations](https://setharkk-growth.fr)**.

Si vous voulez lire du code avant de travailler avec moi, demandez : j'ouvre un accès en lecture sur un dépôt privé, au cas par cas.

**contact@setharkk-growth.fr**
