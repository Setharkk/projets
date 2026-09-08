<div align="center">

# Setharkk Growth

### *Audit de processus et IA, pour ceux qui n'ont pas de service informatique*

[![Rust](https://img.shields.io/badge/Rust-1.75%2B-orange?logo=rust&logoColor=white)](https://www.rust-lang.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Python](https://img.shields.io/badge/Python-3.13-3776AB?logo=python&logoColor=white)](https://python.org)
[![Neo4j](https://img.shields.io/badge/Neo4j-5-008CC1?logo=neo4j&logoColor=white)](https://neo4j.com)
[![Claude](https://img.shields.io/badge/Claude-Partner_Network-D97757?logo=anthropic&logoColor=white)](https://setharkk-growth.fr/certifications)
[![Depots](https://img.shields.io/badge/D%C3%A9p%C3%B4ts-17-0f1826)]()

---

**Une vitrine, pas un dépôt de code.**<br/>
Dix-sept dépôts, deux publics. Les autres appartiennent à mes clients ou ne sont pas prêts à être lus.<br/>
Ce qui suit décrit le problème traité, l'architecture retenue, et les décisions qui ont coûté cher.

**[setharkk-growth.fr](https://setharkk-growth.fr)** · Martigues, PACA et toute la France

</div>

---

## L'écosystème en un schéma

```mermaid
flowchart TD
    R["<b>Recherche</b><br/>ARIA · Setharkk Cortex<br/><i>Rust</i>"]
    O["<b>Outils internes</b><br/>harnais de mesure · moteur comportemental · CRM<br/><i>Python · TypeScript</i>"]
    C["<b>Livraison client</b><br/>agents · applications · tableaux de bord<br/><i>TypeScript · Python · JavaScript</i>"]
    S["<b>setharkk-growth.fr</b><br/>51 pages, validateur en intégration continue"]

    R -.->|"ce que j'apprends des architectures"| C
    O -->|"ce qui mesure et qualifie"| C
    C -->|"études de cas anonymisées"| S

    style R fill:#eef2f8,stroke:#2947c9,color:#0f1826
    style O fill:#eef2f8,stroke:#2947c9,color:#0f1826
    style C fill:#2947c9,stroke:#1c3390,color:#ffffff
    style S fill:#ffffff,stroke:#7386b6,color:#0f1826
```

---

## Recherche

Deux paris longs sur des architectures qui ne reposent ni sur l'attention ni sur des poids pré-entraînés. Ce sont des travaux de recherche, présentés comme tels : l'échec est une issue admise.

### ARIA · Rust

> *Geometric Intelligence, a new paradigm beyond transformers.*

Remplace le paradigme transformeur par des **Geometric Function Units**, où la relation entre neurones est une fonction géométrique plutôt qu'une tête d'attention. Aucun bloc transformeur, aucun poids pré-entraîné, tout construit depuis zéro.

La question posée : la géométrie différentielle offre-t-elle une base plus expressive et mieux fondée théoriquement que l'attention&nbsp;?

### Setharkk Cortex · Rust

> *Un cortex causal déterministe.*

| | |
|---|---|
| **Représentation** | Concepts en index `u32` dans des arènes contiguës |
| **Parcours** | Automate à pile à registres suivant des prédicats booléens, jamais un `argmax` |
| **Apprentissage d'erreur** | Bit d'inhibition **gravé définitivement** : l'erreur devient une contrainte que le processeur rejette en un cycle |
| **Compression** | Macros réutilisables, puis schémas polymorphes |
| **Budget** | Tranche active du chemin de décision sous **2 Mio**, donc en cache CPU |
| **Preuve** | Convergence établie par la théorie des treillis |

Succède à une version TypeScript d'environ **39 000 lignes** qui fonctionnait, mais dont quatre pathologies structurelles ont été diagnostiquées dans le code avant réécriture.

La décision d'architecture la plus importante est négative : **ne jamais dépendre d'un modèle de langage** comme oracle ni comme moteur de secours.

---

## Outils internes

| Projet | Ce qu'il fait | Pile |
|---|---|---|
| **Harnais de vérité terrain** | Mesure ce qu'un agent de code fait réellement. La tâche est déclarée **avant** la session, et le verdict est **externe, jamais écrit par l'agent**. | Python · SQLite |
| **Moteur de marketing comportemental** | Graphe métier d'environ 310 nœuds sur onze domaines, agents de rédaction et de profilage. | Next.js 15 · FastAPI · Neo4j |
| **CRM de prospection ciblée** | Recherche d'entreprises via SIRENE, signaux BODACC, enrichissement, notation. | Flask · FastAPI · Next.js · N8N · PostgreSQL · Neo4j |
| **Playbook commercial** | Bundle installable chez le client : graphe pré-rempli de 54 nœuds, installateur PowerShell, deux skills livrés. Les règles sont des requêtes, pas un document. | Cypher · Neo4j · Docker |
| **BrainrotArena** | Un jeu Roblox, en Rojo et Git. Un système par fichier, synchronisation incrémentale vers Studio : changer une ligne ne réécrit pas tout. | Lua · Rojo |

Le harnais est le prolongement direct de ce que je vends : **on ne décide pas quoi automatiser sans mesurer d'abord.** Le critère de réussite est figé par empreinte avant le début, tout est tracé, et trois courbes en sortent chaque semaine : taux d'autonomie, interventions par heure, horizon. Chaque message envoyé en cours d'exécution compte comme une intervention, reprise de session comprise. C'est volontairement sévère, une mesure indulgente ne servirait à rien.

---

## Travail client

Décrit sans nommer personne. Un client n'apparaît sous son nom que s'il l'a autorisé.

| Projet | Ce qu'il fait | Pile |
|---|---|---|
| **[Agent expert HubSpot](https://setharkk-growth.fr/realisations/agent-hubspot)** | Neuf commandes sur une base réelle : enrichissement SIRENE, notation ICP, audit, fusion de doublons. **Toute écriture irréversible exige `--confirm`.** | JavaScript · API HubSpot |
| **Agent de saisie, plateforme de formation** | Onze outils de lecture, vingt outils d'écriture idempotents, **validation humaine avant toute écriture**. OPCO résolu par SIRET via France compétences. | JavaScript · GraphQL |
| **Plateforme de facturation multi-locataire** | Le plus abouti des sept. Détaillé juste en dessous. | Python · FastAPI · React · PostgreSQL · pgvector |
| **Application de bureau facturation et paie** | Factures, fiches de paie et génération de dossier de crédit. Binaires publics, source privée. | Electron · TypeScript |
| **Tableau de bord pour une accompagnatrice indépendante** | Prise en main des nouvelles clientes automatisée, brief de séance rédigé par IA, vue d'ensemble en direct. | Next.js 16 · API Notion · Claude |
| **Bot Slack pour un bootcamp** | Assistant socratique dans le Slack du client, sur dix séances. **Il ne fait pas le travail à la place des participantes.** Canal d'escalade privé, cloisonnement par personne. | Python · Slack Bolt · PostgreSQL · Claude |
| **Créateur de pages de vente** | Chaque utilisatrice compose ses pages depuis un tableau de bord, puis les publie à une adresse publique. Authentification et espace d'administration. | Next.js · TypeScript · Supabase |

### La plateforme de facturation, en détail

Publié avec l'accord du client, qui a par ailleurs laissé un avis public sur la fiche Google de Setharkk Growth.

Une entreprise de trente salariés dont la facturation ne rentrait dans aucun logiciel du marché. Le résultat est une plateforme complète, pas un formulaire de devis.

| | |
|---|---|
| **Le métier** | Devis, factures, clients, fournisseurs, paiements, relances automatiques. Conversion d'un devis en facture en un clic. |
| **La devise** | Gestion d'une monnaie locale à **parité fixe avec l'euro**, à côté des taux vivants. Une parité fixe ne se calcule pas comme un taux qui bouge : la confondre fausse toute la comptabilité. |
| **L'assistant** | Un agent conversationnel à **41 outils** : création de documents, statistiques, conversion de devises, recherche. Il répond en s'appuyant sur les données réelles de l'entreprise, par recherche sémantique sur pgvector. |
| **Les entrées** | Import des réservations depuis la plateforme métier du client par **webhook**, et reprise en masse depuis des tableurs ou des PDF scannés, avec reconnaissance de texte. |
| **Le cadre** | Multi-locataire avec cloisonnement par société, rôles administrateur, gestionnaire et employé, invitations par courriel, **journal d'audit complet**. Interface française et anglaise, thème sombre. |
| **Les documents** | Génération de PDF avec des gabarits personnalisables. |

La leçon de ce projet : **ce qui coûte cher n'est jamais la facture, c'est tout ce qui l'entoure.** La devise, les imports, les rôles et la traçabilité représentent plus de travail que le cœur métier lui-même.

---

## Dépôts publics

| Dépôt | |
|---|---|
| **[Setharkk](https://github.com/Setharkk/Setharkk)** | Agent IA autonome tournant **100 % en local** sur un GPU grand public. Mémoire long terme, graphe de connaissances. Zéro API cloud, zéro clé, zéro donnée qui sort.<br/>`Python` `Qwen 3.5 9B` `Neo4j` `PostgreSQL` |
| **[facturation-paie-releases](https://github.com/Setharkk/facturation-paie-releases)** | Versions publiques et canal de mise à jour d'une application livrée à un client. Le modèle que j'applique au travail client : binaires publics, source privée. |

---

## Le site, puisqu'il est aussi un projet

**[setharkk-growth.fr](https://setharkk-growth.fr)** · cinquante et une pages, aucun framework.

Un validateur maison en Python vérifie à chaque poussée : liens internes morts, parsage des JSON-LD, correspondance **mot pour mot** entre les questions du `FAQPage` et le texte visible, unicité du H1, cohérence du sitemap, et une liste de tournures interdites. Il tourne en intégration continue et **bloque la fusion**.

L'assistant du site est documenté comme étude de cas testable en direct : **[realisations/assistant-setharkk](https://setharkk-growth.fr/realisations/assistant-setharkk)**.

---

## Ce que vous ne verrez pas ici

Aucun nom de client, aucune marque cliente, aucun chiffre d'affaires.

Les études de cas complètes, anonymisées, sont sur **[setharkk-growth.fr](https://setharkk-growth.fr)**.

Si vous voulez lire du code avant de travailler avec moi, demandez : j'ouvre un accès en lecture sur un dépôt privé, au cas par cas.

<div align="center">

**contact@setharkk-growth.fr**

</div>
