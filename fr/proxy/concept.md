# Proxy : généralités

Dans le cas d’une application web typiquement, l’utilisation d’un proxy est nécessaire :

* afin d’autoriser et de sécuriser les appels vers l’API Isogeo.
* afin de rendre accessible à l’utilisateur certaines ressources particulières, images ou fichiers, en téléchargement par exemple (fiche de métadonnée ISO 19139, fichiers hébergés sur la plateforme Isogeo…).

## Développement

Toutes les plateformes modernes de développement web offrent des moyen simples de réaliser un proxy, et il est donc conseillé de les utiliser. Par exemple :

* node.js : [node-http-proxy](https://www.npmjs.com/package/node-http-proxy).

Les risques liés au développement d’un proxy sont liés à la confidentialité des données partagées à vos applications : si vous devez vérifier que seule l’application peut faire appel à son proxy ([quelques techniques disponibles ici](https://en.wikipedia.org/wiki/Cross-site_request_forgery#Prevention)).

Dans la mesure du possible, nous serons reconnaissants à nos développeurs si leur proxy nous transmet des informations sur l’origine des requêtes qui sont transmises à l’API ([X-Forwarded-For](https://en.wikipedia.org/wiki/X-Forwarded-For) par exemple).
