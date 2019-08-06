# Groupes

Les groupes, communément nommés groupes de travail ou *workgroups*, sont les entités dans lesquelles sont créées les [métadonnées](/metadata.md). Une métadonnée appartenant forcément à un seul groupe.

D'autres éléments appartiennent à un groupe :

- les catalogues créés par les administrateurs du groupe
- les [contacts](contact.md) créés par les administrateurs du groupe
- les partages créés par les administrateurs du groupe
- les licences créées par les administrateurs du groupe
- les spécifications créées par les administrateurs du groupe

Un groupe peut avoir 0-n utilisateurs membres selon 3 niveaux de gestion :

- lecteur
- éditeur
- administrateur

## Sous-ressources

| Sous-ressource     | Description                                                                 | Par défaut | Mode |
| :----------------- | :-------------------------------------------------------------------------- | :--------: | ----: |
| _abilities         | Les droits de l’utilisateur courant sur le groupe                           | NON        | ?_include=_abilities |
| catalogs           | Les catalogues du groupe                                                    | NON        | /memberships |
| contact            | Les informations de contact du groupe (celles du tableau de bord dans APP)  | **OUI**    | ?_include=contact |
| contacts           | Les contacts auxquels les éditeurs du groupe accèdent                       | NON        | /contacts |
| coordinate-systems | Les systèmes de coordonnées sélectionnées par les administrateurs           | NON        | /memberships |
| invitations        | Les invitations du groupe                                                   | NON        | /invitations |
| limits             | Les limites Isogeo du groupe.                                               | NON        | ?_include=limits |
| memberships        | Les utilisateurs membres du groupe                                          | NON        | /memberships |
| shares             | Les partages du groupe                                                      | NON        | /shares |
| specifications     | Les spécifications du groupe                                                | NON        | /specifications  |
| statistics         | Les statistiques du groupe (celles du tableau de bord dans APP)             | NON        | /statistics |

### Exemple

```bash
# obtenir un groupe avec tous ses détails
GET /groups/{GROUP_UUID}/?_include=abilities,limits
# lister les contacts auxquels accède un groupe
GET /groups/{GROUP_UUID}/contacts
```
