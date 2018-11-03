# Ségrégation de résultats par partage {#search_filter_share}

> Paramètre : s

## Description

Par défaut les routes de l’API concernent toutes les entités qui sont accessibles aux applications :

* les entités accessibles à l’utilisateur dans le cas d’une [application utilisateur](/authentication/usersapps.md).
* les entités partagées à l’application dans le cas d’une [application de groupe](/authentication/groupsapps.md).

Les applications tierces d'Isogeo accèdent aux catalogues de métadonnées que les administrateurs choisissent de leur partager via le menu "Partages" de l'interface d'administration ([voir documentation fonctionnelle](http://help.isogeo.com/fr/features/admin/shares.html)).

C'est lié au fait que :

* plusieurs groupes de travail peuvent partager des catalogues à une même application
* un groupe de travail peut créer plusieurs partages alimentant la même application (même si ce n'est pas recommandé aux administrateurs).

Par exemple, si un administrateur 1 du  GT (workgroup) A crée 2 partages différents à l'application PLUGIN et qu'un administrateur 2 du GT B crée 1 partage à la même application PLUGIN, alors la recherche s’effectuera sur l’ensemble des fiches contenues dans les 3 partages.

Ce paramètre permet à une application de proposer à l'utilisateur final de filtrer sur tel ou tel partage.

## Valeurs possibles

Le paramètre accepte l'identifiant d'un partage, c'est-à-dire une chaîne de 32 caractères alphanumériques, généré à la création du partage via l'interface d'administration d'Isogeo \(<https://app.isogeo.com/admin/shares/{sid})> :

![Identifiant d'un partage depuis APP](/assets/api_share_id_app_admin.png "Identifiant d&apos;un partage dans l&apos;interface d&apos;administration")

Pour récupérer les informations d'un partage ou plusieurs partages, consulter [la section dédiée](/shares.md).

---

## Exemple {#sample}

### Requête {#sample_request}

URL de recherche filtrée sur un partage :

```html
https://v1.api.isogeo.com/resources/search?s=c502e8f7c9da4c3aacdf3d905672d54c
```

L'application OpenCatalog fonctionne ainsi.

### Réponse {#sample_response}

```json
[
    {
        "_created": "2014-09-25T21:20:36.1845765+00:00",
        "_creator": {
            "_created": "2014-04-18T16:23:38.617093+00:00",
            "_id": "1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
            "_modified": "2017-12-19T14:31:13.9735939+00:00",
            "_tag": "owner:1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
            "areKeywordsRestricted": false,
            "canCreateLegacyServiceLinks": true,
            "canCreateMetadata": true,
            "contact": {
                "_deleted": false,
                "_id": "1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
                "_tag": "contact:group:1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
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
        "_id": "1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
        "_modified": "2014-09-25T21:20:36.1845765+00:00",
        "applications": [
            {
                "_created": "2015-12-30T14:10:36.2323958+00:00",
                "_id": "1a2b3c4d5e6f7g8h9i0j11k12l13m14n",
                "_modified": "2016-03-11T15:13:39.6829502+00:00",
                "kind": "confidential",
                "name": "Python Minimalist SDK",
                "staff": false,
                "type": "group",
                "url": "https://github.com/Isogeo/isogeo-api-py-minsdk"
            }
        ],
        "catalogs": [],
        "name": "D\u00e9monstration",
        "rights": [],
        "type": "application",
        "urlToken": "1a2b3c4d5e6f7g8h9i0j11k12l13m14n"
    },
]
```
