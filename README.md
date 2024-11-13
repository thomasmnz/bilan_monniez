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


