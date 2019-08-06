# Ressources, entités et sous-entités

## Ressource \(_resource_\)

Ressource =



## Entités et sous-entités

### Sous-entités

Certaines entités possèdent beaucoup d’informations, regroupées dans des sous-entités. Afin d’optimiser l’usage de notre plateforme, l’API ne renvoie par défaut qu’une partie de ces sous-entités. Afin d’accéder à plus d’informations :

* il est possible de les demander en ajoutant le paramètre\_includesur les routes de l’API qui concernent l’entité principale \(conseillé\).

* il est possible de les demander via un appel spécifique lorsqu’une route dédiée existe.

  


Par exemple pour récupérer une ressource ainsi que ses liens il est possible d’appeler :

* la route principale avec le paramètre\_include:/resources/{:rid}?\_include=links

* la route principale/resources/{:rid}puis la route dédiée/resources/{:rid}/links.

  


Ce paramètre est également valable pour la recherche.

  


Les valeurs possibles pour ce paramètre dépendent de l’entité en question :

* les valeurs invalides sont ignorées par l’API \(\_include=toto\).

* il est donc également possible de demander une sous-entité qui n’existe pas sur l’entité en question \(\_include=layerssur une donnée, par exemple\).

### Entités



### Sous-entités







