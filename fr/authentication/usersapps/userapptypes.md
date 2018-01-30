# Types d'application utilisateur

Une application utilisateur peut être de 2 types :

* confidentielle: une application qui est capable de stocker et de transmettre ses identifiants en toute sécurité \(sans les dévoiler à l’utilisateur\).

* * par exemple \(et typiquement\) une application web, qui stocke les identifiants sur son serveur \(dont l’accès est normalement restreint\) et qui les transmet sans passer par le navigateur.

  * une applicationconfidentielleutilise le flot[Authorization Code Grant](https://tools.ietf.org/html/rfc6749#section-4.1)pour permettre à l’utilisateur de s’authentifier à la plateforme Isogeo.
* publique: une application qui est incapable de stocker ou de transmettre ses identifiants sans les dévoiler à l’utilisateur.

* * par exemple une application qui s’exécute entièrement dans le navigateur \(application en javascript en général\) et dont le code source doit être entièrement téléchargé par le client.

  * une applicationpubliqueutilise le flot[Implicit Grant](https://tools.ietf.org/html/rfc6749#section-4.2)pour permettre à l’utilisateur de s’authentifier à la plateforme Isogeo.

Le niveau de confidentialité à affecter à une application utilisateur native \(application de bureau ou application mobile par exemple\) est un problème non encore résolu dans le monde de OAuth :

* en principe elle doit êtrepublique\(les identifiants devraient être fournis avec l’application qui est téléchargée, donc en pratique visible par tous même si cela requiert parfois des techniques plus ou moins avancées de décompilation\).

* en pratique est parfoisconfidentielleafin principalement d’améliorer l’expérience utilisateur.

Pour plus d’informations il est possible de se référer à la RFC en cours de rédaction sur la sécurisation des applications natives : [OAuth 2.0 for Native Apps](https://tools.ietf.org/html/draft-ietf-oauth-native-apps-03).

