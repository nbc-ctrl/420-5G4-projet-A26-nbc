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

- Source # 1 : https://weaviate.io/blog/what-is-a-vector-database

- Source # 2 : https://www.oracle.com/database/vector-search/

- Source # 3 : https://labelbox.com/blog/how-vector-similarity-search-works/

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

- Source # 1 : https://www.ibm.com/think/topics/rag-vector-database

- Source # 2 : https://redis.io/blog/vector-database-use-cases/

- Source # 3 : https://www.couchbase.com/blog/vector-database-use-cases-2/

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

- Source # 1 : https://unstructured.io/insights/vector-embeddings-the-key-to-better-search-relevance

- Source # 2 : https://www.pinecone.io/learn/vector-search-filtering/

- Source # 3 : https://www.elastic.co/search-labs/blog/vector-search-filtering

{{% /expand %}}

### Prompt #4 : Comment insere-t-on des données dans une base de données vectorielles ?

{{% expand title="**Réponse de `duck.ai`**" %}}

Le plus souvent, on n’insère pas seulement le texte brut : on le transforme d’abord en **vecteur (embedding)**, puis on enregistre ce vecteur avec un identifiant et, éventuellement, le texte ou des métadonnées associées.

Le processus typique est le suivant :

1. **Préparer les données** : nettoyer les documents et, s’ils sont longs, les découper en passages cohérents.
2. **Créer les embeddings** : envoyer chaque passage à un modèle d’embeddings, qui renvoie une liste de nombres. Le même modèle doit ensuite servir à vectoriser les requêtes de recherche.
3. **Enregistrer les enregistrements** : transmettre à la base un identifiant stable, le vecteur et les métadonnées utiles — par exemple le titre, la source, la date ou les droits d’accès. Le texte peut être conservé dans les métadonnées ou dans une autre base, liée par l’identifiant.
4. **Insérer ou mettre à jour** : beaucoup de systèmes proposent une opération appelée *upsert*; elle ajoute un enregistrement ou met à jour celui qui porte déjà le même identifiant. <citation src="1"></citation>

Pour un document découpé en passages, chaque passage reçoit généralement son propre identifiant et son propre vecteur. Il faut aussi prévoir comment supprimer ou actualiser les anciens passages lorsque le document source change.

Schématiquement :

```text
document → passages → embeddings → {identifiant, vecteur, métadonnées} → base vectorielle
```

Les appels précis dépendent de la base et de la bibliothèque choisies. Si vous me dites laquelle vous utilisez — par exemple PostgreSQL avec une extension vectorielle ou un service spécialisé — je peux montrer la forme d’insertion adaptée.

- Source # 1 : https://docs.oracle.com/en/cloud/paas/autonomous-vector-database/vecdb/upsert-records.html

{{% /expand %}}

### Prompt #5 : Comment fait-on des requêtes auprès de base de données vectorielles ?

{{% expand title="**Réponse de `duck.ai`**" %}}

Une requête vectorielle suit généralement ces étapes :

1. **Transformer la question en vecteur** avec le même modèle d’embeddings que celui utilisé pour indexer les données.
2. **Chercher les vecteurs les plus proches** dans la base, selon une mesure comme la similarité cosinus ou la distance euclidienne.
3. **Limiter et filtrer les résultats** : par exemple, demander les 5 passages les plus pertinents (`top_k = 5`) dans une catégorie ou une période donnée.
4. **Récupérer les contenus associés** — texte, identifiant et métadonnées — puis, si nécessaire, les transmettre à une autre étape, comme un modèle génératif. <citation src="5"></citation>

Schématiquement :

```text
question → embedding de la question → recherche des voisins proches
         → top-k résultats + filtres → contenus correspondants
```

La requête peut donc associer **similarité vectorielle** et **filtres classiques** : « trouve les passages proches de cette question, mais seulement dans les documents publiés cette année ». Les filtres peuvent être appliqués avant ou pendant la recherche, selon la base; leur prise en charge et leur effet sur le nombre de résultats varient. <citation src="1,2"></citation>

