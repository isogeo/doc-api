[![CircleCI](https://circleci.com/gh/isogeo/doc-api.svg?style=svg)](https://circleci.com/gh/isogeo/doc-api)

# Isogeo - API documentation

Content, structure and media of the website documentation. It's part of the Isogeo online documentations ([see Github repositories](https://github.com/search?q=topic%3Adocumentation+org%3Aisogeo&type=Repositories)).

## Edit this documentation

It's based on Gitbook v3.2.* which is:

* [a book format](https://github.com/GitbookIO/gitbook)
* [a toolchain](https://toolchain.gitbook.com/)

## Deployment

It's deployed on Isogeo Azure (Storage v2 Static website) using CircleCI ([see config](https://github.com/isogeo/doc-api/blob/master/.circleci/config.yml)):

* QA: https://qaisogeohelp.z28.web.core.windows.net/api/
* PROD: https://prodisogeohelp.z28.web.core.windows.net/api/

Deployment rules:

* each commit triggers a deployment on QA
* each tagged commit triggers a deployment on PROD - [see tags](https://github.com/isogeo/doc-api/tags)
