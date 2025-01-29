# Dashboard des Performances des Ventes (2021-2023)

##  Vue d'ensemble

Un tableau de bord interactif pour analyser les performances des ventes sur la période 2021-2023. Il permet de visualiser et suivre les KPIs essentiels des ventes à travers différentes catégories de produits.

##  Indicateurs Clés

Le dashboard présente les métriques suivantes :
- Chiffre d'affaire : 1,99M€ (variation de -14,68% par rapport à N-1)
- Profit : 1,17M€ (variation de -14,07%)
- Panier Moyen : 909,18€
- Nombre de commandes : 2,19K
- Total ventes : 6,99K unités

##  Fonctionnalités Principales

### Visualisations
- Répartition du CA, coût total et profit par catégorie de produits
- Évolution mensuelle du cumul des ventes
- Distribution géographique des profits par pays
- Comparaisons année par année (N vs N-1)

### Catégories de Produits
- Ordinateurs
- Smartphones
- Électroménagers
- Vidéo
- Culture
- Photo
- Audio
- Jeux

## 🔧 Mesures DAX Principales

### 1. Variation du Chiffre d'Affaire (VariationCA)
```dax
VariationCA = 
VAR Variation = 
    IF(
        ISBLANK([CA Année Précédente]),
        0,
        DIVIDE(
            [Chiffre d'affaire] - [CA Année Précédente],
            [CA Année Précédente],
            0
        )
    )
RETURN FORMAT(Variation, "0.00%")
```

### 2. CA Année Précédente
```dax
CA Année Précédente = 
CALCULATE(
    SUMX(
        Ventes,
        Ventes[Quantité] * Ventes[Prix Unitaire]
    ),
    SAMEPERIODLASTYEAR(Calendrier[Date])
)
```

### 3. Panier Moyen
```dax
Panier Moyen = 
DIVIDE(
    [Chiffre d'affaire],
    COUNTROWS(Ventes),
    0
)
```

## 📱 Vues Disponibles
- Vue globale 2021
- Vue globale 2022
- Vue globale 2023
- Vue spécifique Ordinateurs 2023

## 💡 Utilisation

Ce dashboard permet de :
- Suivre les performances de vente en temps réel
- Analyser les tendances par catégorie de produits
- Comparer les performances année par année
- Identifier les zones géographiques les plus performantes
- Surveiller l'évolution du panier moyen


