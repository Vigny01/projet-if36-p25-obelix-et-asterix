# Analyse croisée : Superstore & Walmart

## Introduction

### Contexte et objectif

Dans le cadre de ce projet, nous avons travaillé avec **deux jeux de données différents mais complémentaires**. Ces données permettent d’explorer plusieurs aspects du commerce de détail : les ventes, les produits, les clients, la rentabilité, etc.

- Le premier fichier, appelé *Superstore*, regroupe presque 10 000 lignes de commandes passées dans une entreprise fictive de e-commerce.
- Le second fichier, basé sur des ventes dans des magasins Walmart, contient des données orientées “point de vente” : horaires, satisfaction client, modes de paiement...

L’objectif est de **mener une exploration** sur les données. Nous avons voulu comprendre comment ces systèmes fonctionnent, ce qui génère du profit ou non, et peut-être découvrir des profils de clients, des tendances d’achat ou des produits phares.

---

## Structure et nature des données

###  [Données Superstore](https://www.kaggle.com/datasets/aksha17/superstore-sales)

Ce fichier CSV contient **9994 lignes** et **21 variables**. Il s’agit d’un historique de ventes avec des informations sur les commandes, les clients, les produits et la logistique.

**Variables numériques :**

- `Sales` : montant de la vente.
- `Quantity` : nombre d’unités vendues.
- `Discount` : remise appliquée.
- `Profit` : profit net.
- `Postal Code`, `Row ID` : identifiants.

**Variables temporelles :**

- `Order Date` : date de commande.
- `Ship Date` : date d’expédition.

**Variables nominales :**

- `Order ID`, `Customer ID`, `Product ID` : identifiants.
- `Customer Name` : nom du client.
- `Segment` : type de client.
- `Region`, `State`, `City` : localisation.
- `Ship Mode` : mode d’expédition.
- `Category`, `Sub-Category`, `Product Name` : classification des produits.



---

### [Données Walmart](https://www.kaggle.com/datasets/antaesterlin/walmart-commerce-data)

Ce fichier CSV contient **1000 transactions** et **20 variables**. Il fournit des données détaillées sur chaque vente : prix, quantité, mode de paiement, heure, etc.

**Variables numériques :**

- `unit_price` : prix unitaire.
- `quantity` : quantité achetée.
- `vat` : taxe.
- `total` : montant total payé.
- `cogs` : coût du produit.
- `gross_margin_pct` : pourcentage de marge brute.
- `gross_income` : bénéfice.
- `rating` : note du client (sur 10).

**Variables temporelles :**

- `dtme` : date de la vente.
- `tme` : heure.
- `time_of_day` : moment (matin, après-midi...).
- `day_name`, `month_name` : jour et mois de l’achat.

**Variables nominales :**

- `invoice_id` : identifiant de facture.
- `branch`, `city` : lieu.
- `customer_type` : type de client.
- `gender` : genre.
- `product_line` : type de produit.
- `payment_method` : moyen de paiement.

---

## Plan d’analyse

Nous avons commencé par **explorer les deux jeux de données séparément** : voir ce qui se vend, ce qui rapporte, ce qui coûte, etc. Ensuite, nous avons croisé certaines dimensions pour voir s’il existe des similitudes (par exemple, certaines heures ou remises rendent-elles les ventes plus profitables ?).

Les outils utilisés :

- Diagrammes à barres : pour voir les produits ou catégories populaires.
- Boxplots : pour comparer des groupes (ex. hommes vs femmes).
- Scatter plots : pour voir s’il y a des liens entre deux données.
- Graphiques temporels : pour suivre les ventes dans le temps.

---

## Questions de recherche

|    # | Question (niveau enfant de 12 ans)                           | Variables utilisées                  | Visualisation | Objectif      |
| ---: | ------------------------------------------------------------ | ------------------------------------ | ------------- | ------------- |
|    1 | Quel groupe de clients gagne le plus d’argent ?              | Segment, Profit (Superstore)         | Boxplot       | Comparer      |
|    2 | Est-ce qu’on vend plus certains jours ?                      | day_name, total (Walmart)            | Bar chart     | Évolution     |
|    3 | Est-ce qu’une réduction fait toujours gagner de l’argent ?   | Discount, Profit (Superstore)        | Scatter       | Relation      |
|    4 | Quels produits rapportent le plus ?                          | Product Name, gross_income (Walmart) | Bar chart     | Décomposition |
|    5 | Quelles catégories perdent de l’argent avec les réductions ? | Category, Profit, Discount           | Boxplot       | Relation      |
|    6 | Les choses chères sont-elles mieux notées ?                  | unit_price, rating (Walmart)         | Scatter       | Relation      |
|    7 | Les femmes dépensent-elles plus ?                            | gender, total (Walmart)              | Boxplot       | Comparer      |
|    8 | Est-ce qu’un long délai de livraison fait perdre de l’argent ? | Ship Date, Order Date, Profit        | Histogramme   | Relation      |
|    9 | Quelle catégorie a la plus grosse marge ?                    | product_line, gross_margin_pct       | Bar chart     | Décomposition |
|   10 | Quel moment de la journée rapporte le plus ?                 | time_of_day, gross_income            | Bar chart     | Distribution  |
|   11 | Est-ce qu’il y a des saisons où on vend plus ?               | Order Date, dtme                     | Line chart    | Évolution     |
|   12 | Quels États font le plus de ventes ?                         | State, Sales                         | Bar chart     | Distribution  |
|   13 | Est-ce que les membres dépensent plus ?                      | customer_type, total                 | Boxplot       | Comparer      |
|   14 | Quels produits sont beaucoup achetés ?                       | Product Name, Quantity               | Bar chart     | Décomposition |
|   15 | Est-ce que la façon de payer change le prix moyen ?          | payment_method, total                | Boxplot       | Comparer      |
|   16 | Quelles sous-catégories ne rapportent pas ?                  | Sub-Category, Profit                 | Bar chart     | Décomposition |
|   17 | Quelle boutique gagne le plus d’argent ?                     | branch, gross_income                 | Bar chart     | Comparer      |
|   18 | Une réduction pousse-t-elle à acheter plus ?                 | Discount, Quantity                   | Scatter       | Relation      |
|   19 | Est-ce que les gens notent mieux s’ils paient plus ?         | rating, total                        | Scatter       | Relation      |
|   20 | À quelle heure achète-t-on le plus ?                         | tme, total                           | Line chart    | Évolution     |

---

## Conclusion

Ce projet était principalement exploratoire. Il nous a permis de mieux comprendre comment lire et analyser un jeu de données. 

Nous envisageons de pousser l’analyse plus loin avec des techniques comme le clustering ou la prédiction. Pour le moment, l’accent a été mis sur la clarté, la documentation.

---
