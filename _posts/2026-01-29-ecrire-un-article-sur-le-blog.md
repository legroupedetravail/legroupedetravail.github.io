---
layout: post
title: Ecrire un article sur le blog
date: 2026-01-29 10:39 +0100
description: Comment écrire un article sur ce blog
image: 
categories: [Jekyll]
tags: Contribuer en écrivant un article
author: ala
---
# Avant d'écrire un article
- Ouvrir une Issue sur Github, y indiquer le thème de l'article
- Travailler sur la branche associée à cette Issue

# Une fois l'article écrit
- Une fois le travail terminé -> `Pull Request`

# Comment travailler en local sur le blog ?
Une fois la branche récupérée en local, lancer le Dev Container VSCode. 
Le Dev Container contient des extensions VS Code utiles, en particulier pour la prévisualisation du Markdown.

1. Lancer le Dev Container depuis VS Code, si l'éditeur ne le propose pas directement : `F1` ou `Ctrl+Shift+P` et lancer `Dev Containers: Rebuild & Reopen in Container` .
1. Une nouvelle fenêtre s'ouvre alors, attendre que le Container s'installe et démarre
1. Ouvrir un Terminal
1. Pour créer un article, utiliser la commande `bundle exec jekyll post "My New Post"`, ceci crée un fichier dans le répertoire `_posts`, si celui-ci n'apparaît pas directement, rafraîchir l'explorateur VS Code.
1. Ouvrir le fichier et mettre à jour les informations d'en-tête, laisser vide les infos inutilisées
1. Pour prévisualiser l'article pendant l'écriture, ouvrir la prévisulisation Markdown : `F1` ou `Ctrl + Shift + P` et lancer `Markdown: Open Preview`. On peut splitter l'éditeur pour avoir une visualisation en direct ! 
1. Le site peut être prévisualisé avec la commande `jekyll serve`, le site se lance par défaut sur le port 4000.

# Description de l'en-tête
```
---
layout: post
title: C'est assez parlant je pense
date: 2026-01-29 10:39 +0100
description: Comment écrire un article sur ce blog
image: 
categories: [Jekyll]
tags: contribuer rédiger article
author: ala
---
```

- Ne pas modifier la valeur de layout. 
En cas d'insertion d'images, les placer dans assets/img, indiquer alors le chemin dans le champ image.
- Les articles sont triés par catégories, on peut indiquer 2 niveaux de catégories, par exemple [Développement, C++]
- Pour l'auteur, indiquer vos 3 lettres, ces 3 lettres servent d'identifiant vers une description plus complète de l'auteur (dans _data/authors.yml).
