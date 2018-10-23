# Applications utilisateurs

## Caractéristiques {#userapp-properties}

Une application utilisateur possède :

* un nom ;
* des identifiants ;
* des URIs de redirection ;
* un type.

Une application utilisateur accède en lecture seule à l’ensemble des fiches accessibles à l’utilisateur qui se connecte.

## Types d'application utilisateur {#userapp-types}

Une application utilisateur peut être de 2 types, selon le niveau de confidentialité dont elle est capable. Le type est défini par Isogeo lors du référencement de l'application tierce sur la plateforme.

### Applications confidentielles {#userapp-confidential}

Désignent les applications capables de stocker et de transmettre ses identifiants en toute sécurité \(sans les dévoiler à l’utilisateur\). Par exemple \(et typiquement\) une application web, qui stocke les identifiants sur son serveur \(dont l’accès est normalement restreint\) et qui les transmet sans passer par le navigateur.

Une application confidentielle utilise le flot [Authorization Code Grant](https://tools.ietf.org/html/rfc6749#section-4.1) pour permettre à l’utilisateur de s’authentifier à la plateforme Isogeo.

L'interface d'administration d'Isogeo, APP \(https://app.isogeo.com\), est une application confidentielle.

### Applications publiques {#userapp-public}

A l'inverse, ce type désigne les applications incapables de stocker ou de transmettre ses identifiants sans les dévoiler à l’utilisateur. Par exemple une application qui s’exécute entièrement dans le navigateur \(application en javascript en général\) et dont le code source doit être entièrement téléchargé par le client.

Une application publique utilise le flot [Implicit Grant](https://tools.ietf.org/html/rfc6749#section-4.2) pour permettre à l’utilisateur de s’authentifier à la plateforme Isogeo.

### Cas des applications natives {#userapp-natives}

Le niveau de confidentialité à affecter à une application utilisateur native \(application de bureau ou application mobile par exemple\) est un problème non encore résolu dans le monde de OAuth :

* en principe elle doit être publique \(les identifiants devraient être fournis avec l’application qui est téléchargée, donc en pratique visible par tous même si cela requiert parfois des techniques plus ou moins avancées de décompilation\).

* en pratique, elle est parfois confidentielle afin principalement d’améliorer l’expérience utilisateur.

Pour plus d’informations il est possible de se référer à la RFC en cours de rédaction sur la sécurisation des applications natives : [OAuth 2.0 for Native Apps](https://tools.ietf.org/html/draft-ietf-oauth-native-apps-03).

