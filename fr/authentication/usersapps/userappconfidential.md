# Applications utilisateur "confidentielles" - Authentification {#userapp-authentication}

## Paramètres d'accès {#userapp-confidential-access}

L'équipe Isogeo référence l'application sur sa plateforme et renseigne les URLs de redirection fournies par le développeur.

!["Une application utilisateur déclarée sur Isogeo"](/assets/manage_app_user_confidential.png)

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

## Authorization Code Grant {#userapp-confidential-flow}

La documentation officielle de ce flot est disponible [dans la RFC 6749](https://tools.ietf.org/html/rfc6749#section-4.1). Ce flot se fait en 2 étapes :

1. la requête d'autorisation :
    1. un formulaire web (encapsulé ou non) demande à l'utilisateur final son identifiant/mot de passe Isogeo.
    2. un code d'autorisation est renvoyé
2. l'obtention du jeton d'accès (*access token*)

Puis, le rafraîchissement du jeton d'accès (*access token*) en utilisant le jeton de rafraichissement (*refresh token*).

!["oAuth2 - Schéma Authorization Code Grant"](/assets/oAuth_AuthorizationCodeGrant_FR.png)

### Requête d’autorisation {#userapp_confidential_auth}

La récupération du code d’autorisation se fait via un navigateur \(le navigateur en cours d’utilisation dans le cas d’une application web, un navigateur externe ou un navigateur embarqué dans le cas d’une application native\). L'utilisateur doit être redirigé sur la route d’autorisation [https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize):

* la requête est un GET vers <https://id.api.isogeo.com/oauth/authorize>

* avec des paramètres qui indiquent :

  * `response_type`: code
  * `client_id` : l’identifiant OAuth de l’application.
  * `redirect_uri` : l’adresse de l’application vers laquelle renvoyer le code d’autorisation (préalablement enregistrée dans ses paramètres, par exemple  <https://localhost:5000/login/callback).>

La requête est automatiquement redirigée - [HTTP 302 Found](https://developer.mozilla.org/fr/docs/Web/HTTP/Status/302) vers le formulaire d'authentification intégré à Isogeo (https://id.api.isogeo.com/login) avec un paramètre de retour d'URL correspondant à la requête intiale. C'est l'étape à laquelle l'utilisateur final doit entrer son identifiant/mot de passe Isogeo :

![Formulaire d&apos;authentification Isogeo](/assets/api_id_auth_login_form.png)

#### Exemples {#userapp_confidential_auth_examples}

##### Navigateur

L'URL peut être ouverte directement dans un navigateur :

```http
https://id.api.isogeo.com/oauth/authorize?response_type=code&client_id=sample-3rdapp-demo-test-uuid-1a2b3c4d5e6f7g8h9i0j11k12l&http://localhost:5000/login/oauth/callback
```

Qui redirige donc vers :

```http
https://id.api.isogeo.com/login?ReturnUrl=https%3A%2F%2Fid.api.isogeo.com%2Foauth%2Fauthorize%3Fresponse_type%3Dcode%26client_id%3Dclient_id=sample-3rdapp-demo-test-uuid-1a2b3c4d5e6f7g8h9i0j11k12l%26http%3A%2F%2Flocalhost%3A5000%2Flogin%2Foauth%2Fcallback
```

En cas de succès le navigateur est redirigé vers l'URI de retour (*callback*) enrgeistrée sur la plateforme, avec en paramètre le code d’autorisation (`code`) en paramètre d'URL :

```http
http://localhost:5000/login/oauth/callback?code=%2B7CNjbPnhNbRgieXBS3YDKF%2BtmWLpSQWyQoQd%2Fy3yA6maBTV1cVTtNlyhG7gRvwIlQLlF15hv4dFb8kX%2FMlClU%2B%2FNTZuTRRDCWcop1p8ZF%2BR%2BQ8KbvKNkW%2FSNKWGz43H
```

### Demande du jeton {#userapp_confidential_access}

Muni du code d’autorisation précédent, la récupération d’un *access token* se fait sur la route <https://id.api.isogeo.com/oauth/token.> Donc :

* la requête est un POST vers <https://id.api.isogeo.com/oauth/token> avec :

  * un contenu qui contient les paramètres :

    * `grant_type` : *authorization_code*
    * `code` : le code d’autorisation
    * `redirect_uri` : la même adresse que pour la requête d’autorisation.

  * [un en-tête d’authentification de type Basic](https://tools.ietf.org/html/rfc2617#section-2), où l’on considère que :

    * le nom d’utilisateur est le *client_id*
    * le mot de passe est le *client_secret*

    Ce qui revient à encoder en [Base 64](https://en.wikipedia.org/wiki/Base64) la chaîne `{client_id}:{client_secret}` \(sans les accolades\). Exemple :

    `Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW`

L’*access_token* est renvoyé au format JSON. Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure. Un refresh token est également fourni.

### Le refresh token {#userapp_confidential_refresh}

un *refresh token* est fourni avec l’*access token*. Ce jeton peut être utilisé afin de renouveler simplement l’*access token*. Il doit donc être protégé, de la même manière que les identifiants d’application.

La documentation officielle de l’utilisation d’un *refresh token* est disponible [dans la RFC 6749](https://tools.ietf.org/html/rfc6749#section-6).

Dans le cas d'Isogeo, le renouvellement d’un _access token_ se fait sur la route [https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token). La requête est un **POST** vers [https://id.api.isogeo.com/oauth/token?grant\_type=client\_credentials](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials), avec :

* un contenu qui indique :

  * `grant_type` : *refresh_token*
  * `refresh_token` : *{le token_récupéré_précédemment}*

* avec [un en-tête d’authentification de typeBasic](https://tools.ietf.org/html/rfc2617#section-2), où l’on considère que :

  * le nom d’utilisateur est le *client_id*
  * le mot de passe est le *client_secret*

  Ce qui revient à encoder en [Base 64](https://en.wikipedia.org/wiki/Base64) la chaîne `{client_id}:{client_secret}` \(sans les accolades\). Exemple :

  `Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW`
