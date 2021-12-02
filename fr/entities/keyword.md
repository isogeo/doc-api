# Mots-clés

## Thesauri

Les mots-clés sont répartis par thésaurus, au nombre de trois à l'heure actuelle :

- Thèmes Inspire (_inspire-theme_) ;
- Thématiques (_group-theme_) ;
- Mots-clés (_isogeo_).

| Verbe HTTP | URI                                               | Description                                      |
| :--------- | :------------------------------------------------ | :----------------------------------------------- |
| GET        | /thesauri                                         | Retourne la liste des thésauri existants         |
| GET        | /thesauri/{thesauri_uuid}                         | Retourne un thésaurus                            |
| GET        | /thesauri/{thesauri_uuid}/keywords/search         | Cherche des mots-clés dans le thésaurus spécifié |
| GET        | /thesauri/{thesauri_uuid}/keywords/{keyword_uuid} | Retourne un mot-clé dans le thésaurus spécifié   |

## Thèmes Inspire, thématiques et mots-clés

### Sous-ressources

| Sous-ressource | Description                                                                         | Par défaut | Mode                 |
| :--------------| :---------------------------------------------------------------------------------- | :--------: | -------------------: |
| _abilities     | Les droits de l’utilisateur courant sur le mot-clé                                  | NON        | ?_include=_abilities |
| code           | Code du mot-clé tel qu'il est rédigé lors de la recherche (sans accents ni espaces) | **OUI**    |                      |
| text           | Texte associé au mot-clé tel qu'il est affiché dans les applications                | **OUI**    |                      |
| count          | Nombre d'occurrences du mot-clé dans le groupe ou dans Isogeo                       | NON        | ?_include=count      |
| thesaurus      | Thésaurus du mot-clé                                                                | NON        | ?_include=thesaurus  |

### Requêtes

| Verbe HTTP | URI                                                | Description                                              |
| :--------- | :------------------------------------------------- | :------------------------------------------------------- |
| GET        | /keywords/{keyword_uuid}                           | Retourne un mot-clé                                      |
| GET        | /groups/{group_uuid}/keywords/search               | Cherche des mots-clés dans le groupe de travail          |
| GET        | /resources/{resource_uuid}/keywords                | Retourne la liste des mots-clés associés à une ressource |
| POST       | /resources/{resource_uuid}/keywords/{keyword_uuid} | Associe un mot-clé existant à une ressource              |
| DELETE     | /resources/{resource_uuid}/keywords/{keyword_uuid} | Supprime l'association entre un mot-clé et une ressource |
