# Applications utilisateurs

## Caractéristiques {#userapp-properties}

Une application utilisateur possède :

* un nom ;
* des identifiants ;
* des URIs de redirection ;
* un type.

Une application utilisateur accède en lecture seule à l’ensemble des fiches accessibles à l’utilisateur qui se connecte.

## URIs de redirection {#userapp-uris}

Les flots d’authentification disponibles nécessitent l’utilisation d’un navigateur \(potentiellement embarqué pour une application de bureau\) et se basent sur un principe de redirections \([HTTP 302](https://en.wikipedia.org/wiki/HTTP_302)\) pour fournir un code d’autorisation à l’application. Dans un souci de sécurité il est donc nécessaire d’enregistrer préalablement la ou les URIs de redirection qui correspondent au\(x\) domaine\(s\) de votre application. Les URIs enregistrées doivent correspondre exactement aux routes acceptées par votre application.

Dans le cas d’un développement étalé sur plusieurs plateformes \(par exemple développement, intégration, pré production, production\), il est conseillé d’enregistrer les URLs spécifiques de chaque plateforme \(dans la même application\).

Dans le cas d’une application native \(application de bureau, ou mobile par exemple\) ce mécanisme de redirections nécessite l’appel à un navigateur externe \(Internet Explorer, Firefox, Chrome…\) ou à un navigateur embarqué. La récupération du code d’autorisation peut alors se faire :

* via une redirection vers un serveur local instancié par l’application sur un port dédié \([http://localhost:9873](http://localhost:9873)par exemple\). Cette méthode est parfaitement valide, mais peut s’avérer lourde à l’usage.

* via l’utilisation d’URIs prédéfinies qui fournissent ce code au navigateur et qui permettent à une application qui maîtrise le navigateur qu’elle a créé de récupérer ce code directement dans le navigateur :

* * assez simple en général dans le cas d’un navigateur embarqué.

  * potentiellement plus complexe dans le cas d’un navigateur externe \(sous Windows utilisation des APIs Win32[ ShellExecute](https://msdn.microsoft.com/en-us/library/windows/desktop/bb762153.aspx) ou [ShellExecuteEx](https://msdn.microsoft.com/en-us/library/windows/desktop/bb762154.aspx) par exemple\).

Les URIs prédéfinies \(qui doivent quand même être enregistrées application par application\) sont :

* urn:ietf:wg:oauth:2.0:oob: affiche une page qui permet à l’utilisateur de copier/coller le code d’autorisation depuis le navigateur vers l’application.

* urn:ietf:wg:oauth:2.0:oob:auto: renseigne le code d’autorisation dans le titre de la page, ce qui permet à une application intelligente de le récupérer automatiquement avant de fermer \(automatiquement si possible\) la fenêtre du navigateur.

Ce système est identique à celui utilisé par Google.

---

## Types d'application utilisateur

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

.

