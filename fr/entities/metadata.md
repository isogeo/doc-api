# Métadonnées

Les métadonnées sont les principales entités qui sont manipulées dans Isogeo. Une métadonnée appartient à un seul [groupe](/group.md).

Une métadonnée contient :

- des champs *racines*
- des sous-ressources (attributs, limitations...)
- des objets associés (contacts, système de coordonnées...)

## Principales caratéristiques {#main_characteristics}

### Type de source décrite (#types)

{% include "./enums/metadata_types.md" %}

## Sous-ressources {#include_subresources}

{% include "./subresources/metadata.md" %}

### Exemple

```bash
# obtenir une métadonnée avec les droits et les contacts associés
GET /resources/{METADATA_UUID}/?_include=_abilities,contacts
# obtenir une métadonnée d'une fiche vecteur complète
GET /resources/{METADATA_UUID}/?_include=_abilities%2Cconditions%2Ccontacts%2Ccoordinate-system%2Cevents%2Cfeature-attributes%2Ckeywords%2Climitations%2Clinks%2Cspecifications%2CserviceLayers&_=1564498426430
```
