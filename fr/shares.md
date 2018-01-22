# Partages

GET /shares  
GET /share/{:sid}






## Réponse exemple

```json
[
    {
        "_created": "2014-09-25T21:20:36.1845765+00:00",
        "_creator": {
            "_created": "2014-04-18T16:23:38.617093+00:00",
            "_id": "08b3054757544463abd06f3ab51ee491",
            "_modified": "2017-12-19T14:31:13.9735939+00:00",
            "_tag": "owner:08b3054757544463abd06f3ab51ee491",
            "areKeywordsRestricted": false,
            "canCreateLegacyServiceLinks": true,
            "canCreateMetadata": true,
            "contact": {
                "_deleted": false,
                "_id": "80aabc302fe946c8a51fffe22d60eb77",
                "_tag": "contact:group:80aabc302fe946c8a51fffe22d60eb77",
                "addressLine1": "26 rue du faubourg Saint-Antoine",
                "addressLine2": "4\u00e8me \u00e9tage",
                "available": false,
                "city": "Paris",
                "countryCode": "FR",
                "email": "contact@isogeo.com",
                "fax": "+33 9 81 40 00 66",
                "name": "Isogeo Demo",
                "phone": "+33 9 67 46 50 06",
                "type": "group",
                "zipCode": "75012"
            },
            "hasCswClient": true,
            "hasScanFme": true,
            "keywordsCasing": "lowercase",
            "metadataLanguage": "fr"
        },
        "_id": "344d51c3edfb435daf9d98d948fa207e",
        "_modified": "2014-09-25T21:20:36.1845765+00:00",
        "applications": [
            {
                "_created": "2015-12-30T14:10:36.2323958+00:00",
                "_id": "674b014ebc094bbd8f3036a6f124f541",
                "_modified": "2016-03-11T15:13:39.6829502+00:00",
                "kind": "confidential",
                "name": "Python Minimalist SDK - D\u00e9v",
                "staff": false,
                "type": "group",
                "url": "https://github.com/Guts/isogeo-api-py-minsdk"
            }
        ],
        "catalogs": [],
        "name": "D\u00e9monstration (interne)",
        "rights": [],
        "type": "application",
        "urlToken": "Sbbbbbbd1E8n7LDqzq3azRqNhiMHZf0aaaaaaa"
    },
]
```
