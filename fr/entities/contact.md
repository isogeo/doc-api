# Contacts

3 types possibles :

- `custom`: contacts créés au sein d'un groupe de travail
- `group`: coordonnées d'un groupe de travail
- `user`: coordonnées d'un utilisateur

## GET

| Verbe HTTP | URI                            | Description                           |
| :---       | :----------------------------- | :------------------------------------ |
| GET        | /contacts/{contact_uuid}       | Obtenir un contact en particulier     |

### Exemple

```json
{
    "_abilities": [
        "contact:delete",
        "contact:update"
    ],
    "_deleted": false,
    "_id": "49a4985041aebee76c337d82faaaaaa",
    "_tag": "contact:1a2b3c4d5e6f7g8h9i0j11k12l:49a4985041aebee76c337d82faaaaaa",
    "addressLine1": "Adresse ligne 1",
    "addressLine2": "Adresse ligne 3",
    "addressLine3": "Adresse ligne 3",
    "city": "Bordeaux",
    "count": 4,
    "countryCode": "FR",
    "email": "test@isogeo.com",
    "fax": "+33510203041",
    "name": "TEST - CONTACT 1",
    "organization": "Zozogeo",
    "owner": {
        "_created": "2015-05-21T12:08:16.4295098+00:00",
        "_id": "1a2b3c4d5e6f7g8h9i0j11k12l",
        "_modified": "2018-12-27T10:47:28.7880956+00:00",
        "_tag": "owner:1a2b3c4d5e6f7g8h9i0j11k12l",
        "areKeywordsRestricted": false,
        "canCreateLegacyServiceLinks": true,
        "canCreateMetadata": true,
        "contact": {
            "_deleted": false,
            "_id": "1a2b3c4d5e6f7g8h9i0j11k12l",
            "_tag": "contact:group:1a2b3c4d5e6f7g8h9i0j11k12l",
            "addressLine1": "26 rue du faubourg Saint-Antoine",
            "addressLine2": "4\u00e9me \u00e9tage",
            "addressLine3": "bouton porte",
            "available": false,
            "city": "Paris",
            "countryCode": "FR",
            "email": "dev@isogeo.com",
            "fax": "33 (0)9 67 46 50 06",
            "name": "Isogeo Test",
            "phone": "33 (0)9 67 46 50 06",
            "type": "group",
            "zipCode": "75012"
        },
        "hasCswClient": true,
        "hasScanFme": true,
        "keywordsCasing": "lowercase",
        "metadataLanguage": "fr",
        "themeColor": "#4499A1"
    },
    "phone": "+33510203040",
    "type": "custom",
    "zipCode": "33000"
}
```

----

## POST


