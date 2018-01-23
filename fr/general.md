# Généralités

L’API Isogeo est une API REST qui donne accès à des **entités** via des **routes**. Lorsqu’on souhaite accéder à une entité en particulier il faut appeler la route correspondante, qui contient l’identifiant de l’entité en question.

## Principales routes

| Verbe HTTP | URI | Description |
| :--- | :--- | :--- |
| GET | /resources/search | Moteur de recherche des métadonnées |
| GET | /resources/{:rid} | Métadonnée détaillée |
| GET | /resources/{:rid}.xml | Téléchargement de la métadonnée au format XML ISO 19139 |
| GET | /shares/{:rid} | Caractéristiques des partages alimentant l'application de groupe |

## Principales entités

### Métadonnée \(_resource_\)

C'est l'entité au coeur de l'API Isogeo et de son modèle métier.

### Partage \(_shares_\)

Les applications de groupe \(voir [la rubrique dédiée](/authentication/groupsapps.md)\) sont alimentées par :

* 0 - n partages,
* créés par 0 - n groupes de travail

### Groupe de travail \(workgroup\)

Un groupe de travail est l'entité correspondant à . On parle aussi de _propriétaire \(owner\)_, car certaines entités appartiennent à un groupe de travail.

---

## Entités et sous-entités

### 



