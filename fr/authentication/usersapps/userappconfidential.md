# Applications utilisateur "confidentielles" - Authentification {#userapp-authentication}

## Paramètres d'accès {#userapp-confidential-access}

L'équipe Isogeo référence l'application sur sa plateforme et renseigne les URLs de redirection fournies par le développeur.

!["Une application utilisateur déclarée sur Isogeo"](/assets/manage_app_user.png)

Les identifiants sont ensuite transmis au développeur sous la forme d'un fichier *client_secrets.json* dont la structure est la même que celle utilisée par Google ([voir la documentation](https://developers.google.com/api-client-library/python/guide/aaa_client_secrets)) :

```json
{
  "installed": {
    "client_id": "837647042410-75ifg...usercontent.com",
    "client_secret":"asdlkfjaskd",
    "redirect_uris": ["http://localhost", "urn:ietf:wg:oauth:2.0:oob"],
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://accounts.google.com/o/oauth2/token"
  }
}
```

Noter le nom du dictionnaire `installed`, qui marque la différence avec les applications utilsiateur de type public.

## Authorization Code Grant {#userapp-flow}

La documentation officielle de ce flot est disponible [dans la RFC 6749](http://tools.ietf.org/html/rfc6749#section-4.1).

!["oAuth2 - Schéma Authorization Code Grant"](/assets/oAuth_AuthorizationCodeGrant_FR.png)

### Requête d’autorisation

La récupération du code d’autorisation se fait via un navigateur \(le navigateur en cours d’utilisation dans le cas d’une application web, un navigateur externe ou un navigateur embarqué dans le cas d’une application native\). Le client doit être redirigé sur la route d’autorisation[https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize):

* la requête est un GET vers[https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize)

* avec des paramètres qui indiquent :

  * response\_type:code
  * client\_id: l’identifiant OAuth de l’application.
  * redirect\_uri: l’adresse de l’application vers laquelle renvoyer le code d’autorisation \(préalablement enregistrée dans ses paramètres, par exemple  [https://app.isogeo.com/login/callback](https://app.isogeo.com/login/callback)\).

En cas de succès le navigateur est redirigé vers la route de l’application spécifiée ci-dessus, avec les paramètres :

* code: le code d’autorisation.

### Demande du jeton

Muni du code d’autorisation précédent, la récupération d’unaccess tokense fait sur la route[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token). Donc :

* la requête est un POST vers[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token)


* avec un contenu qui contient les paramètres :
  * grant\_type:authorization\_code
  * code: le code d’autorisation.
  * redirect\_uri: la même adresse que pour la requête d’autorisation.


* avec  [un en-tête d’authentification de typeBasic](http://tools.ietf.org/html/rfc2617#section-2), où l’on considère que le nom d’utilisateur à encoder est leclient\_idet le mot de passe à encoder est leclient\_secret\(ce qui revient à encoder en[Base 64](https://en.wikipedia.org/wiki/Base64)la chaîne{client\_id}:{client\_secret}, sans les accolades\). Exemple :  
  Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW

L’access tokenest renvoyé au format JSON. Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure. Un refresh token est également fourni.

