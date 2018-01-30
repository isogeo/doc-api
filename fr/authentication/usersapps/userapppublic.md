# Applications utilisateur "publiques"



### Implicit Grant {#docs-internal-guid-945f0b5a-47a8-1283-3a9c-6046a096d628}

La documentation officielle de ce flot est disponible[dans la RFC 6749](http://tools.ietf.org/html/rfc6749#section-4.2).

  


La récupération d’unaccess tokense fait via un navigateur \(le navigateur en cours d’utilisation dans le cas d’une application web, un navigateur externe ou un navigateur embarqué dans le cas d’une application native\). Le client doit être redirigé sur la route d’autorisation[https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize):

* la requête est un GET vers[https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize)

* avec des paramètres qui indiquent :

* * response\_type:token

  * client\_id: l’identifiant OAuth de l’application.

  * redirect\_uri: l’adresse de l’application vers laquelle renvoyer le code d’autorisation \(préalablement enregistrée dans ses paramètres, par exemple[https://app.isogeo.com/login/callback](https://app.isogeo.com/login/callback)\).

  


En cas de succès le navigateur est redirigé vers la route de l’application spécifiée ci-dessus, avec les paramètres ajoutés en[fragment](https://en.wikipedia.org/wiki/Fragment_identifier):

* access\_token: le jeton d’accès.

* token\_type: bearer

expires\_in

: la durée de validité du jeton, en secondes.



