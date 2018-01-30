# Applications de groupe

## Caractéristiques {#groupapp-properties}

Une application de groupe possède :

* un nom
* une paire d'identifiants client : un ID et un SECRET

Elle peut être associée à 0, n groupes de travail qui peuvent ainsi lui partager 0, n catalogues.

Une application de groupe accède en lecture seule à l’ensemble des fiches contenues dans l’ensemble des catalogues qui lui sont partagés. En revanche elle n’a pas directement accès à ces catalogues : la notion même de catalogue n’a pas de sens pour une application de groupe.

Une application de groupe utilise le flot [Client Credentials Grant](http://tools.ietf.org/html/rfc6749#section-4.4) pour s’authentifier à la plateforme Isogeo.

## Client Credentials Grant

La documentation officielle de ce flot est disponible [dans la RFC 6749](http://tools.ietf.org/html/rfc6749#section-4.4).

Pour paraphraser, la récupération d’un _access token_ se fait sur la route[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token). Donc :

* la requête est un POST vers[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials)

* avec un contenu qui indique  
  grant\_type=client\_credentials

* avec [un en-tête d’authentification de typeBasic](http://tools.ietf.org/html/rfc2617#section-2), où l’on considère que le nom d’utilisateur à encoder est leclient\_idet le mot de passe à encoder est leclient\_secret\(ce qui revient à encoder en[Base 64](https://en.wikipedia.org/wiki/Base64)la chaîne{client\_id}:{client\_secret}, sans les accolades\). Exemple :  
  Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW

L’_access token_ est renvoyé au format JSON. Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure. Un _refresh token_ est également fourni.

### Refresh Token

La documentation officielle de l’utilisation d’un _refresh token_ est disponible [dans la RFC 6749](http://tools.ietf.org/html/rfc6749#section-6).

Pour paraphraser, le renouvellement d’unaccess tokense fait sur la route[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token). Donc :

* la requête est un POST vers[https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials)

* avec un contenu qui indique :

  * grant\_type:refresh\_token

  * refresh\_token: le refresh token précédemment récupéré

* avec [un en-tête d’authentification de typeBasic](http://tools.ietf.org/html/rfc2617#section-2), où l’on considère que le nom d’utilisateur à encoder est leclient\_idet le mot de passe à encoder est leclient\_secret\(ce qui revient à encoder en [Base 64](https://en.wikipedia.org/wiki/Base64) la chaîne{client\_id}:{client\_secret}, sans les accolades\). Exemple : `Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW`



