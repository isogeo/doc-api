# Filtres sémantiques {#search_filters}

> Paramètre : **q**

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

> Structure : q=**type:{TYPE_CODE_VALUE}**

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

#### Exemples

```js
/resources/search?q=route type:dataset  # jeux de données contenant le mot 'routes'
```

---

### Actions liées {#action}
 
Une métadonnée peut contenir des liens (_links_) que l'utilisateur qualifie selon leur action finale.

> Structure : q=**action:{ACTION_CODE_VALUE}**

Caractéristiques :
* champ optionnel
* les liens sont visibles dans la sous-ressource _links_
* plusieurs valeurs possibles


#### Valeurs possibles

| Valeur   | Description                          |
| :------- | :----------------------------------- |
| download | Lien de téléchargement               |
| other    | Autre type de lien (site externe...) |
| view     | Lien de visualisation                |

#### Exemples

```js
/resources/search?q=type:dataset action:download   # jeux de données ayant au moins un lien de téléchargement
/resources/search?q=has-no:action  # toute ressource sans aucune action
```

---

### Mots-clés {#keyword}
 
Une métadonnée peut contenir 0 - n mots-clés définis par l'utilisateur lors de l'étiquetage (édition).

> Structure : q=**keyword:isogeo:{KEYWORD_CODE_VALUE}**

Caractéristiques :
* champ optionnel
* les keywords sont visibles dans la sous-ressource _keywords_
* plusieurs valeurs possibles

#### Exemples

```js
/resources/search?q=type:dataset keyword:isogeo:2014   # jeux de données ayant le mot-clé '2014'
/resources/search?q=has-no:keyword  # toute ressource sans aucun mot-clé
```

---

### Formats source {#format}
 
Une métadonnée peut contenir le format source du jeu de données décrit. Ce format peut être renseigné par le Scan FME ou manuellement.

> Structure : q=**format:{FORMAT_CODE_VALUE}**

Caractéristiques :
* champ optionnel
* les formats  sont visibles dans la sous-ressource _keywords_
* une seule valeur possible

#### Exemples

```js
/resources/search?q=format:shp   # métadonnées dont le format est Esri Shapefiles
/resources/search?q=has-no:format  # toute ressource dont le format n'est pas décrit
```

---

### Fournisseur {#provider}
 
Une métadonnée peut contenir 0 - n mots-clés définis par l'utilisateur lors de l'étiquetage (édition).

> Structure : q=**provider:manual**

Caractéristiques :
* champ optionnel
* les keywords sont visibles dans la sous-ressource _keywords_
* plusieurs valeurs possibles

#### Exemples

```js
/resources/search?q=format:shp   # métadonnées dont le format est Esri Shapefiles
/resources/search?q=has-no:keyword  # toute ressource sans aucun mot-clé
```

---



