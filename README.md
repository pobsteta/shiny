Docker pour Shiny Server
=======================

Ce Dockerfile permet la mise en service d'un centeneur Shiny server. Il est basé sur docker-base.


## Usage:

Pour lancer un conteneur shiny server, passer la commande :

```sh
docker run --rm -p 3838:3838 pobsteta/shiny
```

Pour exposer le répertoire sur le conteneur hôte, utiliser `-v <host_dir>:<container_dir>`. La commande suivante utilise `/srv/shinyapps` comme répertoire de l'application shint et `/srv/shinylog` comme répertoire des logs :

```sh
docker run --rm -p 3838:3838 \
    -v /srv/shinyapps/:/srv/shiny-server/ \
    -v /srv/shinylog/:/var/log/ \
    pobsteta/shiny
```

Si vous avez une application dans le répertoire `/srv/shinyapps/appdir`, vous pouvez lancer l'application en vous rendant à l'adresse http://localhost:3838/appdir/. (Si vous utilisez boot2docker, visitez http://192.168.59.103:3838/appdir/)

Dans un déploiement réel, vous devrez probablement lancer le conteneur en mode détaché (`-d`) et écouter sur le port 80 (`-p 80:3838`) :

```sh
docker run -d -p 80:3838 \
    -v /srv/shinyapps/:/srv/shiny-server/ \
    -v /srv/shinylog/:/var/log/ \
    pobsteta/shiny
```

## Trademarks

Shiny and Shiny Server are registered trademarks of RStudio, Inc. The use of the trademarked terms Shiny and Shiny Server and the distribution of the Shiny Server through the images hosted on hub.docker.com has been granted by explicit permission of RStudio. Please review RStudio's trademark use policy and address inquiries about further distribution or other questions to permissions@rstudio.com.
