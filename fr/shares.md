# Partages

Cette route permet d'accéder aux détails sur les partages alimentant l'application authentifiée.

## Cas d'usage {#use-cases}

Cette possibilité est utile dans différents cas de figure :

- on souhaite afficher les caractéristiques de l'application pour informer l'utilisateur (nombre de partages et de groupes de travail qui alimentent l'application...), par exemple dans une fenêtre du type "A propos". C'est le cas du plugin pour QGIS et d'Isogeo To Office.

- on souhaite générer des liens de visualisation sur OpenCatalog. Ces routes permettent de vérifier qu'OpenCatalog est bien présent dans le même partage que l'application

- gérer une [ségrégation d'affichage par partages](methods/segregate.html), comme c'est le cas d'OpenCatalog ou du portail de données.

## Routes

| Verbe HTTP | URI            | Description |
| :---       | :--------------| :---------- |
| GET        | /shares        | Liste des partages alimentant l'application  |
| GET        | /shares/{:sid} | Caractéristiques d'un partage en particulier |
