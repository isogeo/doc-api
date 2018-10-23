# Applications de groupe

## Caractéristiques {#groupapp-properties}

Une application de groupe possède :

* un nom
* une URL de description
* une paire d'identifiants client

Elle peut être associée à 0, n groupes de travail qui peuvent ainsi lui partager 0, n catalogues.

Une application de groupe accède en lecture seule à l’ensemble des fiches contenues dans l’ensemble des catalogues qui lui sont partagés. En revanche elle n’a pas directement accès à ces catalogues.

Une application de groupe utilise le flot [_Client Credentials Grant_](https://tools.ietf.org/html/rfc6749#section-4.4) pour s’authentifier à la plateforme Isogeo.

## Client Credentials Grant {#groupapp_flow}

La documentation officielle de ce flot est disponible dans [la RFC 6749](https://tools.ietf.org/html/rfc6749#section-4.4). Pour paraphraser, la récupération d’un _access token_ se fait sur la route [https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token). Donc :

* la requête est un POST vers [https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials)

* avec un contenu qui indique `grant_type=client_credentials`

* avec [un en-tête d’authentification de typeBasic](http://tools.ietf.org/html/rfc2617#section-2), où l’on considère que le nom d’utilisateur à encoder est le *client_id* et le mot de passe à encoder est le *client_secret* (ce qui revient à encoder en[Base 64](https://en.wikipedia.org/wiki/Base64) la chaîne `{*client_id*}:{*client_secret*}`, sans les accolades). Exemple :

  `Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW`

L’_access token_ est renvoyé au format JSON (voir exemple ci-dessous). Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure.

### Exemple d'access token renvoyé {#grouapp_sample_accessToken}

```json
{
  "access_token": "LoremipsumdolorsitametconsecteturadipiscingelitDonecmaurismaurisvariusacdictumvelviverrainvelitProinidvenenatisipsumutlaciniajustoFusceidexeratDuisutlectusinelitvehiculaconsequatvitaeacnullaDonecnibhnibhtristiqueatenimaliquamcursusultricesvelitQuisquepulvinarurnaveldictumefficiturvelitliberomollisduinecpulvinarliguladoloratquamSedtinciduntnequesitametvolutpat",
  "token_type": "bearer",
  "expires_in": 3599
}
```