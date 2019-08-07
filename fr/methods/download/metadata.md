# Télécharger les métadonnées

Dans Isogeo, toute métadonnée est en permanence accessible dans 2 versions :

- la version JSON, renvoyée par défaut lors des appels à l'API
- la version XML conforme à ISO 19139

## Télécharger une métadonnée XML ISO 19139

> Route : GET /resources/{:rid}.xml


Pour accéder à la version XML, il faut utiliser la route du dtéil d'une métadonnée et ajouter l'extension `.xml` en queue d'URL.


| Valeur | Opération appliquée |
| :--- | :--- |
| id| xxxx |
| proxyUrl| xxx |




**Autres ressources  :** le téléchargement de la métadonnée en XML ISO 19139 est implémentée dans le package Python. [Consulter la documentation](https://isogeo-api-pysdk.readthedocs.io/en/latest/usage.html#download-metadata-as-xml-iso-19139).