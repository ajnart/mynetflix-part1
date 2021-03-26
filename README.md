![](assets/mynetflix.png)

# Workshop My Netflix part. 1

*Ce workshop a pour but de vous familiariser avec Docker et Portainer en mettant en place un serveur Plex pour pouvoir visionner des medias téléchargés au préalable grâce à un Docker transmission.*

**N'hésitez pas à star ⭐ le repo si vous avez aimé ce workshop!** ![](https://img.shields.io/github/stars/ajnart/mynetflix-part1?label=%E2%AD%90&style=for-the-badge?branch=master&kill_cache=1")

Ce workshop est divisé en deux parties. La première concerne l'installation 

## Partie 1 : Portainer et Plex
### 1 - Portainer
<img src="assets/portainerlogo.png" width="562" height="230">

**Portainer** est un outil de gestion de conteneur Docker et/ou de Kubernetes. Nous allons l'utiliser pour gérer les conteneurs que nous allons créer dans le futur.

Tout d'abord, installez portainer en suivant le [portainer quick start](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)

Ensuite, rendez vous [localhost:9000](http://localhost:9000) (ou le port que vous avez spécifié.)

Choisissez un mot de passe administrateur et sélectionnez l'utilisation **locale**.

✨ **Voilà !** ✨Vous avez maintenant une installation fonctionelle de portainer. 🐋

### 2 - Plex
<img src="assets/plexlogo.jpg" width="562" height="230">

Nous allons mainteannt procéder à l'installation de [plex](https://www.plex.tv/)

Rendez-vous dans la section "Containers" de portainer ![](assets/containers.png)

Pour savoir quelles variables d'environnement utiliser, utilisez la [page wiki linuxserver plex](https://hub.docker.com/r/linuxserver/plex)

Pour ma part, j'ai créée un volume pour stocker mes données (Portainer -> Volumes -> Create)
Vous pouvez également effectuer un *bind* qui attribuera un dossier dans le conteneur a un dossier en local.

| Env variable | Value |
|--------------|-------|
| VERSION      | docker|


| Volume       |  Value                | Type
|--------------|-----------------------|------
| /config      | /home/pi/.config      | Volume
| /tv          | /home/pi/media/tv     | Volume
| /movies      | /home/pi/media/movies | Volume

Si vous ne savez pas quoi remplir, ne vous en faites pas. Portainer laisse la possibilité de modifier un conteneur existant.

Lancez maintenant Plex et rendez-vous sur [localhost:32400/web](http://localhost:32400/web) pour configurer la configuration de plex. Créez un compte et ajoutez vos dossiers media dans la librairie plex. 
Vous pouvez maintenant rajouter du contenu en local pour tester que plex fonctionne correctement.

## Partie 2 - Transmission Web Interface
![](assets/transmission.png)

Nous allons maintenant nous intéressés à la partie téléchargement des medias, qui seront ensuite automatiquement ajoutés dans plex.