# Projet YNOV-NOSQL-REDIS

## 1. Spécification du Projet :

### 1.1 Sujet de Préférence
   1. Gestion d'Utilisateurs

### 1.2 Technologies Utilisées
   1. HTML, CSS, JavaScript, PHP, Redis, MySQL (CRUD complet)

### 1.3 Création du Repo GitHub :
   1. Établissement d'un repository sur GitHub pour le versionnement du projet.

### 1.4 User Story : Système de Gestion d'Utilisateurs
   1. Champs utilisateur :
      - 1.4.1 id (AI)
      - 1.4.2 nom
      - 1.4.3 prenom
      - 1.4.4 Adresse
      - 1.4.5 Role (Input hidden, valeur définie à 2 pour chaque nouvel inscrit)
      - 1.4.6 email
      - 1.4.7 password
   2. Inscription obligatoire pour la connexion via email.
   3. Connexion réussie redirige vers la page profil.
   4. Échec de connexion redirige vers la page de login.
   5. Vérification de l'existence de l'email lors de l'inscription. Enregistrement si non existant, sinon affichage d'un message d'erreur.
   6. Un utilisateur peut voir ses informations sur son profil.
   7. Il peut modifier son nom, prénom, email, ou le mot de passe.
   8. Possibilité de clôturer ou supprimer son compte.

### 1.5 Sécurité
   1. Intégration de mesures de sécurité contre :
      - 1.5.1 XSS (Cross-Site Scripting)
      - 1.5.2 Injection SQL
      - 1.5.3 CSRF (Cross-Site Request Forgery)
      - 1.5.4 Vérification de la complexité du mot de passe lors de l'inscription
      - 1.5.5 Hashage de mot de passe et un Salt serait un
