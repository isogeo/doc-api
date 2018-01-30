# URIs de redirection

Les flots d’authentification disponibles nécessitent l’utilisation d’un navigateur \(potentiellement embarqué pour une application de bureau\) et se basent sur un principe de redirections \([HTTP 302](https://en.wikipedia.org/wiki/HTTP_302)\) pour fournir un code d’autorisation à l’application. Dans un souci de sécurité il est donc nécessaire d’enregistrer préalablement la ou les URIs de redirection qui correspondent au\(x\) domaine\(s\) de votre application. Les URIs enregistrées doivent correspondre exactement aux routes acceptées par votre application.

Dans le cas d’un développement étalé sur plusieurs plateformes \(par exemple développement, intégration, pré production, production\), il est conseillé d’enregistrer les URLs spécifiques de chaque plateforme dans la même application.

Dans le cas d’une application native \(application de bureau, ou mobile par exemple\) ce mécanisme de redirections nécessite l’appel à un navigateur externe \(Internet Explorer, Firefox, Chrome…\) ou à un navigateur embarqué. La récupération du code d’autorisation peut alors se faire :

* via une redirection vers un serveur local instancié par l’application sur un port dédié \([http://localhost:9873](http://localhost:9873)par exemple\). Cette méthode est parfaitement valide, mais peut s’avérer lourde à l’usage.

* via l’utilisation d’URIs prédéfinies qui fournissent ce code au navigateur et qui permettent à une application qui maîtrise le navigateur qu’elle a créé de récupérer ce code directement dans le navigateur :

* * assez simple en général dans le cas d’un navigateur embarqué.

  * potentiellement plus complexe dans le cas d’un navigateur externe \(sous Windows utilisation des APIs Win32[ ShellExecute](https://msdn.microsoft.com/en-us/library/windows/desktop/bb762153.aspx) ou [ShellExecuteEx](https://msdn.microsoft.com/en-us/library/windows/desktop/bb762154.aspx) par exemple\).

Les URIs prédéfinies \(qui doivent quand même être enregistrées application par application\) sont :

* `urn:ietf:wg:oauth:2.0:oob:` affiche une page qui permet à l’utilisateur de copier/coller le code d’autorisation depuis le navigateur vers l’application.

* `urn:ietf:wg:oauth:2.0:oob:auto:` renseigne le code d’autorisation dans le titre de la page, ce qui permet à une application intelligente de le récupérer automatiquement avant de fermer \(automatiquement si possible\) la fenêtre du navigateur.

Ce système est identique à celui utilisé par Google.

