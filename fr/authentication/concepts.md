# Concepts

## Les différents types d'applications

La plateforme Isogeo distingue 2 types d’applications :

* les applications utilisateur :
  - elles accèdent aux ressources de la plateforme au nom d’un utilisateur, qui doit donc être personnellement authentifié.
  - elles accèdent uniquement aux ressources auquel l’utilisateur a droit : pas d’utilisateur, pas de ressources.
  - exemple d'application : [Isogeo App](https://app.isogeo.com)


* les applications de groupe :
  - elles accèdent aux ressources de la plateforme en leur propre nom, sans notion d’utilisateur.
  - elles accèdent uniquement aux ressources qui leur ont été partagées par l'administrateur d'un ou plusieurs groupes de travail, via l'application Isogeo APP.
  - exemple d'application : [OpenCatalog](https://open.isogeo.com)

Toute application, dveloppée par Isogeo ou un tiers, s'authentifie à la plateforme Isogeo via  [le protocole OAuth 2.0](http://tools.ietf.org/html/rfc6749). La documentation officielle de OAuth 2.0 fait donc référence pour l’authentification Isogeo ([RFC 6749](http://tools.ietf.org/html/rfc6749)).

Chaque type d’application, en fonction de ses caractéristiques peut utiliser un certain nombre de flots OAuth (ou _grants_). Les applications sont préalablement déclarées sur la plateforme Isogeo par l'équipe Isogeo  qui fournit alors les identifiants d’application :
* _client_id_
* et _client_secret_.

## Généralités

Le but de l’authentification est de récupérer un jeton d’accès à l’API \(access token\).


La récupération de ce jeton dépend du type d’application et de ses caractéristiques, mais est conforme au standard OAuth 2.0. Pour simplifier, fiabiliser et pérenniser le processus d’authentification il est donc fortement conseillé d’utiliser[des bibliothèques standard d’authentification OAuth 2.0](http://oauth.net/2/#client-libraries). Par exemple :

* Javascript :  [oauth](https://www.npmjs.com/package/oauth).
* .NET :  [Microsoft.Owin.Security.OAuth](https://www.nuget.org/packages/Microsoft.Owin.Security.OAuth).

L’access tokenainsi récupéré permet d’accéder aux ressources fournies par l’API via[un en-tête d’authentification de type Bearer](http://tools.ietf.org/html/rfc6750#section-2). Exemple :  `Authorization: Bearer mF\_9.B5f-4.1JqM`.

La plupart des méthodes d’authentification disponibles nécessitent le transfert des identifiants de votre application : ces identifiants sont l’équivalent d’un couple login / mot de passe et ils ne doivent doncjamaisêtre visibles par les utilisateurs de votre application \(dans le code source javascript d’une application web par exemple\). Les méthodes courantes pour l’éviter sont :

* l’utilisation d’un proxy \(pour les applications web, donc\).

* modifier les caractéristiques de l’application pour éviter d’avoir à transmettre ces identifiants \(application utilisateur publique, cf. ci-dessous\).

  


Dans certains cas un refresh token
est fourni avec l

’

access token

. Ce jeton peut être utilisé afin de renouveler simplement l

’

access token

. Il doit donc être protégé, de la même manière que les identifiants d

’

application.

## Le refresh token

La documentation officielle de l’utilisation d’unrefresh tokenest disponible [dans la RFC 6749](http://tools.ietf.org/html/rfc6749#section-6).

Pour paraphraser, le renouvellement d’un _access token_ se fait sur la routehttps://id.api.isogeo.com/oauth/token. Donc :

* la requête est un POST vers https://id.api.isogeo.com/oauth/token](https://id.api.isogeo.com/oauth/token?grant_type=client_credentials)

* avec un contenu qui indique :

  * `grant_type:refresh_token`
  * `refresh_token: {token_récupéré_précédemment}`

* avec [un en-tête d’authentification de typeBasic](http://tools.ietf.org/html/rfc2617#section-2), où l’on considère que le nom d’utilisateur à encoder est leclient\_idet le mot de passe à encoder est leclient\_secret\(ce qui revient à encoder en[Base 64](https://en.wikipedia.org/wiki/Base64)la chaîne{client\_id}:{client\_secret}, sans les accolades\). Exemple :  
  Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW

  
L’access token est renvoyé au format JSON. Il permet l’accès aux ressources d’Isogeo en lecture seule et est valide pendant 1 heure.

Un refresh token est également fourni.



