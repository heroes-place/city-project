# city-project-infra

# Contexte

L'installation a été testée sur une machine physique, Debian 12 avec Nginx et Docker.

# Installation

## Docker Compose

```
version: '3'

services:
  city-project-server:
    image: ghcr.io/devsoleo/city-project-server:main
    container_name: city-project-server
    ports:
      - 3000:3000
    environment:
      - NODE_ENV=production
      - CLIENT_ADDRESS=domain.fr
      - PGHOST=192.168.1.*
      - PGUSER=postgres
      - PGPASSWORD=password
      - REDIS_HOST=192.168.1.*
    volumes:
      - ./config/:/usr/src/app/config/

  city-project-client:
    image: ghcr.io/devsoleo/city-project-client:main
    container_name: city-project-client
    ports:
      - 3001:80
```

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
