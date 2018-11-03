# Principes généraux

L’API Isogeo est disponible à l’adresse de base suivante : [https://v1.api.isogeo.com](https://v1.api.isogeo.com). Il est possible de vérifier sa version via [about](https://v1.api.isogeo.com/about).

En cas de problème de vérification du certificat SSL :

* vérifiez que les certificats racine de GoDaddy sont bien installés sur votre plateforme \(c’est en général le cas\).
* l’API Isogeo est également disponible en HTTP \(sauf pour l’authentification\).

L’API Isogeo est une [API REST](https://restfulapi.net/) qui communique en [JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) \([type MIME](https://fr.wikipedia.org/wiki/Type_MIME) _application/json_\). À ce titre elle donne accès à des entités via des routes.

## Authentification

![Logo oAuth2](https://oauth.net/images/oauth-2-sm.png)

L’authentification à l’API Isogeo se fait via [le protocole OAuth 2.0](https://tools.ietf.org/html/rfc6749) :

* vous devez être en possession de vos identifiants d’application \(_client\_id_ et _client\_secret_\) qui vous ont été fournis directement par l’équipe Isogeo.

* votre application peut récupérer un _access token_ via les routes d’authentification disponibles :
  * autorisation :[https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize)
  * token :[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token)

* les flots d’autorisation dépendent de la configuration de votre application :
  * application utilisateur confidentielle : _Authorization Code Grant_.
  * application utilisateur publique : _Implicit Grant_.
  * application de groupe : _Client Credentials Grant_.

* un _access token_ valide doit être envoyé à la plateforme Isogeo lors de chaque appel à l’API via  [un en-tête d’authentification de type Bearer](https://tools.ietf.org/html/rfc6750#section-2).

* un _access token_ a une date d’expiration et doit être renouvelé régulièrement, éventuellement avec un  _refresh token_.

Une description technique plus complète de l’authentification Isogeo est disponible dans [une section dédiée de cette documentation](/authentication/concepts.md).

## Utilisation d'un proxy

Dans le cas d’une application web il est en général nécessaire de faire transiter les appels à l’API Isogeo via un proxy, entre autres pour des raisons de sécurité (confidentialité des identifiants d’application ou des tokens d’authentification). C’est la raison pour laquelle l’API Isogeo ne supporte pas les appels _[Cross Origin](https://fr.wikipedia.org/wiki/Cross-origin_resource_sharing)_.

Le développeur de l’application est responsable de la sécurisation de son proxy :

* contre les attaques ([DoS](https://fr.wikipedia.org/wiki/Attaque_par_d%C3%A9ni_de_service) par exemple).
* contre la fuite de données confidentielles dans le cas d’une application à usage restreint (contre les moteurs de recherche par exemple).

Une description plus complète des proxies est disponible dans [une section dédiée de cette documentation](/proxy/concept.md).

## Autres ressources

À titre expérimental une [description de l’API au format Swagger est disponible ici](http://v1.api.isogeo.com/swagger.json). Il est possible d’en avoir un aperçu \(pour la version en cours de développement\) en [annexe de cette documentation](/appendices/swagger.md) ou bien via l'interface Swagger à l’adresse [http://chantiers.hq.isogeo.fr:1080/docs/Isogeo.Api/latest/Api.V1/](http://chantiers.hq.isogeo.fr:1080/docs/Isogeo.Api/latest/Api.V1/).