À noter : une recherche vectorielle renvoie des éléments **proches selon le modèle**, pas nécessairement la réponse exacte. Pour une recherche plus précise, on peut combiner vecteurs et mots-clés, puis éventuellement reclasser les résultats. <citation src="5"></citation>

- Source # 1 : https://unstructured.io/insights/vector-embeddings-the-key-to-better-search-relevance

- Source # 2 : https://www.pinecone.io/learn/vector-search-filtering/

- Source # 3 : https://www.elastic.co/search-labs/blog/vector-search-filtering

{{% /expand %}}

### Prompt #6 : Quand l'IA intervient-il dans cette technologie ?

{{% expand title="**Réponse de `duck.ai`**" %}}

L’IA intervient surtout **avant et autour de la base**, pas forcément dans la base elle-même :

1. **À l’indexation**, un modèle d’IA transforme chaque texte, image ou autre contenu en vecteur (*embedding*).
2. **À la recherche**, le même type de modèle transforme la question de l’utilisateur en vecteur. La base compare alors ce vecteur à ceux qu’elle stocke — cette comparaison de proximité est généralement un calcul mathématique, pas une réponse générée par l’IA.
3. **Facultativement**, un autre modèle peut réordonner les résultats pour mieux faire ressortir les passages pertinents.
4. **Dans un système RAG**, un modèle génératif peut ensuite lire les passages retrouvés et rédiger une réponse à partir de ceux-ci. <citation src="1,3"></citation>

Donc, la base vectorielle sert principalement à **stocker et retrouver** les vecteurs; les modèles d’IA les créent et peuvent exploiter les résultats. Une recherche vectorielle peut aussi être utilisée sans modèle génératif, par exemple pour trouver des documents similaires.

- Source # 1 : https://www.ibm.com/think/topics/rag-vector-database

- Source # 2 : https://ubuntu.com/blog/hybrid-search-and-reranking-a-deeper-look-at-rag

{{% /expand %}}

### Prompt #7 : Quel est le mécanisme derrière le _embedding_ ?

{{% expand title="**Réponse de `duck.ai`**" %}}

Pour du texte, un modèle d’embedding transforme une phrase en une liste de nombres qui sert de **représentation compacte** de son contenu. Le mécanisme, en simplifié :

1. **Découpage en tokens** : le texte est séparé en mots ou fragments de mots.
2. **Calcul par le modèle** : un réseau neuronal traite ces tokens et leur contexte, puis combine les informations apprises pendant son entraînement.
3. **Production du vecteur** : le modèle renvoie une suite de nombres, par exemple `[0,12, -0,34, 0,56, …]`.
4. **Comparaison** : on mesure la proximité entre vecteurs. Des textes qui se ressemblent selon ce que le modèle a appris tendent à être proches dans cet espace numérique. <citation src="1,2"></citation>

Pendant l’entraînement, le modèle apprend à représenter les éléments utiles à sa tâche. Par exemple, des méthodes d’apprentissage rapprochent des éléments jugés similaires et éloignent ceux jugés différents. Les coordonnées du vecteur ne correspondent généralement pas à des étiquettes simples comme « sujet » ou « ton » : le sens est réparti dans l’ensemble du vecteur. <citation src="2"></citation>

Une nuance importante : l’embedding ne constitue pas une compréhension humaine du texte. C’est une représentation numérique apprise; sa qualité dépend du modèle, de ses données d’entraînement et de la tâche visée. **Le même texte peut aussi produire des vecteurs différents selon le modèle utilisé.**

- Source # 1 : https://developers.google.com/machine-learning/crash-course/embeddings

- Source # 2 : https://stackoverflow.blog/2023/11/09/an-intuitive-introduction-to-text-embeddings/

{{% /expand %}}

### Prompt #8 : Quel est le mécanisme derrière les recherches effectuées dans la base de données ?

