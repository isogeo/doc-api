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
