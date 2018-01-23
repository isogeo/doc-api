# Appliquer un filtre géographique



## Par emprise {#bbox}

### Description

Renvoie les ressources dont l’enveloppe possède [la relation géographique spécifiée](#georel) avec l’emprise envoyée. Si la ressource ne possède pas d’enveloppe, elle n’est pas remontée. Les coordonnées de l’emprise sont en WGS84 \([EPSG 4326](https://epsg.io/4326)\) et respecte les [spécifications d’OpenSearch](http://www.opensearch.org/Specifications/OpenSearch/Extensions/Geo/1.0/Draft_2#The_.22box.22_parameter).

### Exemples

```js
/resources/search?box=-4.970,30.69418,8.258,51.237
```

---

## Par enveloppe

### Description

Enveloppe de recherche. Renvoie les ressources dont l’enveloppe possède [la relation géographique spécifiée](#georel) avec l’enveloppe envoyée. Si la ressource ne possède pas d’enveloppe, elle n’est pas remontée. L’enveloppe doit être décrite au format WKT.

### Exemples

```js
/resources/search?geo=POLYGON((0.582%2040.496%2C%200.231%2040.737%2C%200.736%2042.869%2C%203.351%2042.386%2C%203.263%2041.814%2C%202.164%2041.265%2C%200.978%20%20%2040.957%2C%200.802%2040.781%2C%200.978%2040.649%2C%200.582%2040.496))
```

---

## Opérateurs géométriques {#georel}

### Description

Permet de spécifier la requête spatiale appliquée pour filtrer les résultats dans une emprise ou une enveloppe polygonale.

Uniquement interprété si les paramètres[box](https://docs.google.com/document/d/11dayY1FH1NETn6mn9Pt2y3n8ywVUD0DoKbCi9ct9ZRo/edit#heading=h.il7x5h5xccze)ou[geo](https://docs.google.com/document/d/11dayY1FH1NETn6mn9Pt2y3n8ywVUD0DoKbCi9ct9ZRo/edit#heading=h.7z2v039ma5po)sont passés. Si les 2 paramètres sont présents, une intersection est réalisée.

Les valeurs possibles sont basées sur les relations standard définies par l’OGC dans[OGC 06-103r4](http://portal.opengeospatial.org/files/?artifact_id=25355)§6.1.15.

Valeurs :

* contains: les métadonnées sont remontées si elles contiennent complètement l’enveloppe spécifiée.
* disjoint: les métadonnées sont remontées si elles n’intersectent pas l’enveloppe spécifiée.
* equals: les métadonnées sont remontées si leur enveloppe est la même que l’enveloppe spécifiée.
* intersects: \(défaut\) les métadonnées sont remontées si elles intersectent l’enveloppe spécifiée. Il s'agit de l'option par défaut.
* overlaps: les métadonnées sont remontées si elles chevauchent l’enveloppe spécifiée.
* within: les métadonnées sont remontées elles sont entièrement contenues dans l’enveloppe spécifiée.



En pratique, les valeurs les plus couramment utilisées sont :

* intersects
* within
* contains

### Exemples

```js
/resources/search?geo=POLYGON((0.582%2040.496%2C%200.231%2040.737%2C%200.736%2042.869%2C%203.351%2042.386%2C%203.263%2041.814%2C%202.164%2041.265%2C%200.978%20%20%2040.957%2C%200.802%2040.781%2C%200.978%2040.649%2C%200.582%2040.496))&rel=within
```



