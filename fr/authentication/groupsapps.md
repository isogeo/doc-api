---
description: Isogeo API - Authentification applications de groupe,
keywords: "api,oauth2,client credentials grant,isogeo,auhtentification"
---

# Applications de groupe

## Caractéristiques {#groupapp-properties}

Une application de groupe possède :

* un nom
* une URL de description
* une paire de paramètres d'identification (*client_id* et *client_secret*)

Elle peut être associée à 0, n groupes de travail qui peuvent ainsi lui partager 0, n catalogues.

Une application de groupe accède en lecture seule à l’ensemble des fiches contenues dans l’ensemble des catalogues qui lui sont partagés. En revanche elle n’a pas directement accès à ces catalogues.

Une application de groupe utilise le flot [_Client Credentials Grant_](https://tools.ietf.org/html/rfc6749#section-4.4) pour s’authentifier à la plateforme Isogeo.

## Authentification {#groupapp-authentication}

### Paramètres d'accès {#groupapp-access}

L'équipe Isogeo référence l'application sur sa plateforme et l'affecte au/x groupe/s de travail adéquats.

!["Une application de groupe déclarée sur Isogeo"](/assets/manage_app_group.png)

Les identifiants sont ensuite transmis au développeur sous la forme d'un fichier *client_secrets.json* dont la structure est la même que celle utilisée par Google ([voir la documentation](https://developers.google.com/api-client-library/python/guide/aaa_client_secrets)) :

```json
{
"web": {
    "client_id": "python-minimalist-sdk-test-uuid-1a2b3c4d5e6f7g8h9i0j11k12l",
    "client_secret": "application-secret-1a2b3c4d5e6f7g8h9i0j11k12l13m14n15o16p17Q18rS",
    "auth_uri": "https://id.api.isogeo.com/oauth/authorize",
    "token_uri": "https://id.api.isogeo.com/oauth/token"
    }
}
```

### Client Credentials Grant {#groupapp-flow}

La documentation officielle de ce flot est disponible dans [la RFC 6749](https://tools.ietf.org/html/rfc6749#section-4.4). Pour paraphraser, la récupération d’un _access token_ se fait sur la route [https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token).

La requête est un POST vers [https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials)

* avec un contenu qui indique `grant_type=client_credentials`

* avec [un en-tête d’authentification de type Basic](https://tools.ietf.org/html/rfc2617#section-2), où l’on considère que :

  * le nom d’utilisateur est le *client_id*
  * le mot de passe est le *client_secret*

  Ce qui revient à encoder en [Base 64](https://en.wikipedia.org/wiki/Base64) la chaîne `{client_id}:{client_secret}` \(sans les accolades\). Exemple :

  `Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW`

L’_access token_ est renvoyé au format JSON \(voir exemple ci-dessous\). Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure.

> Voir aussi [le tutoriel du site auth0.com](https://auth0.com/docs/api-auth/tutorials/client-credentials)

### Exemples {#groupapp_auth_examples}

#### Requête

##### cUrl

En utilisant [cURL sur Windows](https://curl.haxx.se/windows/) (Powershell) :

```powershell
.\curl.exe --data "grant_type=client_credentials" <# on passe le type d'authentification en paramètre d'URL #> `
           -u '{client_id}:{client_secret}' <# la chaîne est automatiquement encodée en Base64 par cURL #> `
           --url https://id.api.isogeo.com/oauth/token <# url cible #> `
           -X POST <# superflu mais plus lisible #> `
           --header 'content-type: application/x-www-form-urlencoded'  <# superflu mais plus lisible #> `
           --verbose <# requête détaillée #> `
           --include <# réponse détaillée #>
```

##### Python

Avec le package addditionnel `requests` :

```python
# -*- coding: UTF-8 -*-
import requests

# query string parameters
payload = {"grant_type": "client_credentials"}

# request
rq_auth = requests.post("https://id.api.isogeo.com/oauth/token",
                        auth=(client_id, client_secret),
                        data=payload)

print(rq_auth.json())
```

> Astuce : utiliser [le package officiel Isogeo Python SDK](https://pypi.org/project/isogeo-pysdk/) qui facilite grandement l'utilisation de l'API avec Python.

#### Structure de l'access token renvoyé {#groupapp_auth_example_response}

```json
{
  "access_token": "LoremipsumdolorsitametconsecteturadipiscingelitDonecmaurismaurisvariusacdictumvelviverrainvelitProinidvenenatisipsumutlaciniajustoFusceidexeratDuisutlectusinelitvehiculaconsequatvitaeacnullaDonecnibhnibhtristiqueatenimaliquamcursusultricesvelitQuisquepulvinarurnaveldictumefficiturvelitliberomollisduinecpulvinarliguladoloratquamSedtinciduntnequesitametvolutpat",
  "token_type": "bearer",
  "expires_in": 3599
}
```
