# Contacts

3 types possibles :

- `custom`: contacts créés au sein d'un groupe de travail
- `group`: coordonnées d'un groupe de travail
- `user`: coordonnées d'un utilisateur

## GET

| Verbe HTTP | URI                            | Description                           |
| :---       | :----------------------------- | :------------------------------------ |
| GET        | /contacts/{contact_uuid}       | Obtenir un contact en particulier     |
| GET        | /groups/{group_uuid}/contacts  | Liste les contacts qu'un éditeur du groupe peut utiliser pour documenter (carnet d'adresses du groupe + groupes ayant partagé leurs coordonnées)    |
