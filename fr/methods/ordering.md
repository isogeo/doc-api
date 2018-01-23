# Trier les résultats

## Critère de tri {#ob}

### Description

Signifie OrderBy. Permet de trier les résultats de la recherche.

###  Valeurs

  
\_created : \(défaut\) date de création de la fiche de métadonnées.  
\_modified : date de la dernière modification de la fiche de métadonnées.  
title: titre de la ressource.  
created : date de création de la ressource \(pas forcément renseignée\).  
modified : date de dernière modification de la ressource \(pas forcément renseignée\).  
relevance: score de pertinence par rapport aux termes de recherche.

  
Exemples  
/resources/search?ob=title  
Renvoie les ressources triées par titre.

---

## Sens du tri {#od}

  
Description  
Signifie OrderDirection. Permet de choisir le sens du tri.  
Valeurs:  
desc: \(défaut\) descendant  
asc: ascendant  
Exemples  
/resources/search?ob=title&od=asc  
Renvoie les ressources triées par ordre alphabétique.

