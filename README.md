# Projet YNOV-NOSQL-REDIS

## 1. Spécification du Projet :

### 1.1 Sujet de Préférence
   1. Gestion d'Utilisateurs

### 1.2 Technologies Utilisées
   1. HTML, CSS, JavaScript, PHP, Redis, MySQL (CRUD complet)

### 1.3 Création du Repo GitHub :
   1.1 Établissement d'un repository sur GitHub pour le versionnement du projet.

### 1.4 User Story : Système de Gestion d'Utilisateurs
   1.1 Champs utilisateur :
      - 1.4.1 id (AI)
      - 1.4.2 nom
      - 1.4.3 prenom
      - 1.4.4 Adresse
      - 1.4.5 Role (Input hidden, valeur définie à 2 pour chaque nouvel inscrit)
      - 1.4.6 email
      - 1.4.7 password
   1.2 Inscription obligatoire pour la connexion via email.
   1.3 Connexion réussie redirige vers la page profil.
   1.4 Échec de connexion redirige vers la page de login.
   1.5 Vérification de l'existence de l'email lors de l'inscription. Enregistrement si non existant, sinon affichage d'un message d'erreur.
   1.6 Un utilisateur peut voir ses informations sur son profil.
   1.7 Il peut modifier son nom, prénom, email, ou le mot de passe.
   1.8 Possibilité de clôturer ou supprimer son compte.

### 1.5 Sécurité
   1.1 Intégration de mesures de sécurité contre :
      - 1.5.1 XSS (Cross-Site Scripting)
      - 1.5.2 Injection SQL
      - 1.5.3 CSRF (Cross-Site Request Forgery)
      - 1.5.4 Vérification de la complexité du mot de passe lors de l'inscription
      - 1.5.5 Hashage de mot de passe et un Salt serait un bon point en plus

### 1.6 Dossiers du Projet sur GitHub
   1.1 **src/**       
      - Code source de l'application.
   1.2 **tests/**
      - Tests unitaires et fonctionnels, y compris les tests de sécurité avec PHPUnit.

**Organisation et structure des dossiers:**
```plaintext
|-- 1.6.1 index.php (point d'entrée de l'application)
|-- 1.6.2 /functions (dossier des fonctions gérant le backend et la couche de persistance des données)
|-- 1.6.3 requestHandler.php (gère les requêtes, agissant implicitement comme contrôleur de votre application)
|-- 1.6.4 /templates (frontend de l'application, les vues)
|   |-- 1.6.4.1 parts
|       |-- 1.6.4.1.1 header.php
|       |-- 1.6.4.1.2 footer.php
|-- 1.6.5 assets
|   |-- 1.6.5.1 css
|       |-- 1.6.5.1.1 style.css
|   |-- 1.6.5.2 js
|       |-- 1.6.5.2.1 main.js
|   |-- 1.6.5.3 fonts
|       |-- 1.6.5.3.1 UneTypoGoogleDeVotreChoix.ttf
|   |-- 1.6.5.4 img
|       |-- 1.6.5.4.1 logo.png
```

1.6.6 **Création de la Table dans MySQL :**
   - Utilisation de la requête SQL pour créer la table dans la base de données.

     ```sql
     CREATE TABLE utilisateurs (
         id INT AUTO_INCREMENT PRIMARY KEY,
         nom VARCHAR(50) NOT NULL,
         prenom VARCHAR(50) NOT NULL,
         adresse VARCHAR(10) NOT NULL
         adresse_mail VARCHAR(100) NOT NULL,
         mot_de_passe VARCHAR(255) NOT NULL,
         role VARCHAR(50) NOT NULL
     );
     ```

1.6.7 `request_handler.php` : appelle la fonction `controller.php` et gère les requêtes, dirige le flux de contrôle vers le contrôleur approprié.

1.6.8 **Fichiers dans le Dossier "functions":**

   a. 1.6.8.1 `functions/controller.php` : fonction agissant en tant que routeur/contrôleur.
   
   b. 1.6.8.2 `functions/model.php` : Gestion de la persistance des données, interactions avec la base de données.

   c. 1.6.8.3 `templates` : Partie front (vues) de votre projet.

## 2. Rendu du Projet

### 2.1 Documentation (Readme.md) :
   1. Documentez votre projet dans le `readme.md` de votre repo selon la méthode suivante:

      - 2.1.1 **Description Technique**
         - Présentation des technologies utilisées.

      - 2.1.2 **Description Fonctionnelle**
         - Explication des fonctionnalités de l'application.

      - 2.1.3 **Diagrammes**
         - 2.1.3.1 **Diagramme UML :** (à faire avec Draw.io ou autres..)
            - Use Case
            - Diagramme d'Activité
            - Diagramme de Classe (si orienté objet)
         - 2.1.3.2 **Diagramme de flux, du fonctionnement du système :**
            - ![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/552e2f4c-e96d-4ba1-b457-19096c2abda8)

         - 2.1.3.3 **Exemples de diagrammes :**
            - [Liens vers les exemples](https://github.com/yugmerabtene/ESIEA-FISE-WEB-2024/blob/main/Module-04/TP-01.md)

         
### 2.2 Demo
   1. Démonstration de l'application.

## 3. FONCTIONNEMENT D'UN CRUD REDIS <=> MYSQL ##

![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/8bab5127-2ab7-4418-b279-37acfef96100)

Dans un contexte de CRUD (Create, Read, Update, Delete), l'utilisation d'un cache Redis entre un utilisateur, une application, la base de données, et le cache Redis peut

 améliorer les performances et l'efficacité du système. Voici comment cela fonctionne :

3.1 **Lecture (Read) :**
   - Lorsqu'un utilisateur effectue une requête de lecture, l'application vérifie d'abord si les données demandées sont présentes dans le cache Redis.
   - Si les données sont présentes dans le cache, l'application les récupère directement depuis Redis sans interroger la base de données, ce qui réduit le temps de réponse.
   - Si les données ne sont pas présentes dans le cache, l'application va interroger la base de données, récupérer les données, les stocker dans le cache Redis pour les prochaines requêtes, puis les renvoyer à l'utilisateur.

3.2 **Écriture (Create/Update/Delete) :**
   - Lorsqu'un utilisateur effectue une opération d'écriture (création, mise à jour, suppression), l'application effectue d'abord l'opération sur la base de données.
   - Ensuite, l'application met à jour le cache Redis en conséquence pour maintenir la cohérence entre le cache et la base de données.
   - Cette mise à jour du cache peut impliquer la suppression des données obsolètes, la

