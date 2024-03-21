# YNOV-NOSQL-REDIS

## Projet WebApp - Paradigme Procédural Fonctionnel avec une Base de donnée NoSql <=> MySql

### 1. Spécification du projet :

#### 1.1 Sujet de Préférence
   1. Gestion d'Utilisateurs

#### 1.2 Technologies Utilisées
   1. HTML, CSS, JavaScript, PHP, Redis, MySQL (CRUD complet)

#### 1.3 Création du Repo GitHub :
   1. Établissement d'un repository sur GitHub pour le versionnement du projet.

#### 1.4 User Story/UseCase Textuel : Système de Gestion d'Utilisateurs
   1. Champs utilisateur :
      - id (AI)
      - nom
      - prenom
      - adresse
      - email
      - password
   2. Inscription obligatoire pour la connexion via email.
   3. Connexion réussie redirige vers la page dashboard.
   4. Échec de connexion redirige vers la page de login.
   5. Vérification de l'existence de l'email lors de l'inscription. Enregistrement si non existant, sinon affichage d'un message d'erreur.
   6. Un utilisateur peut voir ses informations sur son dashboard.
   7. Il peut modifier son nom, prénom, email.
   8. Possibilité de clôturer ou supprimer son compte.

#### 1.5 Sécurité
   1. Intégration de mesures de sécurité contre :
      - XSS (Cross-Site Scripting)
      - Injection SQL Try-catch et prepare statements
      - CSRF (Cross-Site Request Forgery)
      - Vérification de la complexité du mot de passe lors de l'inscription
      - Hashage de mot de passe et un Salt serait un bon point en plus
      - utilisation de regex

#### 1.6 Dossiers du Projet sur GitHub
    1. **src/**  
       - Code source de l'application.
    2. **readme.md**
       - Documentation
    3. **tests/**
      - Tests unitaires et fonctionnels, y compris les tests de sécurité avec PHPUnit.

**Organisation et structure des dossiers:**
```plaintext
|-- index.php (point d'entrée de l'application)
|-- controller.php (gère les requêtes, agissant comme contrôleur de votre application)
|-- model.php (Communique avec redis et persiste les données en BDD Mysql)
|-- login.php
|-- register.php
|-- dashboard.php
|-- header.php
|-- footer.php
|-- assets
|   |-- css
|       |-- style.css
|   |-- js
|       |-- main.js
|   |-- fonts
|       |-- UneTypoGoogleDeVotreChoix.ttf
|   |-- img
|       |-- logo.png
```

1. **Création de la Table dans MySQL :**
   - Utilisation de la requête SQL pour créer la table dans la base de données.

     ```sql
     CREATE TABLE utilisateurs (
         id INT AUTO_INCREMENT PRIMARY KEY,
         nom VARCHAR(50) NOT NULL,
         prenom VARCHAR(50) NOT NULL,
         adresse VARCHAR(10) NOT NULL
         email VARCHAR(100) NOT NULL,
         password VARCHAR(255) NOT NULL,
     );
     ```
2. `controller.php` : gère les requêtes, dirige le flux de contrôle vers la route appropriée définie dans la fonction controller().
   
3. `model.php` : Gestion de la persistance des données, interactions avec la base de données.


### 2. Rendu du projet

#### 2.1 Documentation (Readme.md) :
   1. Documentez votre projet dans le `readme.md` de votre repo selon la méthode suivante:

      - **Description Technique**
         - Présentation des technologies utilisées.

      - **Description Fonctionnelle**
         - Explication des fonctionnalités de l'application.

      - **Diagrammes**
         - **Diagramme UML :** (à faire avec Draw.io ou autres..)
            - Use Case
            - Diagramme d'Activité d'un utilistauer connecté
            - Diagramme de séquence
            - Diagramme de Classe (si orienté objet)
            - MPD de votre base de donnée MySql

         1. **Documentation :**<br>
            a. [Diagramme UseCase](https://www.lucidchart.com/pages/uml-use-case-diagram)<br>
            b. [Diagramme d'activité](https://www.lucidchart.com/pages/fr/diagramme-dactivite-uml)<br>
            c. [Diagramme de flux (Système)](https://www.lucidchart.com/pages/fr/diagramme-de-flux-de-donnees)<br>
            d. [Diagramme de séquence](https://www.lucidchart.com/pages/fr/diagramme-de-sequence-uml)<br>
            e. [Diagramme MPD](https://www.edrawsoft.com/fr/what-is-entity-relationship-diagram-erd.html)<br>

         
#### 2.2 Demo
   1. Démonstration de l'application.


**RETOUR SUR LE FONCTIONNEMENT D'UN CRUD REDIS**

## FONCTIONNEMENT D'UN CRUD REDIS <=> MYSQL ##

![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/8bab5127-2ab7-4418-b279-37acfef96100)
Dans un contexte de CRUD (Create, Read, Update, Delete), l'utilisation d'un cache Redis entre un utilisateur, une application, la base de données, et le cache Redis peut améliorer les performances et l'efficacité du système. Voici comment cela fonctionne :

1. **Lecture (Read) :**
   - Lorsqu'un utilisateur effectue une requête de lecture, l'application vérifie d'abord si les données demandées sont présentes dans le cache Redis.
   - Si les données sont présentes dans le cache, l'application les récupère directement depuis Redis sans interroger la base de données, ce qui réduit le temps de réponse.
   - Si les données ne sont pas présentes dans le cache, l'application va interroger la base de données, récupérer les données, les stocker dans le cache Redis pour les prochaines requêtes, puis les renvoyer à l'utilisateur.

2. **Écriture (Create/Update/Delete) :**
   - Lorsqu'un utilisateur effectue une opération d'écriture (création, mise à jour, suppression), l'application effectue d'abord l'opération sur la base de données.
   - Ensuite, l'application met à jour le cache Redis en conséquence pour maintenir la cohérence entre le cache et la base de données.
   - Cette mise à jour du cache peut impliquer la suppression des données obsolètes, la mise à jour des données existantes, ou l'ajout de nouvelles données.

3. **Explication des Avantages :**
   - **Réduction de la Charge sur la Base de Données :** En utilisant le cache Redis pour les opérations de lecture, la charge sur la base de données est réduite, car les requêtes fréquemment demandées sont satisfaites par le cache.
   - **Amélioration des Performances :** Les données en cache sont souvent plus rapides à récupérer que celles provenant d'une base de données, ce qui améliore les performances globales de l'application.
   - **Réduction de la Latence :** La latence est réduite car le cache permet de fournir des données plus rapidement, surtout pour les requêtes de lecture.

4. **Gestion du Cache Redis :**
   - La durée pendant laquelle les données sont stockées dans le cache (TTL - Time To Live) est généralement configurée en fonction des besoins de l'application.
   - Les stratégies d'éviction peuvent être mises en place pour gérer l'espace du cache et éliminer les données obsolètes lorsque la capacité maximale est atteinte.

5. **Considérations de Sécurité :**
   - Il est crucial de mettre en place des mécanismes de gestion des droits d'accès pour s'assurer que seules les données appropriées sont mises en cache.
   - La sécurité du cache Redis, y compris la gestion des autorisations et la désactivation des fonctionnalités potentiellement dangereuses, doit être configurée de manière appropriée.

  
