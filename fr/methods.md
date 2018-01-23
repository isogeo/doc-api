# Rechercher avec l'API Isogeo


## Paramètres de recherche

## Requête (_q=_) {#query}


q=

## Langue (_lang_) {#lang}


## Filtre géographique {#lang}

### Par emprise {#bbox}


### Polygone {#geo}

#### Description

Enveloppe de recherche. Renvoie les ressources dont l’enveloppe possède la relation géographique spécifiée (intersection par défaut, cf. rel) avec l’enveloppe envoyée. Si la ressource ne possède pas d’enveloppe, elle n’est pas remontée. L’enveloppe doit être décrite au format WKT.

#### Exemples

```
/resources/search?geo=POLYGON((0.582%2040.496%2C%200.231%2040.737%2C%200.736%2042.869%2C%203.351%2042.386%2C%203.263%2041.814%2C%202.164%2041.265%2C%200.978%20%20%2040.957%2C%200.802%2040.781%2C%200.978%2040.649%2C%200.582%2040.496))
```

### Opérateurs géographiques {#rel}



