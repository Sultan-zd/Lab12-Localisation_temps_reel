# 📍 Localisation Temps Réel (GPS & Google Maps)

Bienvenue dans le dépôt du **Lab 12 : Localisation Temps Réel**. 
Ce projet complet illustre comment récupérer les coordonnées GPS d'un appareil Android, les envoyer à un serveur PHP/MySQL via une API REST, et afficher ces positions en temps réel sur une carte Google Maps intégrée à l'application.

---

## 🏗️ Architecture du Projet

Le projet est divisé en trois grandes parties :

1. **Base de données (`database/`)** : Script SQL pour la création de la table `position`.
2. **Backend Serveur (`server/localisation/`)** : API en PHP utilisant PDO pour l'insertion et la récupération des coordonnées GPS.
3. **Application Android (`android/`)** : Code source de l'application mobile (Java, XML) gérant la géolocalisation, l'appel API via Volley, et l'affichage Maps.

---

## 🚀 Prérequis

- **Serveur Web Local** : XAMPP, WAMP ou LAMP avec PHP et MySQL activés.
- **IDE Android** : Android Studio avec un émulateur (avec Google Play Services) ou un smartphone physique (GPS et Débogage USB activés).
- **Réseau** : Le téléphone/émulateur et le PC hébergeant le serveur doivent impérativement être connectés au **même réseau Wi-Fi** (ou hotspot).
- **Clé API Google Maps** : Une clé Google Maps Android API valide.

---

## 🛠️ Installation et Configuration

### 1. Base de données (MySQL)
1. Ouvrez phpMyAdmin (ex: `http://localhost/phpmyadmin`).
2. Créez une nouvelle base de données nommée **`localisation`**.
3. Importez le fichier `database/schema.sql` fourni dans ce dépôt, ou exécutez la requête SQL présente dans ce fichier pour créer la table `position`.

### 2. Backend PHP
1. Copiez le dossier `server/localisation/` dans la racine de votre serveur web (ex: `C:\xampp\htdocs\` pour XAMPP ou `C:\wamp64\www\` pour WAMP).
2. Vérifiez la connexion à la base de données dans le fichier `localisation/connexion/Connexion.php`. Modifiez les identifiants si votre configuration MySQL est différente (`root` et mot de passe vide par défaut).
3. Vous pouvez tester l'API de lecture en accédant à l'URL : `http://localhost/localisation/showPositions.php` via votre navigateur ou Postman.

### 3. Application Android
1. Ouvrez **Android Studio** et créez un projet "Empty Activity" nommé `Localisation`.
2. Remplacez ou intégrez les fichiers sources fournis dans le dossier `android/` de ce dépôt vers les répertoires correspondants de votre projet Android Studio.
3. **Configuration Réseau (Important) :** 
   Dans `MainActivity.java` et `MapsActivity.java`, modifiez les variables `insertUrl` et `showUrl` en remplaçant `192.168.43.228` par **l'adresse IP locale de votre PC** (utilisez `ipconfig` dans l'invite de commande sous Windows).
4. **Clé Google Maps :**
   Créez une activité de type *Google Maps Activity* dans votre projet. Ajoutez votre clé d'API Google Maps dans le fichier généré `google_maps_api.xml`.
5. Compilez et lancez l'application sur votre appareil !

---

## 📱 Fonctionnalités

- 📡 **Tracking GPS** : Récupération des coordonnées (Latitude, Longitude, Altitude, Précision) à intervalle régulier.
- 🌐 **Communication Réseau** : Utilisation de la bibliothèque **Volley** pour envoyer les données au format POST vers l'API PHP.
- 💾 **Persistance** : Sauvegarde de chaque point dans la base MySQL (incluant l'identifiant IMEI/DeviceID).
- 🗺️ **Cartographie** : Récupération asynchrone des données en JSON et placement dynamique de *Markers* sur une instance Google Map.

---

## 📜 Technologies Utilisées

- **Android** : Java, Android SDK, Volley, Google Play Services Maps.
- **Backend** : PHP 7/8+, Programmation Orientée Objet (POO), PDO, Architecture DAO/Service.
- **Base de données** : MySQL.

---

*Projet réalisé dans le cadre d'un laboratoire académique sur le développement mobile et les services web.*
