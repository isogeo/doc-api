# Glossaire

# Métadonnée

Nommée _resource_ dans le code, c'est la principale entité de l'API Isogeo. Appartenant au groupe de travail \(_workgroup_\) qui l'a créée, elle décrit un jeu de données \(vectoriel ou raster\), un service géographique ou une ressource non géographique.

# oAuth

Protocole d'authentification qui permet d'autoriser un site web, un logiciel ou une application \(dite « consommateur »\) à utiliser l'API sécurisée d'un autre site web \(dit « fournisseur »\) pour le compte d'un utilisateur ou d'une application enregistré/e. Voir [https://oauth.net/](https://oauth.net/).

## _access token_

L'_ac\_ccess \_token_ \(ou jeton d’accès\) permet à l'application cliente d’accéder aux ressources authentifiées. Ce _token_ a une durée de validité limitée à 1h et sa portée est limitée en lecture seule.

## _refresh token_

Le _refresh token_ \(ou jeton de rafraîchissement\) permet à l'application cliente d’obtenir un nouveau _access token_ une fois que celui-ci a expiré,  sans l’intervention du propriétaire de la ressource protégée. Sa durée de validité est aussi limitée mais est beaucoup plus élevée que celle de l'_access token_.

