# YNOV-NOSQL-REDIS

## Projet WebApp - Paradigme Procédural Fonctionnel

### 1. Spécification du projet :

#### 1.1 Sujet de Préférence
   1. Gestion d'Utilisateurs

#### 1.2 Technologies Utilisées
   1. HTML, CSS, JavaScript, PHP, Redis, MySQL (CRUD complet)

#### 1.3 Création du Repo GitHub :
   1. Établissement d'un repository sur GitHub pour le versionnement du projet.

#### 1.4 User Story : Système de Gestion d'Utilisateurs
   1. Champs utilisateur :
      - id (AI)
      - nom
      - prenom
      - Adresse
      - Role (Input hidden, valeur défini à 2 pour chaque nouvel inscrit)
      - email
      - password
   2. Inscription obligatoire pour la connexion via email.
   3. Connexion réussie redirige vers la page profil.
   4. Échec de connexion redirige vers la page de login.
   5. Vérification de l'existence de l'email lors de l'inscription. Enregistrement si non existant, sinon affichage d'un message d'erreur.
   6. Un utilisateur peut voir ses informations sur son profil.
   7. Il peut modifier son nom, prénom, email, ou le mot de passe.
   8. Possibilité de clôturer ou supprimer son compte.

#### 1.5 Sécurité
   1. Intégration de mesures de sécurité contre :
      - XSS (Cross-Site Scripting)
      - Injection SQL
      - CSRF (Cross-Site Request Forgery)
      - Vérification de la complexité du mot de passe lors de l'inscription
      - Hashage de mot de passe et un Salt serait un bon point en plus

#### 1.6 Dossiers du Projet sur GitHub
    1. **src/**       
      - Code source de l'application.
    2. **tests/**
      - Tests unitaires et fonctionnels, y compris les tests de sécurité avec PHPUnit.

**Organisation et structure des dossiers:**
```plaintext
|-- index.php (point d'entrée de l'application)
|-- /functions (dossier des fonctions gérant le backend et la couche de persistance des données)
|-- requestHandler.php (gère les requêtes, agissant implicitement comme contrôleur de votre application)
|-- /templates (frontend de l'application, les vues)
|   |-- home.php
|   |-- login.php
|   |-- register.php
|   |-- profil.php ou dashboard.php
|   |-- parts
|       |-- header.php
|       |-- footer.php
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
         role VARCHAR(50) NOT NULL
     );
     ```
2. `request_handler.php` : appelle la fonction `controller.php` et gère les requêtes, dirige le flux de contrôle vers le contrôleur approprié.

3. **Fichiers dans le Dossier "functions":**

   a. `functions/controller.php` : fonction agissant en tant que routeur/contrôleur.
   
   b. `functions/model.php` : Gestion de la persistance des données, interactions avec la base de données.

   c. `templates` : Partie front (vues) de votre projet.

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
            - Diagramme d'Activité
            - Diagramme de Classe (si orienté objet)
         - **Diagramme de flux, du fonctionnement du système :**
            - ![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/552e2f4c-e96d-4ba1-b457-19096c2abda8)

         - **Exemples de diagrammes :**
            - [Liens vers les exemples](https://github.com/yugmerabtene/ESIEA-FISE-WEB-2024/blob/main/Module-04/TP-01.md)

         
#### 2.2 Demo
   1. Démonstration de l'application.

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
