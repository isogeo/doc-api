# Applications utilisateur "publiques" - Authentification {#userapp-authentication}

## Paramètres d'accès {#userapp-confidential-access}

L'équipe Isogeo référence l'application sur sa plateforme et renseigne les URLs de redirection fournies par le développeur.

!["Une application utilisateur déclarée sur Isogeo"](/assets/manage_app_user_public.png)

Les identifiants sont ensuite transmis au développeur sous la forme d'un fichier *client_secrets.json* dont la structure est la même que celle utilisée par Google ([voir la documentation](https://developers.google.com/api-client-library/python/guide/aaa_client_secrets)) :

```json
{
  "web": {
    "client_id": "asdfjasdljfasdkjf",
    "client_secret": "1912308409123890",
    "redirect_uris": ["https://www.example.com/oauth2callback"],
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://accounts.google.com/o/oauth2/token"
  }
}
```

Noter le nom du dictionnaire `web`, qui marque la différence avec les applications utilsiateur de type confidentiel.

## Implicit Grant {#userapp-public-flow}

La documentation officielle de ce flot est disponible [dans la RFC 6749](https://tools.ietf.org/html/rfc6749#section-4.2).

La récupération d’un *access_token* se fait via un navigateur \(le navigateur en cours d’utilisation dans le cas d’une application web, un navigateur externe ou un navigateur embarqué dans le cas d’une application native\). Le client doit être redirigé sur la route d’autorisation [https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize):

* la requête est un GET vers [https://id.api.isogeo.com/oauth/authorize](https://id.api.isogeo.com/oauth/authorize)

* avec des paramètres qui indiquent :

  * `response_type` : token
  * `client_id` : l’identifiant OAuth de l’application.
  * `redirect_uri` : l’adresse de l’application vers laquelle renvoyer le code d’autorisation \(préalablement enregistrée dans ses paramètres, par exemple [https://app.isogeo.com/login/callback](https://app.isogeo.com/login/callback)\).

En cas de succès le navigateur est redirigé vers la route de l’application spécifiée ci-dessus, avec les paramètres ajoutés en [fragment](https://en.wikipedia.org/wiki/Fragment_identifier) :

* `access_token` : le jeton d’accès
* `token_type` : *bearer*
* `expires_in` : la durée de validité du jeton, en secondes
