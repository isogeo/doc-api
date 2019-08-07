# Sous-ressources à inclure dans le modèle des résultats {#limit}

> Paramètre : **\_include**

## Description

Ce paramètre permet de gérer les différentes extensions du modèle à renvoyer pour les résultats de recherche. Il s'agit des mêmes sous-ressources détaillées dans

## Valeurs possibles

{% include "../../entities/subresources/metadata.md" %}

### Points de vigilance

A DOCUMENTER

### Exemples

```js
/resources/search?_include=contacts,links    # les résultats contiendront les informations sur les contacts et les liens asssociés
```

---
