# Liens associés à des métadonnées

Les liens permettent de lier des ressources externes à une fiche de métadonnée.

## Attributs commun

url: l’URL de la ressource associée  
title: le titre de la ressource associée

actions: tableau d’actions possibles sur cette ressource associée. Peut prendre les valeurs :

* view : la ressource associée est destinée à être visualisée
* download : la ressource associée est destinée à être téléchargée
* other : des actions autres que la visualisation ou le téléchargement sont possibles sur la ressource associée 

size: \(uniquement disponible pour les ressources associée de type hosted\) taille du fichier hébergé en octets  
link: \(uniquement pour les ressources associées de type link\): ressource associée pointée

## Types de ressources décrites

kind: type de ressource vers lequel pointe la ressource associée. Peut prendre les valeurs :

* url: pas d’information précise \(site web, pdf, …\)
* data: donnée \(zip, rar, png, …\)

### Attributs dépréciés

isHeader: \(déprécié\) indique si la ressource associée doit être affichée dans l’en-tête de la donnée dans la plateforme Isogeo

* kind :
  * wfs: Web Feature Service
  * wms: Web Map Service
  * wmts: Web Map Tile Service
  * esriFeatureService: service d’entité Esri
  * esriMapService: service de carte Esri
  * esriTileService: service de tuiles Esri

## Types de liens

type: type de la ressource associée. Peut prendre les valeurs :

* url: une simple URL.
* hosted: une URL \(relative\) vers un fichier hébergé sur la plateforme Isogeo. une application tierce devra en général rendre cette URL accessible via un proxy.
* link: lien issu d’une autre ressource \(voir plus bas pour plus d’explications\).



