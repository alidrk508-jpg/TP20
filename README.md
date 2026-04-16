# NumberBook - Android Application

**NumberBook** est une application Android permettant de gérer un répertoire de contacts synchronisé avec un serveur distant (MySQL via PHP). L'application offre une interface moderne en Material Design avec des fonctionnalités de recherche en temps réel et d'ajout direct.

<iframe width="560" height="315" 
src="https://www.youtube.com/embed/btxV5AWqPNM" 
title="YouTube video player" 
frameborder="0" 
allowfullscreen>
</iframe>

## 🚀 Fonctionnalités

- **Affichage en temps réel** : Liste des contacts récupérée depuis une base de données MySQL.
- **Ajout de Contact** : Formulaire via une boîte de dialogue pour insérer un nouveau contact (Nom et Téléphone) directement sur le serveur.
- **Synchronisation** : Bouton permettant d'importer les contacts physiques du téléphone vers le serveur distant.
- **Recherche Intelligente** : Barre de recherche filtrant les résultats instantanément au fur et à mesure de la saisie.
- **Design Moderne** : Utilisation de Material Design 3, CoordinatorLayout et Floating Action Buttons.

## 🛠 Technologies Utilisées

- **Langage** : Java
- **Réseau** : Retrofit 2.11.0 & GSON Converter (pour les appels API JSON)
- **UI** : RecyclerView, Material Design Components, CoordinatorLayout
- **Permissions** : Gestion dynamique des permissions (READ_CONTACTS)

## 📡 Configuration du Backend (API)

L'application communique avec une API PHP située sur un serveur local (XAMPP/WAMP).

### Structure de la base de données
```sql
CREATE TABLE contact (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(150) NOT NULL,
    phone VARCHAR(50) NOT NULL,
    source VARCHAR(50) DEFAULT 'mobile',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

### Endpoints API
L'URL de base configurée dans l'application pour l'émulateur est : `http://10.0.2.2/numberbook-api/api/`

- `getAllContacts.php` : Récupère la liste de tous les contacts (JSON).
- `insertContact.php` : Ajoute un nouveau contact (POST).
- `searchContact.php?keyword=...` : Recherche des contacts par nom ou numéro.

## ⚙️ Installation

1. Clonez le projet dans Android Studio.
2. Assurez-vous que votre serveur local (Apache/MySQL) est démarré.
3. Importez les fichiers PHP dans votre dossier `htdocs` ou `www`.
4. Dans le fichier `RetrofitClient.java`, vérifiez l'adresse IP :
   - Utilisez `10.0.2.2` pour l'émulateur Android Studio.
   - Utilisez l'adresse IP de votre PC (ex: `192.168.1.50`) si vous testez sur un vrai téléphone.
5. Synchronisez Gradle et lancez l'application.

## 🔒 Permissions
L'application requiert les permissions suivantes :
- `INTERNET` : Pour communiquer avec le serveur.
- `READ_CONTACTS` : Pour pouvoir importer les contacts du téléphone.

---
Développé dans le cadre d'un projet d'apprentissage Android.