{{% expand title="**Réponse de `duck.ai`**" %}}

Quand une recherche est lancée, la base compare le **vecteur de la requête** aux vecteurs enregistrés et renvoie les plus proches selon une mesure choisie, par exemple la distance cosinus ou euclidienne. Elle associe ensuite ces vecteurs aux contenus correspondants (documents, images, métadonnées).

Avec peu de données, elle peut comparer la requête à **tous** les vecteurs. À grande échelle, elle utilise souvent un index de recherche approximative pour examiner rapidement un sous-ensemble de candidats. Par exemple, HNSW navigue dans un graphe de vecteurs voisins; IVF répartit les vecteurs en groupes et cherche d’abord dans les groupes les plus prometteurs. Ces méthodes accélèrent la recherche, au prix possible de manquer certains voisins très proches. <citation src="3,4"></citation>

Enfin, la base peut appliquer des filtres — comme une catégorie, une date ou un accès autorisé — puis classer les candidats et retourner les *k* meilleurs résultats. En résumé : **représenter la requête en vecteur → repérer des candidats proches → filtrer et classer → renvoyer les contenus associés**.

- Source # 1 : https://fit.neu.edu.vn/en/post/hnsw-approximate-nearest-neighbor-search-for-vector-databases

- Source # 2 : https://milvus.io/blog/understanding-ivf-vector-index-how-It-works-and-when-to-choose-it-over-hnsw.md

{{% /expand %}}

### Prompt #X : Quels sont les mathématiques derrière cette technologie ?

{{% expand title="**Réponse de `duck.ai`**" %}}

Les mathématiques reposent surtout sur **la géométrie des vecteurs**, puis sur des méthodes pour chercher efficacement parmi beaucoup de vecteurs.

1. **Représenter un élément par un point**  
   Un embedding est un vecteur de \(d\) nombres, par exemple \(\mathbf{x}=(x_1,\ldots,x_d)\). On peut le voir comme un point dans un espace à \(d\) dimensions. Les dimensions n’ont généralement pas d’interprétation humaine simple.

2. **Mesurer la proximité entre deux vecteurs**  
   La base compare le vecteur de la question \(\mathbf{q}\) à ceux des documents. Les mesures courantes sont :
   - **Distance euclidienne** : \(\|\mathbf{q}-\mathbf{x}\|_2\), la distance en ligne droite entre deux points.
   - **Similarité cosinus** : \(\frac{\mathbf{q}\cdot\mathbf{x}}{\|\mathbf{q}\|\,\|\mathbf{x}\|}\), qui compare surtout leur direction.
   - **Produit scalaire** : \(\mathbf{q}\cdot\mathbf{x}=\sum_i q_i x_i\), qui tient compte de l’alignement et de la longueur des vecteurs. <citation src="1,3"></citation>

   La base classe les résultats selon la mesure choisie. Pour une distance, les valeurs les plus petites sont généralement préférées; pour une similarité, ce sont les plus grandes.

3. **Trouver les meilleurs résultats**  
   Le principe consiste à chercher les \(k\) vecteurs les plus proches — les *k plus proches voisins*. On peut comparer la requête à tous les vecteurs, ou utiliser un index approximatif qui explore moins de candidats pour accélérer la recherche, avec un compromis possible sur la précision. <citation src="1,4"></citation>

La qualité du résultat dépend donc de deux choses : **la qualité des embeddings**, qui place les contenus dans cet espace, et **la mesure/index de recherche**, qui détermine quels voisins sont retournés. La proximité mathématique indique une ressemblance selon le modèle; elle ne garantit pas à elle seule que le résultat soit vrai ou pertinent.

- Source # 1 : https://docs.cloud.google.com/spanner/docs/find-k-nearest-neighbors

- Source # 2 : https://www.pinecone.io/learn/vector-similarity/

- Source # 3 : https://weaviate.io/blog/distance-metrics-in-vector-search

{{% /expand %}}