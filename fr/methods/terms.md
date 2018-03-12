# Termes de recherche


## Termes {#search_terms}


## Filtres sémantiques {#search_filters}


### Groupe de travail {#owner}

Dans Isogeo, chaque métadonnée appartient au groupe de travail (workgroup) dans lequel elle a été créée. De cette relation 1:1 découle un filtre sur le groupe de travail propriétaire des métadonnées.

> Structure : q=**owner:{WORKGROUP_ID}**

Caractéristiques :
* valeur obigatoire
* à la racine du modèle
* 1 seule occurrence possible

---

### Type de ressource {#type}

Dans Isogeo, chaque métadonnée indique le type de ressource qu'elle décrit. De cette relation 1:1 découle un filtre sur le type de ressources décrites.

> Structure : q=**type:{WORKGROUP_ID}**

Caractéristiques :
* valeur obigatoire
* à la racine du modèle
* 1 seule occurence possible

#### Valeurs possibles

| Valeur         | Ressource décrite                         |
| :------------- | :---------------------------------------- |
| dataset        | Jeu de données (vecteur OU raster)        |
| raster-dataset | Jeu de données **raster**                 |
| vector-dataset | Jeu de données vectorielles (**vecteur**) |
| service        | Service géographique                      |
| resource       | Ressource non géographique                |

Les différents types sont expliqués dans [le guide utilisateur](http://help.isogeo.com/fr/features/documentation/#les-diff%C3%A9rents-types-de-ressources).

### Exemples

```js
/resources/search?q=route type:dataset  # jeux de données contenant le mot 'routes'
```

---






