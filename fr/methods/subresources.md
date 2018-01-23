## Sous-ressources à inclure dans le modèle des résultats {#limit}

> Paramètre : **\_include**

### Description

Ce paramètre permet de gérer les différentes extensions du modèle à renvoyer pour les résultats de recherche.

### Valeurs possibles

| Valeur | Description | Types de métadonnées concernés |
| :--- | :--- | :---: |
| conditions | conditions d'utilisation appliquées à ladonnée \(CGUs\) | tous |
| contacts | contacts de la donnée | tous |
| coordinate-system | système de coordonnées | vecteur et raster |
| events | événements sur la vie de la donnée | tous |
| feature-attributes | table attributaire du vecteur | vecteur |
| keywords | mots-clés Isogeo affectés à la métadonnée | tous |
| layers | couches diffusées par le service | service |
| limitations | limitations à l'usage appliquées à la donnée | tous |
| links | liens associés à la donnée | tous |
| operations | opérations disponibles sur le service | service |
| serviceLayers | couhes de service associées à la donnée | vecteur et raster |
| specifications | spécifications \(CCTP, standard...\) | vecteur, raster et service |

### Points de vigilance

A DOCUMENTER

### Exemples

```js
/resources/search?_include=contacts,links    # les résultats contiendront les informations sur les contacts et les liens asssociés
```

---



