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
      - Hashage de mot de passe et un Salt serai un bon point en plus

#### 1.6 Dossiers du Projet sur github
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
         adresse_mail VARCHAR(100) NOT NULL,
         mot_de_passe VARCHAR(255) NOT NULL,
         role VARCHAR(50) NOT NULL
     );
     ```
2. `request_handler.php` : appelle la fonction controller.php et gère les requêtes, dirige le flux de contrôle vers le contrôleur approprié.

3. **Fichiers dans le Dossier "functions":**

   a. `functions/controller.php` : fonction agissant en tant que routeur/contrôleur.
   
   b. `functions/model.php` : Gestion de la persistance des données, interactions avec la base de données.

   c. `templates` : Partie front (vues) de votre projet.



### 2. Rendu du projet

#### 2.1 Documentation (Readme.md) :
   1. Documentez votre projet dans le readme.md de votre repo selon la méthode suivante:

      - **Description Technique**
         - Présentation des technologies utilisées.

      - **Description Fonctionnelle**
         - Explication des fonctionnalités de l'application.

      - **Diagrammes**
         - **Diagramme UML :**
            - Use Case
            - Diagramme d'Activité
            - Diagramme de Classe (si orienté objet)
         - **Diagramme de flux, du fonctionnement du système :**
            - ![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/552e2f4c-e96d-4ba1-b457-19096c2abda8)

         - **Exemples de diagrammes :**
            - [Liens vers les exemples](https://github.com/yugmerabtene/ESIEA-FISE-WEB-2024/blob/main/Module-04/TP-01.md)

         
#### 2.2 Demo
   1. Démonstration de l'application.


##FONCTIONNEMENT D'UN CRUD REDIS <=> MYSQL##

![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/5b8a3a48-e269-4f3e-b3fe-0686215ea01d)
![image](https://github.com/yugmerabtene/YNOV-B3-REDIS-2024/assets/3670077/8bab5127-2ab7-4418-b279-37acfef96100)


