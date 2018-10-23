# Concepts

## Différents types d'applications

La plateforme Isogeo distingue 2 types d’applications :

* les [applications utilisateur](/authentication/usersapps.md) :
  * elles accèdent aux ressources de la plateforme au nom d’un utilisateur, qui doit donc être personnellement authentifié.
  * elles accèdent uniquement aux ressources auquel l’utilisateur a droit : pas d’utilisateur, pas de ressources.
  * exemple d'application : [Isogeo App](https://app.isogeo.com)


* les [applications de groupe](/authentication/groupsapps.md) :
  * elles accèdent aux ressources de la plateforme en leur propre nom, sans notion d’utilisateur.
  * elles accèdent uniquement aux ressources qui leur ont été partagées par l'administrateur d'un ou plusieurs groupes de travail, via l'application Isogeo APP.
  * exemples d'application : [OpenCatalog](https://open.isogeo.com), les plugins pour SIG, Isogeo to Office

Toute application, développée par Isogeo ou un tiers, s'authentifie à la plateforme Isogeo via  [le protocole OAuth 2.0](https://tools.ietf.org/html/rfc6749). La documentation officielle de OAuth 2.0 fait donc référence pour l’authentification Isogeo.

Chaque type d’application, en fonction de ses caractéristiques peut utiliser un certain nombre de flots OAuth \(ou _grants_\). Les applications sont préalablement déclarées sur la plateforme par l'équipe Isogeo. Elle fournit alors les identifiants d’application sous forme d'[un fichier client_secrets.json dont la structure, différente selon le type de l'application, est la même que celle utilisée par Google](https://developers.google.com/api-client-library/python/guide/aaa_client_secrets).


---

## Généralités

Le but de l’authentification est de récupérer un jeton d’accès à l’API, l'*access token*.

La récupération de ce jeton dépend du type d’application et de ses caractéristiques, mais est conforme au standard OAuth 2.0. Pour simplifier, fiabiliser et pérenniser le processus d’authentification il est donc fortement conseillé d’utiliser[des bibliothèques standard d’authentification OAuth 2.0](http://oauth.net/2/#client-libraries). Par exemple :

* Javascript :  [oauth](https://www.npmjs.com/package/oauth).
* .NET :  [Microsoft.Owin.Security.OAuth](https://www.nuget.org/packages/Microsoft.Owin.Security.OAuth).

L’*access token* ainsi récupéré permet d’accéder aux ressources fournies par l’API via  [un en-tête d’authentification de type Bearer](https://tools.ietf.org/html/rfc6750#section-2). Exemple :  `Authorization: Bearer mF_9.B5f-4.1JqM`.

La plupart des méthodes d’authentification disponibles nécessitent le transfert des identifiants de votre application : ces identifiants sont l’équivalent d’un couple login / mot de passe et ils ne doivent donc jamais être visibles par les utilisateurs de votre application \(dans le code source javascript d’une application web par exemple\). Les méthodes courantes pour l’éviter sont :

* l’utilisation d’un proxy \(applications web\).
* modifier les caractéristiques de l’application pour éviter d’avoir à transmettre ces identifiants \(application utilisateur publique\).
