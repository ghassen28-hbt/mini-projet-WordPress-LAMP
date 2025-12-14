# mini-projet-WordPress-LAMP
Déploiement WordPress avec Docker et Docker Compose (Architecture LAMP)

# 🐳 Mini‑Projet : Déploiement WordPress avec Docker (Architecture LAMP)

##  Objectif du projet

L’objectif de ce mini‑projet est de créer une **plateforme de déploiement automatisée de WordPress** en utilisant **Docker** et **Docker Compose**, basée sur l’architecture **LAMP** :

* **Linux** (conteneurs Docker)
* **Apache2** (serveur web)
* **MySQL / MariaDB** (base de données)
* **PHP 8.x**

Le projet met en œuvre :

* Des **conteneurs Docker**
* Un **réseau Docker dédié**
* Des **volumes Docker** pour assurer la persistance des données

---

##  Architecture du projet

```
Navigateur
    ↓
[ WordPress + Apache + PHP ]  ←→  [ MariaDB ]
            (conteneurs Docker)
                ↓
        Réseau Docker privé
                ↓
        Volume Docker (DB)
```

* WordPress et MariaDB sont isolés dans **deux conteneurs distincts**
* Les conteneurs communiquent via un **réseau Docker privé**
* Les données de la base sont stockées dans un **volume persistant**

---

##  Structure du projet

```
mini-projet-WordPress-LAMP/
│
├── docker-compose.yml
├── wordpress/
│   └── Dockerfile
├── db/
│   └── Dockerfile
└── README.md
```

---

##  1. Configuration de l’environnement Docker

###  Installation des outils

* Docker
* Docker Compose

###  Réseau Docker

Un réseau Docker dédié est créé automatiquement par Docker Compose afin de permettre la communication interne entre les conteneurs.

###  Volume Docker

Un volume Docker est utilisé pour stocker les données de MariaDB afin de garantir la **persistance des données** même après l’arrêt ou la suppression des conteneurs.

---

##  2. Déploiement du serveur Web (Apache + PHP)

* Utilisation de l’image officielle **WordPress avec Apache et PHP 8.x**
* Apache sert les fichiers PHP de WordPress
* Le conteneur WordPress est connecté au réseau Docker dédié

---

##  3. Configuration de la base de données (MariaDB)

* Déploiement d’un conteneur **MariaDB**
* Configuration automatique via variables d’environnement :

  * Nom de la base de données
  * Utilisateur
  * Mot de passe
* Les données sont stockées dans un **volume Docker persistant**
* Le conteneur est connecté au réseau Docker dédié

---

##  4. Déploiement de WordPress

* Déploiement de WordPress via Docker Compose
* Connexion automatique à la base de données MariaDB
* Génération automatique du fichier `wp-config.php`
* Accès à l’interface WordPress via le navigateur

URL d’accès :

```
http://localhost:8080
```

---

##  5. Tests et validation

### Test de fonctionnement

* Accès à WordPress depuis le navigateur
* Connexion à l’interface d’administration

###  Test de persistance des données

1. Création d’un article nommé :
   **"Test de persistance"**
2. Arrêt des conteneurs :

   ```bash
   docker compose down
   ```
3. Redémarrage des conteneurs :

   ```bash
   docker compose up -d
   ```
4. Vérification que l’article existe toujours

 Résultat : les données sont bien conservées grâce au volume Docker.

---

##  Lancement du projet

```bash
docker compose up -d
```

Pour arrêter les conteneurs :

```bash
docker compose down
```

---

##  Conclusion

Ce projet démontre l’utilisation efficace de Docker et Docker Compose pour déployer une application WordPress robuste, modulaire et persistante. L’architecture LAMP est respectée tout en bénéficiant des avantages de la conteneurisation : isolation, portabilité et automatisation.

---

##  Réalisé par

**Ghassen Mbarki**
Licence Informatique de Gestion @ ISGT


