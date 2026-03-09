# Projet Data Engineering – Superstore

-----

## Contexte
Après avoir nettoyé et préparé un dataset fiable (`superstore_clean.csv`), l’entreprise souhaite structurer et centraliser les données dans une base relationnelle PostgreSQL afin de :  
- Gérer des volumes de données croissants  
- Garantir l’intégrité et la cohérence  
- Permettre des requêtes SQL performantes  
- Préparer la construction d’un dashboard interactif  

L’équipe Data doit concevoir un modèle relationnel cohérent, normaliser les données, créer les tables, charger les données via SQLAlchemy et vérifier l’intégrité des relations.  
Ce sprint introduit la logique Data Engineering de base : **modélisation → création des tables → chargement → requêtes SQL**.

-----

## Objectifs
- Concevoir un schéma relationnel normalisé  
- Séparer les entités : `Orders`, `Customers`, `Products`, `Categories`, `Regions`  
- Créer les tables avec **clés primaires** et **clés étrangères**  
- Charger les données nettoyées dans PostgreSQL  
- Écrire des requêtes SQL simples (`SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`)  
- Vérifier la cohérence et l’intégrité des données  
- Suivre l’avancement via Jira  

-----

## User Stories

### Point de vue Direction IT / Data
> « En tant que responsable Data, je veux une base bien structurée et normalisée afin de garantir la qualité des données et faciliter les futures analyses. »

**Attentes :**  
- Modèle relationnel clair  
- Clés primaires et étrangères correctes  
- Pas de redondance inutile  
- Intégrité référentielle respectée  

### Point de vue Analyste Business
> « En tant qu’analyste métier, je veux pouvoir interroger facilement la base pour obtenir des indicateurs par produit, région et client. »

**Exemples de requêtes attendues :**  
- Ventes totales par catégorie  
- Profit par région  
- Top clients par chiffre d’affaires  
- Nombre de commandes par mois  

-----

## Technologies & Ressources
- Dataset : `superstore_clean.csv`  
- Python 3.x, **SQLAlchemy**, `psycopg2`  
- Base de données : **PostgreSQL**  
- IDE : **Jupyter Notebook / VS Code**  
- Suivi de projet : **Jira**

-----

## Étapes du projet

### 1️⃣ Création de la base et connexion
- Création de la base PostgreSQL : `superstore_db`  
- Configuration de la connexion Python → PostgreSQL via SQLAlchemy  

### 2️⃣ Conception du modèle relationnel
- Identification des entités principales : `Orders`, `Customers`, `Products`, `Categories`, `Regions`  
- Création des tables correspondantes avec **primary keys** et **foreign keys**  
- Application des règles de normalisation (1NF, 2NF, 3NF)  

### 3️⃣ Chargement des données
- Séparation du dataset CSV selon les tables normalisées  
- Insertion des données dans PostgreSQL via SQLAlchemy  
- Vérification de l’intégrité des données après insertion  

### 4️⃣ Transformations complémentaires
- Calcul de métriques directement dans la base :  
  - Total Sales par produit, catégorie, région  
  - Profit moyen par commande ou client  
- Création de vues pour analyses rapides  

### 5️⃣ Préparation pour la visualisation
- Vérification que toutes les données nécessaires pour le dashboard sont disponibles  
- Vérification des relations et clés pour permettre des jointures simples  

-----

## Modèle conceptuel simplifié

```text
Customers --< Orders >-- Products >-- Categories
         \
          >-- Regions
