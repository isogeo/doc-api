# Systèmes de coordonnées {#coordinate-system}

Par défaut, l'information du système de coordonnées du jeu de données source n'est pas détaillé. Il faut donc le demander spécifiquement via [le paramètre `_include`](/methods/subresources.html).

> _include=coordinate-system


## Exemple

### Par défaut {#default}

```json
"tags": {
    [...],
    "coordinate-system:4326": "WGS 84",
    [...],
    },
```

### Détaillé {#included}

```json
"coordinate-system": {
    "_tag": "coordinate-system:4326",
    "code": 4326,
    "name": "WGS 84"
    },
```
