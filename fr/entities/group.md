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

## Sous-ressources {#include_subresources}

{% include "./subresources/group.md" %}

### Exemple

```bash
# obtenir un groupe avec tous ses détails
GET /groups/{GROUP_UUID}/?_include=abilities,limits
# lister les contacts auxquels accède un groupe
GET /groups/{GROUP_UUID}/contacts
```
