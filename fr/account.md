---
description: Isogeo API - Profil utilisateur (compte, options, abonnement, groupes de travail...)
---

# Compte utilisateur

## Profil {#user-profile}

| Verbe HTTP | URI            | Description                                 |
| :---       | :------------- | :------------------------------------------ |
| GET        | /account       | Profil et options de l'utilisateur          |

```json
{
    '_id': '89ee0eb3a15046a28886033b27f1d882',
    '_created': '2014-03-14T14:11:40.6815298+00:00',
    '_modified': '2018-06-07T08:13:32.0826782+00:00',
    'staff': True,
    'contact': {
        '_id': '647ce48061a64faf9f75577a41a63229',
        '_tag': 'contact:user:647ce48061a64faf9f75577a41a63229',
        '_deleted': False,
        'type': 'user',
        'name': 'Prénom NOM',
        'email': 'prenom.nom@organization.com',
        'phone': '+33 6 69 11 82 18',
        'addressLine1': '26 rue du faubourg Saint-Antoine',
        'city': 'Paris',
        'zipCode': '75012',
        'countryCode': 'FR',
        'hash': 'Loremipsumdolorsitametconsectetu',
        'available': False
        },
    'language': '',
    'timezone': 'Romance Standard Time',
    'mailchimp': {
        'subscriptions': [
            {
                'name': 'NewReleases',
                'isInterested': True
            },
            {
                'name': 'TipsAndTricks',
                'isInterested': True
            }
        ]
    }
}
```

## Droits {#user-memberships}

| Verbe HTTP | URI                  | Description                                               |
| :---       | :------------------- | :-------------------------------------------------------- |
| GET        | /account/memberships | Liste des groupes de travail auquel l'utilisateur a accès |

```json
[
    {
        '_id': '89ee0eb3a15046a28886033b27f1d882',
        '_created': '2014-03-14T14:11:40.6815298+00:00',
        '_modified': '2018-06-07T08:13:32.0826782+00:00',
        'staff': True,
        'contact': {
            '_id': '647ce48061a64faf9f75577a41a63229',
            '_tag': 'contact:user:647ce48061a64faf9f75577a41a63229',
            '_deleted': False,
            'type': 'user',
            'name': 'Prénom NOM',
            'email': 'prenom.nom@organization.com',
            'phone': '+33 6 69 11 82 18',
            'addressLine1': '26 rue du faubourg Saint-Antoine',
            'city': 'Paris',
            'zipCode': '75012',
            'countryCode': 'FR',
            'hash': 'Loremipsumdolorsitametconsectetu',
            'available': False
            },
        'group': {
            '_id': '60a8a69b7a8e43e5881800749a24068c',
            '_tag': 'owner:60a8a69b7a8e43e5881800749a24068c',
            '_created': '2016-11-29T09:04:49.8446535+00:00',
            '_modified': '2016-12-05T18:00:28.0279419+00:00',
            'contact': {
                '_id': '1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
                '_tag': 'contact:group:1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
                '_deleted': False,
                'type': 'group',
                'name': 'Agglomération de la Métadonnée',
                'email': 'sig@organization.com',
                'phone': '+33 1 23 45 67 89',
                'addressLine1': '1 Rue du Faubourg Saint-Antoine',
                'addressLine2': 'CS10317',
                'city': 'Isogeo Cedex',
                'zipCode': '33140',
                'countryCode': 'FR',
                'available': True
            },
            'canCreateMetadata': True,
            'canCreateLegacyServiceLinks': True,
            'areKeywordsRestricted': False,
            'hasCswClient': False,
            'hasScanFme': True,
            'keywordsCasing': 'capitalized',
            'metadataLanguage': 'fr'
        }
    },
    {
        '_id': '1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
        '_created': '2014-03-14T14:11:40.6815298+00:00',
        '_modified': '2018-06-07T08:13:32.0826782+00:00',
        'staff': True,
        'contact': {
            '_id': '1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
            '_tag': 'contact:user:1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
            '_deleted': False,
            'type': 'user',
            'name': 'Prénom NOM',
            'email': 'prenom.nom@organization.com',
            'phone': '+33 6 69 11 82 18',
            'addressLine1': '26 rue du faubourg Saint-Antoine',
            'city': 'Paris',
            'zipCode': '75012',
            'countryCode': 'FR',
            'hash': 'Loremipsumdolorsitametconsectetu',
            'available': False
            },
        'group': {
            '_id': '1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
            '_tag': 'owner:1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
            '_created': '2017-02-20T16:53:48.8643365+00:00',
            '_modified': '2017-08-29T12:44:00.0887129+00:00',
            'contact': {
                '_id': '1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
                '_tag': 'contact:group:1a2b3c4d5e6f7g8h9i0j11k12l13m14n',
                '_deleted': False,
                'type': 'group',
                'name': 'Agglomération de la Métadonnée',
                'email': 'sig@organization.com',
                'phone': '+33 1 23 45 67 89',
                'addressLine1': '1 Rue du Faubourg Saint-Antoine',
                'addressLine2': 'CS10317',
                'city': 'Isogeo Cedex',
                'zipCode': '33140',
                'countryCode': 'FR',
                'available': True
            },
        'canCreateMetadata': True,
        'canCreateLegacyServiceLinks': True,
        'areKeywordsRestricted': False,
        'hasCswClient': False,
        'hasScanFme': False,
        'keywordsCasing': 'lowercase',
        'metadataLanguage': 'fr',
        'themeColor': '#188AAA'
        }
    }
]
```
