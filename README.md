# Analyse des incendies aux États-Unis

## Introduction

### Données

Pour ce projet, nous avons choisi d’analyser les incendies survenus aux États-Unis en nous appuyant sur un jeu de données enrichi, disponible sur Kaggle : [US Wildfire Data + Other Attributes](https://www.kaggle.com/datasets/capcloudcoder/us-wildfire-data-plus-other-attributes). Ce dataset regroupe de nombreuses informations détaillées sur plus de deux millions d'incendies, avec un focus sur les conditions météorologiques, les causes des feux et leur répartition géographique et temporelle.

L’objectif de cette base de données est de fournir un aperçu à la fois complet et structuré des feux de forêt sur le territoire américain. Elle compile des données provenant d’agences telles que la NOAA (National Oceanic and Atmospheric Administration) ou encore le US Forest Service.

#### Structure et contenu

Le fichier est au format CSV et contient plus de 30 variables. Parmi elles, on retrouve :

- **Données numériques** :
  - `FIRE_SIZE` : superficie brûlée (en acres)
  - `TEMP`, `HUMIDITY`, `WIND`, `PRECIP` : conditions météo moyennes
  - `LATITUDE`, `LONGITUDE` : localisation des feux

- **Données ordinales** :
  - `FIRE_YEAR` : année de survenue de l'incendie
  - `DISCOVERY_DOY`, `CONT_DOY` : jour de l'année (Day Of Year) de début/fin
  - `MONTH` : mois d’occurrence

- **Données nominales** :
  - `STAT_CAUSE_DESCR` : description de la cause (foudre, humaine, etc.)
  - `STATE`, `COUNTY` : localisation administrative
  - `FIRE_NAME`, `FIRE_CODE` : identifiants uniques des feux


Ces données sont réparties dans le temps (sur plusieurs décennies), dans l’espace (États et comtés), et selon la nature des incendies (naturels, humains, inconnus). C’est cette richesse qui a motivé notre choix : elle permet d’aborder les incendies sous plusieurs angles – environnemental, humain et climatique.

### Plan d’analyse

L’objectif principal de notre étude est de mieux comprendre les facteurs qui influencent les incendies : où et quand se produisent-ils le plus souvent ? Quelle est leur origine ? Quel rôle joue la météo dans leur intensité ? À partir de ces questions, nous chercherons à extraire des tendances claires et à identifier des zones ou des périodes à risque.

#### Objectifs

Nous avons défini plusieurs axes d’analyse :

1. Identifier les principales causes des incendies.
2. Repérer les périodes de l’année les plus sensibles.
3. Localiser les régions les plus touchées, en fréquence comme en intensité.
4. Analyser le lien entre les conditions météorologiques et la taille des feux.
5. Étudier l’évolution des incendies dans le temps : y a-t-il plus de feux aujourd’hui qu’avant ?


#### Questions à explorer

Voici quelques questions que nous souhaitons approfondir au cours de notre analyse, accompagnées des variables mobilisées et des visualisations envisagées :

| Question | Variables utilisées | Visualisation prévue |
|----------|---------------------|-------------|
| Quelles sont les causes les plus fréquentes ? | `STAT_CAUSE_DESCR` | histogramme |
| Les incendies sont-ils plus fréquents à certaines périodes de l’année ? | `MONTH`, `FIRE_SIZE` | Courbes mensuelles, boxplots |
| Certains États sont-ils plus exposés que d'autres ? | `STATE`, `FIRE_SIZE` | Cartes par État, histogrammes |
| Quelle est l’évolution des incendies dans le temps ? | `FIRE_YEAR`, `FIRE_SIZE` | Graphiques de tendance |
| Existe-t-il une corrélation entre la température et la superficie brûlée ? | `TEMP`, `FIRE_SIZE` | Nuages de points, heatmaps |
| L’humidité ou la pluie ont-elles un effet protecteur ? | `HUMIDITY`, `PRECIP`, `FIRE_SIZE` | Courbes comparatives, scatterplots |
| Les incendies d’origine humaine sont-ils plus destructeurs que les autres ? | `STAT_CAUSE_DESCR`, `FIRE_SIZE` | Boxplots par type de cause |


#### Méthodologie prévue

Avant d’entrer dans l’analyse à proprement parler, nous commencerons par une phase de nettoyage et d’exploration du dataset. Nous vérifierons la qualité des données, corrigerons les incohérences éventuelles, et nous assurerons que toutes les variables sont bien typées (numériques, catégorielles, dates…).

Ensuite, nous réaliserons des analyses descriptives : moyenne des superficies brûlées, distribution des causes, nombre de feux par État ou par année. À cela s’ajouteront des analyses croisées pour comprendre, par exemple, si la température est un facteur aggravant, ou si les feux d’origine humaine ont tendance à être plus importants.


#### Limites potentielles

Certains éléments pourraient venir compliquer l’analyse : les conditions météo ne sont pas toujours parfaitement synchronisées avec chaque incendie, certaines valeurs extrêmes peuvent fausser les moyennes, et il existe peut-être des biais dans la collecte des données (zones plus surveillées que d’autres, etc.). Nous garderons ces aspects à l’esprit tout au long du projet.

## Conclusion

Ce projet s’inscrit dans une démarche d’analyse à la fois environnementale et sociétale. En explorant les incendies aux États-Unis à travers un jeu de données riche et structuré, nous espérons dégager des tendances utiles à la compréhension du phénomène, tout en identifiant des leviers potentiels pour la prévention. L’approche choisie se veut rigoureuse, visuelle, et progressive, afin d’aboutir à une restitution claire et accessible des résultats.
