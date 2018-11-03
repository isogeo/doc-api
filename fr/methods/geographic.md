# Appliquer un filtre géographique

Dans Isogeo, les métadonnées peuvent contenir une enveloppe géographique \(mais ça n'est pas systématique\).

Elle est alors décrite comme un GeoJSON inclus dans le JSON renvoyé :

```js
            "envelope": {
                "bbox": [
                    1.53421117608959,
                    47.4932915310182,
                    3.12437082073202,
                    48.3342563074165
                ],
                "coordinates": [
                    [
                        [
                            1.53878873538249,
                            47.8421564892245
                        ],
                        [
                            1.56189864932977,
                            47.7901519658336
                        ],
                        [...]
                    ]
                ],
                "type": "Polygon"
            },
```

L'API permet de filtrer directement les résultats en tenant compte de cette enveloppe.

## Par emprise {#bbox}

> Paramètre : **box**

### Description

Renvoie les ressources dont l’enveloppe possède [la relation géographique spécifiée](#georel) avec l’emprise envoyée. Si la ressource ne possède pas d’enveloppe, elle n’est pas remontée. Les coordonnées de l’emprise sont en WGS84 \([EPSG 4326](https://epsg.io/4326)\) et respecte les [spécifications d’OpenSearch](http://www.opensearch.org/Specifications/OpenSearch/Extensions/Geo/1.0/Draft_2#The_.22box.22_parameter).

### Exemples

```js
/resources/search?box=-4.970,30.69418,8.258,51.237
```

---

## Par enveloppe {#geo}

> Paramètre : **geo**

### Description {#geo_descr}

Renvoie les ressources dont l’enveloppe possède [la relation géographique spécifiée](#georel) avec l’enveloppe envoyée. Si la ressource ne possède pas d’enveloppe, elle n’est pas remontée. L’enveloppe doit être décrite au format WKT.

### Exemples {#geo_example}

```js
/resources/search?geo=POLYGON((0.582%2040.496%2C%200.231%2040.737%2C%200.736%2042.869%2C%203.351%2042.386%2C%203.263%2041.814%2C%202.164%2041.265%2C%200.978%20%20%2040.957%2C%200.802%2040.781%2C%200.978%2040.649%2C%200.582%2040.496))
```

---

## Opérateurs spatiaux {#georel}

> Paramètre : **rel**

### Description {#georel_descr}

Permet de spécifier la requête spatiale appliquée pour filtrer les résultats dans une emprise ou une enveloppe polygonale.

Uniquement interprété si l'un des paramètres [_box_](#box) ou [_geo_](#geo) est passé.

### Valeurs possibles {#georel_values}

Les valeurs possibles sont basées sur les relations standard définies par l’OGC dans  [OGC 06-103r4](http://portal.opengeospatial.org/files/?artifact_id=25355) §6.1.15.

| Valeur | Opération appliquée |
| :--- | :--- |
| contains | les métadonnées renvoyées sont celles dont l'enveloppe **contient complètement** l’enveloppe envoyée |
| disjoint | les métadonnées renvoyées sont celles dont l'enveloppe **n'intersecte pas** l’enveloppe envoyée |
| equals | les métadonnées renvoyées sont celles dont l'enveloppe **est exactement** celle de l’enveloppe envoyée |
| **intersects** | les métadonnées renvoyées sont celles dont l'enveloppe **croise** l’enveloppe envoyée - VALEUR PAR DEFAUT |
| overlaps | les métadonnées renvoyées sont celles dont l'enveloppe **englobe** l'enveloppe envoyée |
| within | les métadonnées renvoyées sont celles dont l'enveloppe **est entièrement contenue** dans l’enveloppe envoyée |

En pratique, les valeurs les plus couramment utilisées sont :

* intersects
* within
* contains

### Exemples {#georel_example}

```js
/resources/search?geo=POLYGON((0.582%2040.496%2C%200.231%2040.737%2C%200.736%2042.869%2C%203.351%2042.386%2C%203.263%2041.814%2C%202.164%2041.265%2C%200.978%20%20%2040.957%2C%200.802%2040.781%2C%200.978%2040.649%2C%200.582%2040.496))&rel=within
```

---

## Cas particuliers

### Les paramètres _box_ et _geo_ sont tous les deux passés

Si les 2 paramètres sont présents dans la même requête, l'opérateur géométrique est forcément une intersection et le paramètre _georel_ est ignoré.

### Sens de numérisation des enveloppes

A DOCUMENTER
