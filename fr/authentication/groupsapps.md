# Applications de groupe

## Caractéristiques {#groupapp-properties}

Une application de groupe possède :

* un nom.

* des identifiants.

Elle peut être associée à 0, n groupes de travail qui peuvent ainsi lui partager des catalogues.

Une application de groupe accède en lecture seule à l’ensemble des fiches contenues dans l’ensemble des catalogues qui lui sont partagés. En revanche elle n’a pas directement accès à ces catalogues : la notion même de catalogue n’a pas de sens pour une application de groupe.

Une application de groupe utilise le flot [Client Credentials Grant](http://tools.ietf.org/html/rfc6749#section-4.4) pour s’authentifier à la plateforme Isogeo.



