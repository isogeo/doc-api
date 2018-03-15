# Filtrer sur une liste de métadonnées spécifiques

Il est possible de limiter la recherche à une liste de métadonnées en particulier. Utilisé pour implémenter un système de liste de données favorites pour l'utilisateur final.

## Longueur de la liste des résultats {#_id}

> Paramètre : **\_id**

### Description

Limites la rechercher à la liste des identifiants de métadonnées spécifiés.

### Valeurs possibles

Une liste d'identifiants séparés par des virgules.

### Exemples

```js
/resources/search?q=type:dataset&_id=b46f086ec6b24f25ae2aca61c1fc80a2,14bc943cddd749e38047381dcc9e4bcd    # les métadonnées de données parmi les 3 passées en paramètre _id

/resources/search?_id=b46f086ec6b24f25ae2aca61c1fc80a2    # retourne uniquement la métadonnée

