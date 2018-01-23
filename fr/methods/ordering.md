# Trier les résultats

## Critère de tri {#ob}

> Paramètre : **ob**

### Description

_ob_ signifie _OrderBy_ et permet de trier les résultats de la recherche selon plusieurs critères.

Par défaut, les résultats de recherche sont triés par score de pertinence \([voir ici pour le mode de calcul](http://help.isogeo.com/fr/features/inventory/search.html#pertinence-)\) selon les [termes libres passés au paramètre _q_](/methods/terms.md).

Si aucun terme n'est envoyé, le score de pertinence est donc le même pour tous les résultats et c'est alors la date de création de la métadonnée qui sert de valeur par défaut.

**Attention :** il y a un fort risque de confusion entre les dates concernant la métadonnée et celles concernant la donnée \(ou le service ou la ressource\) décrite par sa métadonnée. Être attentif à l'underscore dans le tableau des valeurs possibles ci-dessous. Pour une information plus complète, consulter [l'annexe sur les différentes dates dans Isogeo](http://help.isogeo.com/fr/appendices/different_dates.html).

### Valeurs possibles

Le tableau ci-dessous indique les valeurs acceptées pour le paramètre _ob_.


| Valeur | Description | Présence systématique |
| :--- | :--- | :--- |
| \_created | date de création de la **métadonnée** | OUI |
| \_modified | date de dernière mise à jour de la **métadonnée** | OUI |
| created | date de création de la **donnée** | NON |
| modified | date de dernière mise à jour de la **donnée** | NON |
| **relevance** | pertinence par apport aux termes de recherche - VALEUR PAR DEFAUT | Quand un terme de recherche est saisi |
| title | titre de la métadonnée | OUI |


### Points de vigilance

#### Métadonnée ou donnée : _underscore rules!_

Il y a un fort risque de confusion entre les dates concernant la métadonnée et celles concernant la donnée \(ou le service ou la ressource\) décrite par sa métadonnée. Être attentif à l'underscore dans le tableau des valeurs possibles ci-dessous. Pour une information plus complète, consulter [l'annexe sur les différentes dates dans Isogeo](http://help.isogeo.com/fr/appendices/different_dates.html).

#### Tri inopérant



### Exemples

```js
/resources/search?ob=title
```

---

## Sens du tri {#od}

> Paramètre : **od**

### Description

Signifie OrderDirection. Permet de choisir le sens du tri.

### Valeurs possibles

| Valeur    | Description |
| :-------- | :---------- |
| **desc ** | descendant  |
| asc       | ascendant   |

### Exemples

```js
/resources/search?ob=title&od=asc  # tri par ordre alphabétique.
```



