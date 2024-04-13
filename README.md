# city-project-infra

# Contexte

L'installation a été testée sur une machine physique, Debian 12 avec Nginx et Docker.

# Installation

## Docker Compose

### Base de données

Bientôt...

### Serveur

Le serveur contient les fichiers du jeu (textures, sons, etc...), le système d'authentification et la partie responsable de tous les calculs du jeu.

Le jeu étant au format web, les fichiers du jeu sont hébergés en ligne, et non en local.

```
cd ./server/

docker compose up -d
```

### Client

Le client contient toute l'interface en jeu (inventaire, menus, connexion, etc...).

Il est aussi responsable de générer la partie graphique du jeu à partir des fichiers fournis par le serveur.

```
cd ./client/

docker compose up -d
```

## Nginx

Installer la configuration Nginx fournie dans ce repo.

```
mv ./nginx/default /etc/nginx/sites-available/default
```

## Certbot

Installer les 2 certificats :

```
certbot --nginx
```