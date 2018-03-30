# Routes accessibles pour les applications de groupe

Les applications tierces utilisant le flot d'authentification oAuth2 de type _Client Credentials Grant_, accèdent au _scope_ **resources:read**. Les routes accessibles par ce scope sont détaillées ci-après.

> les valeurs entre **{}** sont des identifiants à remplacer (crochets inclus) lors des requêtes

| Route                  | Description                  |
| :--------------------- | :--------------------------- |
| /licenses/{lid} | Consulter le détail d'une licence |
| /link-kinds | Lister les types de liens possibles |
| /resources/{rid} | Consulter une métadonnée en détail |
| /resources/{rid}.xml | Télécharger une métadonnée au format XML ISO 19139 |
| /resources/{rid}/conditions | Lister les conditions (licences) appliquées à une métadonnée |
| /resources/{rid}/conditions/{id} | Consulter les détails d'une condition en particulier |
| /resources/{rid}/contacts | Lister les contacts affectés à une métadonnée |
| /resources/{rid}/coordinate-system | Lister le système de coordonnées d'une métadonnée |
| /resources/{rid}/events | Lister les événements d'une métadonnée |
| /resources/{rid}/events/{id} | Consulter les détails d'un événement en particulier (nom, type, date, description) |
| /resources/{rid}/feature-attributes | Lister les attributs d'une donnée vectorielle |
| /resources/{rid}/feature-attributes/{name} | Consulter les détails d'un attribut en particulier (nom, alias, description, type) |
| /resources/{rid}/limitations | Lister les limitations appliquées à une métadonnée |
| /resources/{rid}/limitations/{id} | Consulter les détails d'une limitation en particulier |
| /resources/{rid}/links | Lister les liens liées à une métadonnée |
| /resources/{rid}/links/{id} | Consulter les détails d'un lien en particulier |
| /resources/{rid}/links/{id}.bin | Télécharger le fichier téléversé lié à la métadonnée |
| /resources/{rid}/specifications | Lister les spécifications liées à une métadonnée |
| /resources/{rid}/thumbnail/{id} | Consulter les détails de la vignette liée à une métadonnée (générée par l'ancien daemon) |
| /resources/{rid}/thumbnail/{id}.png | Télécharger la vignette liée à une métadonnée (générée par l'ancien daemon) |
| /resources/{rid}/keywords | Lister les étiquettes (mots-clés, thèmes INSPIRE...) affectés à une métadonnée |
| /resources/{rid}/layers | Lister les couches de services associées à une métadonnée |
| /resources/{rid}/layers/{lid} | Consulter les détails d'une couche de service assoicée particulier |
| /resources/{rid}/operations | Lister les opérations disponibles sur un service |
| /resources/{rid}/operations/{oid} | Consulter les détails d'une opération sur un service (nom, type MIME, verbes...) |
| /resources/search | Chercher parmi les métadonnées partagées à l'application |
| /shares | Lister les partages alimentant l'application tierce |
| /shares/{sid} | Consulter les détails d'un partage en particuleir parmi ceux alimentant l'application tierce |
| /specifications/{sid} | Consulter les détails d'une spécification en particulier |
| /thesauri | Lister les thésauri |
| /thesauri/{tid} | Consulter les détails d'un thésaurus |
| /thesauri/{tid}/keywords/{kid} | Consulter les détails d'un mot-clé en particulier d'un thésaurus |
| /thesauri/{tid}/keywords/search | Chercher parmi les mots-clés d'un thésaurus en particulier |
