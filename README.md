# YNOV-NOSQL-REDIS

## Projet WebApp - Paradigme Procédural Fonctionnel

### 1. Spécification du projet :

#### 1.1 Sujet de Préférence
   - Système de Gestion d'Utilisateurs

#### 1.2 Technologies Utilisées
   - Technologies : HTML, CSS, JavaScript, PHP, Redis, MySQL (CRUD complet)

#### 1.3 Création du Repo GitHub :
   - Mettez en place un repository sur GitHub pour versionner le projet.

#### 1.4 User Story : Système de Gestion d'Utilisateurs
   - Champs utilisateur :
      - ID (AI)
      - Nom
      - Prénom
      - Email
      - Mot de passe
   - Inscription obligatoire pour se connecter via email.
   - Connexion réussie redirige vers la page profil.
   - Échec de connexion redirige vers la page de login.
   - Vérification de l'existence de l'email lors de l'inscription. Enregistrement si non existant, sinon affichage d'un message d'erreur.
   - Un utilisateur peut voir ses informations sur son profil.
   - Il peut modifier son nom, prénom, email, ou le mot de passe.
   - Possibilité de clôturer ou supprimer son compte.

#### 1.5 Sécurité
   - Intégrez des mesures de sécurité contre :
      - XSS (Cross-Site Scripting)
      - Injection SQL
      - CSRF (Cross-Site Request Forgery)

#### 1.6 Dossiers du Projet
    - **src/**
      - Code source de l'application.
    - **tests/**
      - Tests unitaires et fonctionnels, y compris les tests de sécurité avec PHPUnit.

### 2. Rendu du projet

#### 2.1 Documentation (Readme.md) :
   - Documentez votre projet dans le readme.md de votre repo selon la méthode suivante:

      - **Description Technique**
         - Présentation des technologies utilisées.

      - **Description Fonctionnelle**
         - Explication des fonctionnalités de l'application.

      - **Diagrammes**
         - **Diagramme UML :**
            - Use Case
            - Diagramme d'Activité
            - Diagramme de Classe (si orienté objet)
         - **Exemples de diagrammes :**
            - [Liens vers les exemples](https://github.com/yugmerabtene/ESIEA-FISE-WEB-2024/blob/main/Module-04/TP-01.md)

#### 2.2 Demo
   - Démonstration de l'application.
