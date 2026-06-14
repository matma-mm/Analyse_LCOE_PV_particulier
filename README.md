# Analyse LCOE PV pour Installations Photovoltaïques Particulières

## Description Générale

Ce projet propose une analyse complète du coût de production du kilowattheure (LCOE - Levelized Cost of Energy) pour une installation photovoltaïque résidentielle. 

L'objectif principal est de :
- Analyser les données de consommation et production d'une installation solaire
- Évaluer l'autoconsommation et les déficits énergétiques
- Calculer le LCOE en tenant compte des paramètres économiques de l'installation
- Modéliser la dégradation de performance sur la durée de vie du système

## Fonctionnalités Principales

### 1. Analyse des Données Énergétiques
- Importation de données horaires de consommation et production PV
- Fusion et organisation temporelle des données (année complète 2020, 8760 heures)
- Visualisation des courbes de consommation vs production

### 2. Calcul d'Autoconsommation
- Détermination de l'énergie consommée localement
- Analyse des heures d'excédent et de déficit énergétique
- Identification des périodes critiques

### 3. Analyse du Déficit Énergétique
- Quantification des heures en déficit (4886 heures sur l'année)
- Durée maximale d'un déficit continu (19 heures)
- Distribution statistique des durées de déficit
- Visualisation avec histogramme et courbe de densité

### 4. Calcul du LCOE
Le LCOE est calculé selon deux approches :

#### a) LCOE Standard
```
LCOE = (CAPEX annualisé + Coûts O&M) / Production énergétique annuelle
```

#### b) LCOE avec Dégradation
Prend en compte la dégradation progressive des panneaux sur 20 ans
- Taux de dégradation : 0,5% par an
- Actualisation des flux de trésorerie

## Données d'Entrée

### Paramètres de l'Installation
| Paramètre | Valeur | Unité |
|-----------|--------|-------|
| Puissance installée | 8-20 | kWc |
| Facteur de charge | 12,15% | % |
| Coût d'investissement initial | 2830 | $/kW |
| Coûts O&M fixes | 50 | $/kW/an |
| Taux d'intérêt | 0,01% | % |
| Durée de vie | 20 | ans |
| Taux de dégradation | 0,5% | %/an |

### Données de Consommation/Production
- Résolution temporelle : Horaire
- Période : 1 janvier - 31 décembre 2020 (8760 heures)
- Colonnes principales :
  - Consommation du ménage (kWh)
  - Production PV brute et nette (kWc)

## Technologie Utilisée

- Python 3.x
- Pandas : Manipulation et analyse de données
- NumPy : Calculs numériques
- Matplotlib & Seaborn : Visualisation
- SciPy : Optimisation numérique

## Résultats Typiques

Pour une installation de 8 kWc :
- LCOE calculé : ~179,93 $/MWh
- Autoconsommation totale : Variable selon la courbe de charge
- Déficit énergétique : 4886 heures/an (55,8%)

## Structure du Projet

```
Analyse_LCOE_PV_particulier/
├── README.md (ce fichier)
├── analyse_LCOE_particulier.ipynb (notebook principal)
└── exo_Autoconso_PV.xlsx (données source)
```

## Utilisation

1. Cloner le dépôt :
```bash
git clone https://github.com/matma-mm/Analyse_LCOE_PV_particulier
cd Analyse_LCOE_PV_particulier
```

2. Installer les dépendances :
```bash
pip install pandas numpy matplotlib seaborn scipy openpyxl
```

3. Exécuter le notebook :
```bash
jupyter notebook analyse_LCOE_particulier.ipynb
```

## Étapes de l'Analyse

### Phase 1 : Préparation des Données
- Chargement du fichier Excel
- Fusion date/heure
- Nettoyage et formatage

### Phase 2 : Calcul d'Autoconsommation
- Extraction du minimum entre consommation et production
- Calcul des écarts (excédent/déficit)

### Phase 3 : Analyse du Déficit
- Identification des périodes déficitaires
- Groupement et durée de chaque période
- Statistiques descriptives

### Phase 4 : Calcul Économique
- LCOE sans et avec dégradation
- Actualisation sur la durée de vie
- Comparaison des scénarios

## Auteur

matma-mm

## Licence

Ce projet est ouvert à l'utilisation et à la modification.

## Support et Questions

Pour toute question ou suggestion, n'hésitez pas à ouvrir une issue dans ce dépôt.

---

Note : Cette analyse repose sur des données réelles d'une installation de 2020. Les résultats varient selon la géographie, les conditions météorologiques et les paramètres de l'installation.
