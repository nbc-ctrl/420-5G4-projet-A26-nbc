+++
title = "Veille technologique"
weight = 1
+++

## Recherche avec le LLM doté d’un accès web

- **Outil utilisé :** `duck.ai`
- **Modèle principal et version :** GPT-6 Luna
- **Mode actif** : Chat > Recherche sur le web

### Prompt #1 : Qu'est-ce que les bases de données vectorielles en général ?

{{% expand title="**Réponse de `duck.ai`**" %}} 

Une **base de données vectorielle** stocke des représentations numériques — des *vecteurs* — associées à des contenus comme des textes, des images ou des sons. Ces vecteurs, appelés **embeddings**, sont produits par un modèle d’IA et encodent certaines caractéristiques ou relations de sens du contenu. <citation src="3,4"></citation>

Quand on lance une recherche, le système transforme la requête en vecteur, puis retrouve les vecteurs les plus proches selon une mesure de similarité. Cela permet, par exemple, de trouver des documents qui parlent d’un sujet même s’ils n’emploient pas les mêmes mots que la question. <citation src="2,3"></citation>

En pratique, une base vectorielle peut aussi conserver des références au contenu original et des métadonnées — comme la date ou la catégorie — pour filtrer les résultats. On l’utilise notamment pour la recherche sémantique, les recommandations et la récupération de documents qui fournissent du contexte à un assistant IA (RAG). <citation src="3,5"></citation>

En bref : une base classique retrouve souvent des correspondances exactes ou structurées; une base vectorielle aide à retrouver des éléments **proches par leur représentation**, souvent par leur sens. Les deux approches peuvent être combinées.

{{% /expand %}}

### Prompt #2 : En quoi les bases de données vectorielles diffèrent des bases de données relationnelles/traditionnelles en général ?

{{% expand title="**Réponse de `duck.ai`**" %}}

La différence principale tient à **la façon dont on retrouve les données**.

| Aspect | Base relationnelle (ex. SQL) | Base vectorielle |
|---|---|---|
| **Données privilégiées** | Lignes et colonnes structurées : clients, commandes, dates, montants | Vecteurs numériques représentant du texte, des images ou d’autres contenus |
| **Recherche** | Conditions précises : égalité, intervalle, filtres, jointures | Similarité : éléments dont les vecteurs sont les plus proches d’une requête |
| **Résultats** | Enregistrements qui satisfont exactement les critères | Résultats classés par proximité, parfois trouvés par une recherche approximative |
| **Usages typiques** | Transactions, inventaires, comptes, rapports et relations entre entités | Recherche sémantique, recommandations et récupération de contexte pour l’IA |

Par exemple, une base relationnelle répond bien à **« commandes passées par ce client en octobre »**. Une base vectorielle aide plutôt à répondre à **« quels documents parlent de modifier un mot de passe ? »**, même si ces documents emploient d’autres termes. <citation src="1,2"></citation>

**Elles ne se remplacent donc pas nécessairement** : une base relationnelle est souvent le bon choix pour les données opérationnelles et les requêtes exactes; une base vectorielle sert quand la recherche par similarité est importante. Un même système peut utiliser les deux, ou une base relationnelle dotée d’une extension de recherche vectorielle. <citation src="2,4"></citation>

{{% /expand %}}

### Prompt #3 : Pourquoi utiliser une base de données vectorielles ? Dans quels contextes ?

{{% expand title="**Réponse de `duck.ai`**" %}}

On utilise une base vectorielle quand on veut retrouver des éléments **par ressemblance de sens ou de contenu**, plutôt que par correspondance exacte. Elle est particulièrement utile si les gens formulent leurs recherches de façons différentes ou si les données sont difficiles à organiser en catégories fixes.

Quelques contextes courants :

- **Recherche sémantique** : retrouver des documents pertinents même s’ils n’emploient pas les mêmes mots que la requête.
- **Assistants IA avec RAG** : chercher dans des documents internes ou spécialisés, puis fournir ces passages à un modèle pour qu’il réponde en s’appuyant dessus. Une base vectorielle peut aider, mais le RAG peut aussi combiner recherche par mots-clés et autres méthodes. <citation src="1,3"></citation>
- **Recommandations** : proposer des articles, produits ou contenus proches d’un élément consulté ou des préférences d’un utilisateur.
- **Recherche multimodale** : retrouver des images, sons ou textes similaires à un exemple fourni. <citation src="2,3"></citation>
- **Détection de ressemblances** : repérer des doublons ou des éléments inhabituels par rapport à un ensemble de références.

Ce n’est pas automatiquement le meilleur choix. Pour des requêtes exactes — retrouver une commande par son numéro, calculer un solde, gérer des transactions — une base relationnelle est généralement plus adaptée. Pour beaucoup d’applications, les deux se complètent : la base relationnelle conserve les données de référence, tandis que la recherche vectorielle sert à trouver des contenus pertinents. <citation src="2,5"></citation>

En pratique, envisagez une base vectorielle si la recherche par sens apporte un bénéfice mesurable et si votre système existant ne répond pas déjà assez bien au besoin. Le modèle qui crée les vecteurs et la qualité de l’indexation influencent beaucoup la pertinence des résultats.

{{% /expand %}}

### Prompt #X : Comment insere-t-on des données dans une base de données vectorielles ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}

### Prompt #X : Comment fait-on des requêtes auprès de base de données vectorielles ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}

### Prompt #X : Quand l'IA intervient-il dans cette technologie ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}

### Prompt #X : Quel est le mécanisme derrière le _embedding_ ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}

### Prompt #X : Quel est le mécanisme derrière les recherches effectuées dans la base de données ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}

### Prompt #X : Quels sont les mathématiques derrière cette technologie ?

{{% expand title="**Réponse de `duck.ai`**" %}}

...

{{% /expand %}}