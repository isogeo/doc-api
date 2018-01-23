# Paginer les résultats

A l'instar de la plupart des API, 2 paramètres permettent de paginer les résultats.

## Longueur de la liste des résultats {#limit}

> Paramètre : **\_limit**

### Description

Nombre de résultats maximum retourné.

### Valeurs possibles

Un entier compris entre 0 et 100.  
Valeur par défaut : **20**.

### Exemples

```js
/resources/search?ob=_created&od=desc&_limit=1    # dernière métadonnée créée

/resources/search?ob=_modified&od=desc&_limit=100    # 100 dernières métadonnées modifiées
```

---

## Index de départ dans la liste de résultats {#offset}

> Paramètre : **\_offset**

### Description

Placement du curseur dans l'ensemble des résultats de la recherche.

### Valeurs possibles

Un entier compris entre 0 et le nombre maximum de résultats.  
Valeur par défaut : **0**.

### Exemples

```js
/resources/search?ob=_created&od=desc&_offset=20    # dernières fiches créées sauf les 20 premières (ou à partir de la 21è)
```



