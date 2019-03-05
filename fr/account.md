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
        '_id': '4f5f97e268cd475f8df2e76971e42102',
        'role': 'admin',
        'user': {
            '_id': '89ee0eb3a15046a28886033b27f1d882',
            '_created': '2014-03-14T14:11:40.6815298+00:00',
            '_modified': '2018-06-07T08:13:32.0826782+00:00',
            'staff': True,
            'contact': {
                '_id': '647ce48061a64faf9f75577a41a63229',
                '_tag': 'contact:user:647ce48061a64faf9f75577a41a63229',
                '_deleted': False,
                'type': 'user',
                'name': 'Julien MOURA',
                'email': 'julien.moura@isogeo.com',
                'phone': '+33 6 58 00 30 64',
                'addressLine1': '26 rue du faubourg Saint-Antoine',
                'city': 'Paris',
                'zipCode': '75012',
                'countryCode': 'FR',
                'hash': '23bc09e00e945c3c2cc0d13f7448c261',
                'available': False
            },
            'language': '',
            'timezone': 'Romance Standard Time'
        },
        'group': {
            '_id': '60a8a69b7a8e43e5881800749a24068c',
            '_tag': 'owner:60a8a69b7a8e43e5881800749a24068c',
            '_created': '2016-11-29T09:04:49.8446535+00:00',
            '_modified': '2016-12-05T18:00:28.0279419+00:00',
            'contact': {
                '_id': '3ae98fa874e242ae9bd2a12c4e29291d',
                '_tag': 'contact:group:3ae98fa874e242ae9bd2a12c4e29291d',
                '_deleted': False,
                'type': 'group',
                'name': 'Conseil de territoire Istres-Ouest Provence',
                'email': 'michel.privat@ampmetropole.fr',
                'city': 'Istres',
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
        '_id': '583cad9b678a4e6982392ae0830eaec4',
        'role': 'admin',
        'user': {
            '_id': '89ee0eb3a15046a28886033b27f1d882',
            '_created': '2014-03-14T14:11:40.6815298+00:00',
            '_modified': '2018-06-07T08:13:32.0826782+00:00',
            'staff': True,
            'contact': {
                '_id': '647ce48061a64faf9f75577a41a63229',
                '_tag': 'contact:user:647ce48061a64faf9f75577a41a63229',
                '_deleted': False,
                'type': 'user',
                'name': 'Julien MOURA',
                'email': 'julien.moura@isogeo.com',
                'phone': '+33 6 58 00 30 64', 'addressLine1': '26 rue du faubourg Saint-Antoine',
                'city': 'Paris',
                'zipCode': '75012',
                'countryCode': 'FR',
                'hash': '23bc09e00e945c3c2cc0d13f7448c261',
                'available': False
            },
            'language': '',
            'timezone': 'Romance Standard Time'
        },
        'group': {
            '_id': '14f2720433c048d4b34400c3ce6b0bf7', '_tag': 'owner:14f2720433c048d4b34400c3ce6b0bf7', '_created': '2017-02-20T16:53:48.8643365+00:00', '_modified': '2017-08-29T12:44:00.0887129+00:00', 'contact': {'_id': '3f8f7607069c4a0984e22032f9b6775d', '_tag': 'contact:group:3f8f7607069c4a0984e22032f9b6775d', '_deleted': False, 'type': 'group', 'name': 'Agglomération Montargoise Et rives du loing', 'email': 'sig@agglo-montargoise.fr', 'phone': '0238950876', 'addressLine1': '1 Rue du Faubourg de la Chaussée', 'addressLine2': 'CS10317', 'city': 'MONTARGIS Cedex', 'zipCode': '45125', 'countryCode': 'FR', 'available': True}, 'canCreateMetadata': True, 'canCreateLegacyServiceLinks': True, 'areKeywordsRestricted': False,
            'hasCswClient': False, 'hasScanFme': False, 'keywordsCasing': 'lowercase', 'metadataLanguage': 'fr',
            'themeColor': '#188AAA'
        }
    }
]
```
