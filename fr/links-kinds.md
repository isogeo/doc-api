# Types de liens

Les liens permettent de lier des ressources externes à une fiche de métadonnée. Ils sont renvoyés dans les résultats d'une recherche ou d'une métadonné détaillée lorsque la paramètre `_include`contient la valeur `links`.

> [Consulter la page détaillée des liens](/resources/subresources/links.md).

Cette route permet de lister les types de liens et les actions associées possibles.

## Route

| Verbe HTTP | URI            | Description                                 |
| :---       | :--------------| :------------------------------------------ |
| GET        | /link-kinds    | Dictionnaire des types de liens et actions  |

### Réponse

La réponse est toujours la même :

```js
[
    {
        "actions": [
            "download",
            "view",
            "other"
        ],
        "kind": "url",
        "name": "Link"
    },
    {
        "actions": [
            "download",
            "view",
            "other"
        ],
        "kind": "wfs",
        "name": "WFS service"
    },
    {
        "actions": [
            "view",
            "other"
        ],
        "kind": "wms",
        "name": "WMS service"
    },
    {
        "actions": [
            "view",
            "other"
        ],
        "kind": "wmts",
        "name": "WMTS service"
    },
    {
        "actions": [
            "download",
            "view",
            "other"
        ],
        "kind": "esriFeatureService",
        "name": "ESRI Feature Service"
    },
    {
        "actions": [
            "view",
            "other"
        ],
        "kind": "esriMapService",
        "name": "ESRI Map Service"
    },
    {
        "actions": [
            "view",
            "other"
        ],
        "kind": "esriTileService",
        "name": "ESRI Tile Service"
    },
    {
        "actions": [
            "download",
            "other"
        ],
        "kind": "data",
        "name": "Raw data"
    }
]
```
