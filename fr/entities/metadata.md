# Métadonnées

Les métadonnées sont les principales entités qui sont manipulées dans Isogeo. Une métadonnée appartient à un seul [groupe](/group.md).

Une métadonnée contient :

- des champs *racines*
- des sous-ressources (attributs, limitations...)
- des objets associés (contacts, système de coordonnées...)

## Sous-ressources

| Sous-ressource     | Description                                                                 | Par défaut | Mode                          | Types de métadonnée |
| :----------------- | :-------------------------------------------------------------------------- | :--------: | :------------------------     | ------------------: |
| _abilities         | Les droits de l’utilisateur courant sur le groupe                           | NON        | ?_include=_abilities          | tous |
| _creator           | Les droits de l’utilisateur courant sur le groupe                           | **OUI**    | ?_include=_creator            | tous |
| conditions         | Les conditions (CGUs) qui s'appliquent à la donnée                          | NON        | ?_include=conditions          | tous |
| contacts           | Les contacts associés                                                       | NON        | ?_include=contacts            | tous |
| coordinate-system  | Le système de coordonnées de la donnée                                      | NON        | ?_include=coordinate-system   | vecteur et raster |
| events             | Les événements de l'historique de la donnée                                 | NON        | ?_include=events              | tous |
| feature-attributes | Les champs attributaires de la donnée                                       | NON        | ?_include=feature-attributes  | vecteur |
| keywords           | Les mots-clés Isogeo affectés à la métadonnée                               | NON        | ?_include=keywords            | tous |
| layers             | Les couches diffusées par le service                                        | NON        | ?_include=layers              | service |
| limitations        | Les limitations à l'usage appliquées à la donnée                            | NON        | ?_include=limitations         | tous |
| links              | Les liens associés à la donnée                                              | NON        | ?_include=links               | tous |
| operations         | Les opérations disponibles sur le service                                   | NON        | ?_include=operations          | service |
| serviceLayers      | Les couches de service associées à la donnée                                | NON        | ?_include=serviceLayers       | vecteur et raster |
| specifications     | Les spécifications                                                          | NON        | ?_include=specifications      | vecteur, raster et service |
| tags               | Les étiquettes associées à la métadonnée.                                   | **OUI**    | ?_include=tags                | tous |


### Exemple

```bash
# obtenir une métadonnée avec les droits et les contacts associés
GET /resources/{METADATA_UUID}/?_include=_abilities,contacts
# obtenir une métadonnée d'une fiche vecteur complète
GET /resources/{METADATA_UUID}/?_include=_abilities%2Cconditions%2Ccontacts%2Ccoordinate-system%2Cevents%2Cfeature-attributes%2Ckeywords%2Climitations%2Clinks%2Cspecifications%2CserviceLayers&_=1564498426430
```
