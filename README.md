# city-project-infra

# Contexte

L'installation a été testée sur une machine physique, Debian 12 avec Nginx et Docker.

# Installation

## Docker Compose

### Base de données

Bientôt...

### Serveur

Le serveur contient le système d'authentification et la partie responsable de tous les calculs du jeu.

```
cd ./server/

docker compose up -d
```

### Client

Le client contient les fichiers du jeu (textures, sons, etc...) et toute l'interface en jeu (inventaire, menus, connexion, etc...). Il est aussi responsable de rendre la partie graphique.

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
