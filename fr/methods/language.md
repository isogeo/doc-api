# Langue appliquée à la recherche

> Paramètre : **_lang**

## Description

Certaines informations sont disponibles en plusieurs langues : les thèmes INSPIRE par exemple.

## Valeurs possibles

| Valeur | Description                  |
| :----- | :--------------------------- |
| en     | anglais                      |
| **fr** | français - VALEUR PAR DEFAUT |

## Exemples

### Résultats en français

```js
/resources/search?
# ou
/resources/search?_lang=fr
```

Donne :

```js
{
  "keyword:inspire-theme:addresses": "Adresses",
  "keyword:inspire-theme:administrativeunits": "Unités administratives",
  "keyword:inspire-theme:agriculturalandaquaculturefacilities": "Installations agricoles et aquacoles",
  "keyword:inspire-theme:areamanagementrestrictionregulationzonesandreportingunits": "Zones de gestion, de restriction ou de réglementation et unités de déclaration",
  "keyword:inspire-theme:atmosphericconditions": "Conditions atmosphériques",
  "keyword:inspire-theme:biogeographicalregions": "Régions biogéographiques",
  "keyword:inspire-theme:buildings": "Bâtiments",
  "keyword:inspire-theme:cadastralparcels": "Parcelles cadastrales"
}
```

### Résultats en anglais

```js
/resources/search?_lang=en
```

Donne :

```js
{
  "keyword:inspire-theme:addresses": "Addresses",
  "keyword:inspire-theme:administrativeunits": "Administrative units",
  "keyword:inspire-theme:agriculturalandaquaculturefacilities": "Agricultural and aquaculture facilities",
  "keyword:inspire-theme:areamanagementrestrictionregulationzonesandreportingunits": "Area management/restriction/regulation zones and reporting units",
  "keyword:inspire-theme:atmosphericconditions": "Atmospheric conditions",
  "keyword:inspire-theme:biogeographicalregions": "Bio-geographical regions",
  "keyword:inspire-theme:buildings": "Buildings",
  "keyword:inspire-theme:cadastralparcels": "Cadastral parcels"
}
```
