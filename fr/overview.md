# Principes généraux

L’API Isogeo est disponible à l’adresse de base suivante : **https://v1.api.isogeo.com**. Il est possible de vérifier sa version via [about](https://v1.api.isogeo.com/about).

En cas de problème de vérification du certificat SSL :

* vérifiez que les certificats racine de GoDaddy sont bien installés sur votre plateforme \(c’est en général le cas\).
* l’API Isogeo est également disponible en HTTP \(sauf pour l’authentification\).

L’API Isogeo est une [API REST](https://restfulapi.net/) qui communique en [JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) \([type MIME](https://fr.wikipedia.org/wiki/Type_MIME) _application/json_\). À ce titre elle donne accès à des entités via des routes.

À titre expérimental une [description de l’API au format Swagger est disponible ici](http://v1.api.isogeo.com/swagger.json). Il est possible d’en avoir un aperçu \(pour la version en cours de développement\) en [annexe de cette documentation](/appendices/swagger.md) ou bien via l'interface Swagger à l’adresse http://chantiers.hq.isogeo.fr:1080/docs/Isogeo.Api/latest/Api.V1/.

