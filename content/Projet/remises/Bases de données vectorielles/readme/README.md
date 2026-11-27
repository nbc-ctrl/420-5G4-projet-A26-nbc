# Clonez le dépot

Ce site utilise de le thème relearn. Cette dépendance est mise comme un sous module.

`$ git clone --recurse-submodules <url>`

Autrement après un clone simple :

`$ git submodule init`

`$ git submodule update`

Si vous oubliez cette étape, la commande `$ hugo serve` retournera une erreur.

# Testez vos changements

Ce site Hugo a besoin de la version 148.1 minimum à cause de sa dépendance au thème relearn.

Créez un dev container avec vscode en utilisant le Dockerfile fourni :

1. `ctrl+shift+p`
1. Dev Containers: Open Folder in Container...
1. Sélectionnez le dossier racine de ce projet et cliquez sur **Ouvrir** (_Open_).
1. add configs to workspace
1. From 'Dockerfile'
1. ok
1. ok

Faites vos modifications dans la partie `content` du site.

> [!warning]
> N'ajoutez pas de fichiez volumineux au dépot. Maximum 1Mo pour une image.
>
> Git est fait pour gérer du texte, les gros fichiers binaire endommage les performances du dépot.
>
> Si vous devez joindre un fichier volumineux, stockez le quelque part en ligne, et faite un lien vers votre fichier.

Dans un terminal du dev container, vous pouvez taper la commande suivante :
`$ hugo serve`

Vous aurez un serveur web de test disponible à l'adresse http://127.0.0.1:1313/420-5G4/

> [!TIP]
> Le script `start_hugo.sh` peut vous servir d'inspiration si vous souhaitez exécuter votre container manuellement (hors de vscode).
> L'image du script à été construite avec `docker build -t hugo_relearn .`

# Idée générale du laboratoire

Avec Jupiter Notebook (au autre, à déterminer plus tard), faire une petite base de données vectorielles, et créer une liste de données (images, sons, phrases), convertir les données en vecteurs, visualiser les vecteurs (observer les dimensions, et les voirs dans un graphique), et insérer les vecteurs dans la base de données, puis faire une recherche dans la liste de données par mots clés et ensuite faire une recherche dans la base de données vectorielles par recherche vectorielle.
 > Si cela ne suffit pas :
 Avant de faire la base de données vectorielles, simuler avec des maths simples avec python ce que l'IA fait avec la liste de données.

  > Et si cela ne suffit pas :
 Faire un exercice de préparation de données avant insertion dans la BD.

# Idées de sujet à explorer dans les notes de cours

- Insertion de biais dans le embedding ?
- Comparaison des BD traditionnelles vs BD vectorielles.
- Depuis quand existe les bases de données vectorielles ?
- Explication des calculs sur les vecteurs effectués lors de la recherche.
- Explication du processus :
    - Insertion des données dans la BD
    - Embedding
    - Recherche
    - Retour des données
- Quand faut-il utiliser les bases de données vectorielles (quand est-ce nécessaire et quand est-ce superflus) ?
