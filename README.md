# TP SISR : Déploiement de WordPress et Zabbix avec Docker sur Debian 12

Ce projet guide l'installation et la configuration d'une VM minimaliste sous Debian 12 pour déployer WordPress et Zabbix en utilisant Docker et Docker Compose.

## Prérequis

- **VM sous Debian 12** (idéalement hébergée sur Proxmox)
- **Accès à un terminal Bash**
- **Connexion internet** (pour télécharger Docker, Docker Compose, et les images des conteneurs)
- **Git** installé pour cloner ce projet depuis GitHub

## Contenu

Ce repository contient les fichiers suivants :
- `install_docker.sh` : script d'installation de Docker et Docker Compose.
- `docker-compose.yml` : fichier de configuration pour déployer WordPress et Zabbix en conteneurs Docker.
- `README.md` : ce fichier de documentation.

## Étapes d'installation et d'utilisation

### 1. Cloner le Projet 

Commencez par cloner ce repository GitHub dans votre VM :
```bash
git clone https://github.com/ton_username/ton_repository.git
cd ton_repository
```

### 2. Exécuter le Script install_docker.sh

Ce script installe Docker et Docker Compose. Avant de l'exécuter, assurez-vous qu'il est exécutable :

```bash
chmod +x install_docker.sh
./install_docker.sh
```

Le script install_docker.sh commence par mettre à jour la liste des paquets et installe les dépendances nécessaires pour Docker.
Il ajoute ensuite la clé GPG et le dépôt Docker officiel.
Enfin, il installe Docker et Docker Compose et vérifie leur version pour s'assurer de leur bonne installation.
Vérification : Après l'exécution du script, vérifiez que Docker et Docker Compose sont installés correctement avec :

```bash
Copier le code
docker --version
docker compose version
```

### 3. Déployer WordPress et Zabbix avec Docker Compose

Le fichier docker-compose.yml contient les configurations pour déployer WordPress et Zabbix, ainsi que leurs bases de données respectives (MySQL).

Pour lancer les conteneurs, exécutez :

```bash
docker compose up -d
```

Explication du Fichier docker-compose.yml :

Voici une description détaillée de chaque service défini dans docker-compose.yml :

Service wordpress :

Utilise l'image wordpress:latest officielle.
Se connecte à la base de données MySQL du service db (défini ci-dessous).
Expose le port 8080 pour permettre l'accès à WordPress via http://localhost:8080.
Service db :

Utilise l'image mysql:5.7, compatible avec WordPress.
Initialise la base de données avec un nom d'utilisateur et un mot de passe.
Service zabbix-server :

Utilise l'image zabbix/zabbix-server-mysql:latest.
Configure une base de données Zabbix sur le service zabbix-db.
Expose le port 10051 pour le serveur Zabbix.
Service zabbix-db :

Utilise l'image mysql:5.7 pour stocker les données de Zabbix.

### 4. Accéder aux Services Déployés

Une fois les conteneurs lancés, vous pouvez accéder aux services comme suit :

WordPress : Accédez à WordPress en ouvrant un navigateur et en allant sur http://localhost:8080.
Zabbix : Le serveur Zabbix écoute sur le port 10051, et vous pouvez l'utiliser pour vos besoins de monitoring.
Note : Pour arrêter les services, exécutez :

```bash
docker compose down
```

Voici les étapes pour tester et vérifier que tout fonctionne correctement :

Vérifier l'installation de Docker et Docker Compose :
Exécutez docker --version et docker compose version pour confirmer leur installation.
Lancer les services et vérifier les logs :
Utilisez docker compose ps pour voir si tous les services sont en cours d'exécution.
Utilisez docker compose logs wordpress et docker compose logs zabbix-server pour afficher les logs des services et détecter tout éventuel problème.
Dépannage
Port occupé : Si 8080 ou 10051 sont déjà utilisés, vous pouvez modifier ces ports dans le fichier docker-compose.yml.
Erreur de connexion à la base de données : Assurez-vous que les identifiants de la base de données sont correctement configurés dans docker-compose.yml.

