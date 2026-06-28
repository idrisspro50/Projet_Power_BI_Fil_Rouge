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

<img width="915" height="300" alt="image" src="https://github.com/user-attachments/assets/befdb084-bd5a-4d95-91ad-e6ec58287a73" />

1 - La base de cette entreteprise est une base transactionnelle (AdventureWorks2019) disponible sur le site de Microsoft (https://learn.microsoft.com/fr-fr/sql/samples/adventureworks-install-configure?view=sql-server-ver17&tabs=ssms). 

Cette base à été hebergée sur un server SQL en local. 

2 - Pour enrichir les données de cette base d'autres fichiers ont été créés : 

- Un fichier CSV, contenant 15 managers et commerciaux  fictifs qui ont été associés aux données des ventes.  
- Un fichier JSON contenant des avis clients aléatoire (généré par intelligence artificielle) qui a été associé aux ventes aussi.  

Ces 2 fichiers ont été hebergés sur un Blob Storage sur le cloud Azure. 

- Un fichier CSV contenant les objectifs des ventes des commerciaux. Fichier hebergé sur OneDrive. 
- Et finalement, une API a été utilisée pour pouvoir obtenir le taux de change à jour. 

## Modèle Sémantique 

<img width="896" height="286" alt="image" src="https://github.com/user-attachments/assets/22b11017-e8b9-4a33-958e-06e316e5c0fa" />

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

<img width="896" height="500" alt="image" src="https://github.com/user-attachments/assets/26bce9a6-cb02-4bbc-8489-fee80295fe2d" />

### Managers 

* Analyse des performances par manager 
* Suivi des objectifs 
* Analyse hiérarchique des équipes 

<img width="674" height="695" alt="image" src="https://github.com/user-attachments/assets/a5061980-7492-47dd-b1c6-13a52984b8a1" />

### Sales Person 

* Analyse détaillée par commercial 
* Drill-through depuis la vue manager 

<img width="482" height="778" alt="image" src="https://github.com/user-attachments/assets/74f6c7a8-5beb-4201-83d9-dc9987725094" />

### Reviews 
  
* Analyse de la satisfaction client 
* Répartition des sentiments 
* Analyse des thématiques principales 

<img width="1034" height="574" alt="image" src="https://github.com/user-attachments/assets/a7dd596c-e211-443c-a5cc-b40f9de4ce22" />


--- 

## Conclusion 

Ce projet a permis de construire une chaîne décisionnelle complète en intégrant des données issues de sources variées (SQL Server, API, fichiers) dans Power BI.  
La transformation des données OLTP en un modèle en étoile a assuré des performances optimales et une structuration adaptée à l’analyse.  
Les mesures DAX ont permis de produire des indicateurs métier fiables, tandis que la mise en place d’une hiérarchie managériale et du RLS a renforcé la pertinence des analyses et la gouvernance des données.  
L’intégration d’une analyse de sentiment via Python a enrichi le modèle avec une dimension qualitative, offrant une meilleure compréhension de la satisfaction client.  
Les dashboards interactifs permettent une analyse multi-niveaux (globale, manager, individuel) et facilitent l’identification des tendances et leviers de performance.  
Ce projet démontre ainsi la capacité à concevoir un modèle analytique complet, robuste et orienté prise de décision. 


**Idriss FEKARI** 
