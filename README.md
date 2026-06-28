![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) 
![Power Query](https://img.shields.io/badge/Power_Query-217346?style=for-the-badge) 
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge) 
![SQL](https://img.shields.io/badge/SQL-00758F?style=for-the-badge&logo=mysql&logoColor=white) 

# Sales & Customer Insights Dashboard 

## Présentation du projet 

Ce projet consiste à concevoir une solution décisionnelle complète sous Power BI à partir des données bruts provenant de plusieurs sources différentes. 
L’objectif est d’aider une entreprise fictive 'AdventureWorks' qui est spécialisée dans la ventes des vélos et équipements à analyser ses performances commerciales, comprendre le comportement client et mesurer la satisfaction via les avis clients.  
Le projet combine analyse des ventes et analyse de sentiment pour offrir une vision complète du business. 
Pour plus de détail -> voir le rapport PDF. 

## Sources de données 

<img width="1106" height="352" alt="image" src="https://github.com/user-attachments/assets/53fdacc2-bdcc-4ca1-be69-a925edf8ff2f" /> 

1 - La base de cette entreteprise est une base transactionnelle (AdventureWorks2019) disponible sur le site de Microsoft (https://learn.microsoft.com/fr-fr/sql/samples/adventureworks-install-configure?view=sql-server-ver17&tabs=ssms). 

Cette base à été hebergée sur un server SQL en local. 

2 - Pour enrichir les données de cette base d'autres fichiers ont été créés : 

- Un fichier CSV, contenant 15 managers et commerciaux  fictifs qui ont été associés aux données des ventes.  
- Un fichier JSON contenant des avis clients aléatoire (généré par intelligence artificielle) qui a été associé aux ventes aussi.  

Ces 2 fichiers ont été hebergés sur un Blob Storage sur le cloud Azure. 

- Un fichier CSV contenant les objectifs des ventes des commerciaux. Fichier hebergé sur OneDrive. 
- Et finalement, une API a été utilisée pour pouvoir obtenir le taux de change à jour. 

## Modèle Sémantique 

<img width="1078" height="352" alt="image" src="https://github.com/user-attachments/assets/39988206-d202-4932-8c60-231a5292de1a" /> 

## ETL et Préparation des données 

Les traitements ont été réalisés avec Power Query : 

* Nettoyage des données. 
* Suppression des doublons. 
* Gestion des valeurs manquantes. 
* Standardisation des formats. 
* Dénormalisation des données OLTP (base transactionnelle AdventureWorks). 
* Fusion et enrichissement des données provenant de plusieurs sources. 

--- 

## Modélisation 

La base AdventureWorks étant initialement conçue pour un usage transactionnel (OLTP), elle a été restructurée en : 

* Modèle en étoile (Star Schema) 
* Modèle en constellation pour intégrer les avis clients 

Le modèle comprend : 

### Tables de faits 

* Ventes 
* Avis clients 

### Tables de dimensions 

* Dates 
* Produits 
* Clients 
* Géographie 
* Commerciaux 
* Managers 

--- 

## Fonctionnalités mises en œuvre 

### KPI et DAX 

* Chiffre d'affaires 
* Nombre de ventes 
* Objectifs commerciaux atteints 
* YTD (Year-To-Date) 
* MoM (Month-over-Month) 
* YoY (Year-over-Year) 

### Hiérarchie managériale 

Implémentation d'une hiérarchie Manager → Commercial grâce aux fonctions DAX : 

* PATH 
* PATHITEM 
* LOOKUPVALUE 

### Sécurité dynamique (RLS) 

Mise en place d'une Row-Level Security dynamique basée sur : 

* USERPRINCIPALNAME() 
* CALCULATE() 
* FILTER() 
* SELECTEDVALUE() 

### Analyse de sentiment 

Utilisation de Python et de la librairie TextBlob pour : 

* Calcul du score de sentiment 
* Classification Positive / Neutral / Negative 
* Détection automatique des thématiques : 
  * Livraison 
  * Qualité produit 
  * Prix 
  * Service client 

--- 

## Dashboard 

Le dashboard est composé de 4 pages : 

### Trend Analysis 

* Évolution des ventes 
* Comparaison avec l'année précédente 
* Analyse par catégorie de produit 

### Managers 

* Analyse des performances par manager 
* Suivi des objectifs 
* Analyse hiérarchique des équipes 

### Sales Person 

* Analyse détaillée par commercial 
* Drill-through depuis la vue manager 

### Reviews 
  
* Analyse de la satisfaction client 
* Répartition des sentiments 
* Analyse des thématiques principales 

--- 

## Captures d'écran 

### Dashboard - Trend Analysis 

<img width="1430" height="808" alt="image" src="https://github.com/user-attachments/assets/366ebf0c-604c-4dbd-977e-bf40e3ff1314" /> 

### Dashboard - Managers 

<img width="777" height="797" alt="image" src="https://github.com/user-attachments/assets/f9ced915-9efb-42e3-9185-c43f3c9867bf" /> 


### Dashboard - Sales Person 

<img width="523" height="850" alt="image" src="https://github.com/user-attachments/assets/537aae96-76f0-4f8d-9b0e-507b7cb378e9" /> 

### Dashboard - Reviews 

<img width="1297" height="726" alt="image" src="https://github.com/user-attachments/assets/bc13e967-50a1-4564-84d2-256721796492" /> 

--- 

## Conclusion 

Ce projet a permis de construire une chaîne décisionnelle complète en intégrant des données issues de sources variées (SQL Server, API, fichiers) dans Power BI.  
La transformation des données OLTP en un modèle en étoile a assuré des performances optimales et une structuration adaptée à l’analyse.  
Les mesures DAX ont permis de produire des indicateurs métier fiables, tandis que la mise en place d’une hiérarchie managériale et du RLS a renforcé la pertinence des analyses et la gouvernance des données.  
L’intégration d’une analyse de sentiment via Python a enrichi le modèle avec une dimension qualitative, offrant une meilleure compréhension de la satisfaction client.  
Les dashboards interactifs permettent une analyse multi-niveaux (globale, manager, individuel) et facilitent l’identification des tendances et leviers de performance.  
Ce projet démontre ainsi la capacité à concevoir un modèle analytique complet, robuste et orienté prise de décision. 


**Idriss FEKARI** 
