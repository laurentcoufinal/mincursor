# Commandes Docker

Guide des commandes Docker les plus utilisées avec explications en français.

## Gestion des conteneurs

### Démarrer et arrêter

```bash
docker run <image>
```
Crée et démarre un nouveau conteneur à partir d'une image.

```bash
docker run -d <image>
```
Démarre un conteneur en mode détaché (en arrière-plan).

```bash
docker run -it <image>
```
Démarre un conteneur en mode interactif avec un terminal.

```bash
docker run -p <host_port>:<container_port> <image>
```
Démarre un conteneur en mappant un port du conteneur vers un port de l'hôte.

```bash
docker run --name <name> <image>
```
Démarre un conteneur avec un nom personnalisé.

```bash
docker run -v <host_path>:<container_path> <image>
```
Démarre un conteneur avec un volume monté (partage de fichiers entre hôte et conteneur).

```bash
docker run --rm <image>
```
Démarre un conteneur qui sera automatiquement supprimé après son arrêt.

```bash
docker start <container>
```
Démarre un conteneur existant qui a été arrêté.

```bash
docker stop <container>
```
Arrête un conteneur en cours d'exécution de manière gracieuse (envoie SIGTERM puis SIGKILL).

```bash
docker restart <container>
```
Redémarre un conteneur.

```bash
docker pause <container>
```
Met en pause tous les processus d'un conteneur.

```bash
docker unpause <container>
```
Reprend l'exécution d'un conteneur en pause.

```bash
docker kill <container>
```
Force l'arrêt immédiat d'un conteneur (envoie SIGKILL).

### Lister et inspecter

```bash
docker ps
```
Liste tous les conteneurs en cours d'exécution.

```bash
docker ps -a
```
Liste tous les conteneurs (en cours d'exécution et arrêtés).

```bash
docker ps -q
```
Liste uniquement les IDs des conteneurs en cours d'exécution.

```bash
docker inspect <container>
```
Affiche des informations détaillées sur un conteneur au format JSON.

```bash
docker logs <container>
```
Affiche les logs d'un conteneur.

```bash
docker logs -f <container>
```
Affiche les logs d'un conteneur en temps réel (mode suivi).

```bash
docker logs --tail <number> <container>
```
Affiche les N dernières lignes des logs d'un conteneur.

```bash
docker top <container>
```
Affiche les processus en cours d'exécution dans un conteneur.

```bash
docker stats
```
Affiche en temps réel l'utilisation des ressources de tous les conteneurs.

```bash
docker stats <container>
```
Affiche en temps réel l'utilisation des ressources d'un conteneur spécifique.

### Interagir avec les conteneurs

```bash
docker exec -it <container> <command>
```
Exécute une commande dans un conteneur en cours d'exécution en mode interactif.

```bash
docker exec -it <container> bash
```
Ouvre un shell bash interactif dans un conteneur en cours d'exécution.

```bash
docker exec -it <container> sh
```
Ouvre un shell sh interactif dans un conteneur (utile si bash n'est pas disponible).

```bash
docker attach <container>
```
Se connecte à un conteneur en cours d'exécution (attache au processus principal).

```bash
docker cp <container>:<container_path> <host_path>
```
Copie des fichiers depuis un conteneur vers l'hôte.

```bash
docker cp <host_path> <container>:<container_path>
```
Copie des fichiers depuis l'hôte vers un conteneur.

### Supprimer des conteneurs

```bash
docker rm <container>
```
Supprime un conteneur arrêté.

```bash
docker rm -f <container>
```
Force la suppression d'un conteneur même s'il est en cours d'exécution.

```bash
docker rm $(docker ps -aq)
```
Supprime tous les conteneurs arrêtés.

```bash
docker container prune
```
Supprime tous les conteneurs arrêtés (avec confirmation).

```bash
docker container prune -f
```
Supprime tous les conteneurs arrêtés sans confirmation.

## Gestion des images

### Télécharger et construire

```bash
docker pull <image>
```
Télécharge une image depuis Docker Hub ou un registre.

```bash
docker pull <image>:<tag>
```
Télécharge une version spécifique d'une image.

```bash
docker build -t <name>:<tag> .
```
Construit une image à partir d'un Dockerfile dans le répertoire courant.

```bash
docker build -t <name>:<tag> -f <dockerfile> .
```
Construit une image à partir d'un Dockerfile spécifique.

```bash
docker build --no-cache -t <name>:<tag> .
```
Construit une image sans utiliser le cache.

```bash
docker build --build-arg <key>=<value> -t <name>:<tag> .
```
Construit une image en passant des arguments de construction.

### Lister et inspecter

```bash
docker images
```
Liste toutes les images disponibles localement.

```bash
docker images -a
```
Liste toutes les images y compris les images intermédiaires.

```bash
docker images -q
```
Liste uniquement les IDs des images.

```bash
docker inspect <image>
```
Affiche des informations détaillées sur une image au format JSON.

```bash
docker history <image>
```
Affiche l'historique des couches d'une image.

### Gérer les images

```bash
docker tag <source_image> <target_image>:<tag>
```
Crée un tag (alias) pour une image.

```bash
docker rmi <image>
```
Supprime une image.

```bash
docker rmi -f <image>
```
Force la suppression d'une image même si elle est utilisée par des conteneurs arrêtés.

```bash
docker rmi $(docker images -q)
```
Supprime toutes les images.

```bash
docker image prune
```
Supprime les images non utilisées (avec confirmation).

```bash
docker image prune -a
```
Supprime toutes les images non utilisées par des conteneurs existants.

```bash
docker image prune -af
```
Force la suppression de toutes les images non utilisées sans confirmation.

### Sauvegarder et charger

```bash
docker save -o <filename>.tar <image>
```
Sauvegarde une image dans un fichier tar.

```bash
docker load -i <filename>.tar
```
Charge une image depuis un fichier tar.

```bash
docker export -o <filename>.tar <container>
```
Exporte le système de fichiers d'un conteneur dans un fichier tar.

```bash
docker import <filename>.tar <image>:<tag>
```
Crée une image à partir d'un fichier tar exporté.

## Gestion des volumes

```bash
docker volume create <volume_name>
```
Crée un nouveau volume nommé.

```bash
docker volume ls
```
Liste tous les volumes.

```bash
docker volume inspect <volume_name>
```
Affiche des informations détaillées sur un volume.

```bash
docker volume rm <volume_name>
```
Supprime un volume.

```bash
docker volume prune
```
Supprime tous les volumes non utilisés (avec confirmation).

```bash
docker volume prune -f
```
Force la suppression de tous les volumes non utilisés sans confirmation.

## Gestion des réseaux

```bash
docker network create <network_name>
```
Crée un nouveau réseau.

```bash
docker network ls
```
Liste tous les réseaux.

```bash
docker network inspect <network_name>
```
Affiche des informations détaillées sur un réseau.

```bash
docker network connect <network_name> <container>
```
Connecte un conteneur à un réseau.

```bash
docker network disconnect <network_name> <container>
```
Déconnecte un conteneur d'un réseau.

```bash
docker network rm <network_name>
```
Supprime un réseau.

```bash
docker network prune
```
Supprime tous les réseaux non utilisés (avec confirmation).

## Docker Compose

```bash
docker-compose up
```
Démarre tous les services définis dans docker-compose.yml.

```bash
docker-compose up -d
```
Démarre tous les services en mode détaché (en arrière-plan).

```bash
docker-compose up --build
```
Reconstruit les images avant de démarrer les services.

```bash
docker-compose down
```
Arrête et supprime tous les conteneurs, réseaux et volumes définis dans docker-compose.yml.

```bash
docker-compose down -v
```
Arrête et supprime tous les conteneurs, réseaux et volumes (y compris les volumes nommés).

```bash
docker-compose ps
```
Liste tous les conteneurs des services définis dans docker-compose.yml.

```bash
docker-compose logs
```
Affiche les logs de tous les services.

```bash
docker-compose logs -f
```
Affiche les logs de tous les services en temps réel.

```bash
docker-compose logs -f <service>
```
Affiche les logs d'un service spécifique en temps réel.

```bash
docker-compose exec <service> <command>
```
Exécute une commande dans un conteneur de service en cours d'exécution.

```bash
docker-compose exec <service> bash
```
Ouvre un shell bash dans un conteneur de service.

```bash
docker-compose build
```
Construit ou reconstruit les services.

```bash
docker-compose pull
```
Télécharge les images pour tous les services.

```bash
docker-compose restart <service>
```
Redémarre un service spécifique.

```bash
docker-compose stop
```
Arrête tous les services sans les supprimer.

```bash
docker-compose start
```
Démarre les services précédemment arrêtés.

```bash
docker-compose config
```
Valide et affiche la configuration de docker-compose.yml.

## Registres Docker

```bash
docker login
```
Se connecte à Docker Hub (ou un registre privé).

```bash
docker login <registry_url>
```
Se connecte à un registre Docker spécifique.

```bash
docker logout
```
Se déconnecte de Docker Hub (ou un registre privé).

```bash
docker push <image>:<tag>
```
Pousse une image vers Docker Hub ou un registre.

```bash
docker search <term>
```
Recherche des images sur Docker Hub.

## Nettoyage global

```bash
docker system df
```
Affiche l'utilisation de l'espace disque par Docker.

```bash
docker system prune
```
Supprime tous les conteneurs arrêtés, réseaux non utilisés, images pendantes et cache de build.

```bash
docker system prune -a
```
Supprime tous les conteneurs arrêtés, réseaux non utilisés, toutes les images non utilisées et cache de build.

```bash
docker system prune -af
```
Force le nettoyage complet sans confirmation.

```bash
docker system prune -a --volumes
```
Nettoyage complet incluant tous les volumes non utilisés.

## Informations système

```bash
docker version
```
Affiche les versions du client et du serveur Docker.

```bash
docker info
```
Affiche des informations détaillées sur l'installation Docker.

```bash
docker events
```
Affiche les événements Docker en temps réel.

```bash
docker port <container>
```
Liste les mappages de ports d'un conteneur.

## Commandes avancées

```bash
docker commit <container> <image>:<tag>
```
Crée une nouvelle image à partir des modifications d'un conteneur.

```bash
docker diff <container>
```
Affiche les modifications apportées au système de fichiers d'un conteneur.

```bash
docker wait <container>
```
Bloque jusqu'à ce qu'un conteneur s'arrête et affiche son code de sortie.

```bash
docker rename <old_name> <new_name>
```
Renomme un conteneur.

```bash
docker update --memory <value> <container>
```
Met à jour la configuration d'un conteneur en cours d'exécution.

## Combinaisons utiles

```bash
docker stop $(docker ps -q)
```
Arrête tous les conteneurs en cours d'exécution.

```bash
docker rm $(docker ps -aq)
```
Supprime tous les conteneurs (arrêtés et en cours).

```bash
docker rmi $(docker images -f "dangling=true" -q)
```
Supprime toutes les images pendantes (sans tag).

```bash
docker exec -it $(docker ps -q -f name=<pattern>) bash
```
Ouvre un bash dans le conteneur dont le nom correspond au pattern.

```bash
docker logs --since 30m <container>
```
Affiche les logs des 30 dernières minutes d'un conteneur.

```bash
docker run -d -p 80:80 -v $(pwd):/app <image>
```
Démarre un conteneur en arrière-plan avec port mapping et volume du répertoire courant.

## Docker Swarm

### Initialisation et gestion du cluster

```bash
docker swarm init
```
Initialise un nouveau cluster Swarm et fait de la machine actuelle un manager.

```bash
docker swarm init --advertise-addr <ip_address>
```
Initialise un Swarm en spécifiant l'adresse IP à annoncer aux autres nœuds.

```bash
docker swarm join --token <token> <manager_ip>:<port>
```
Joint un nœud worker ou manager à un cluster Swarm existant.

```bash
docker swarm join-token worker
```
Affiche la commande et le token pour joindre un worker au Swarm.

```bash
docker swarm join-token manager
```
Affiche la commande et le token pour joindre un manager au Swarm.

```bash
docker swarm leave
```
Fait quitter le Swarm au nœud actuel.

```bash
docker swarm leave --force
```
Force un nœud manager à quitter le Swarm.

```bash
docker swarm update --autolock=true
```
Active le verrouillage automatique du Swarm pour protéger les clés de chiffrement.

```bash
docker swarm unlock
```
Déverrouille un Swarm après un redémarrage du manager.

```bash
docker swarm unlock-key
```
Affiche la clé de déverrouillage du Swarm.

### Gestion des nœuds

```bash
docker node ls
```
Liste tous les nœuds du cluster Swarm.

```bash
docker node inspect <node>
```
Affiche des informations détaillées sur un nœud.

```bash
docker node inspect --pretty <node>
```
Affiche les informations d'un nœud dans un format lisible.

```bash
docker node promote <node>
```
Promeut un nœud worker en manager.

```bash
docker node demote <node>
```
Rétrograde un nœud manager en worker.

```bash
docker node update --availability active <node>
```
Rend un nœud disponible pour recevoir des tâches.

```bash
docker node update --availability pause <node>
```
Empêche un nœud de recevoir de nouvelles tâches (les tâches existantes continuent).

```bash
docker node update --availability drain <node>
```
Évacue toutes les tâches d'un nœud vers d'autres nœuds.

```bash
docker node update --label-add <key>=<value> <node>
```
Ajoute un label à un nœud pour le ciblage des services.

```bash
docker node update --label-rm <key> <node>
```
Supprime un label d'un nœud.

```bash
docker node rm <node>
```
Supprime un nœud du Swarm (le nœud doit être arrêté).

```bash
docker node rm --force <node>
```
Force la suppression d'un nœud du Swarm.

```bash
docker node ps
```
Liste les tâches en cours d'exécution sur le nœud actuel.

```bash
docker node ps <node>
```
Liste les tâches en cours d'exécution sur un nœud spécifique.

### Gestion des services

```bash
docker service create --name <service_name> <image>
```
Crée un nouveau service dans le Swarm.

```bash
docker service create --name <service_name> --replicas <number> <image>
```
Crée un service avec un nombre spécifique de réplicas.

```bash
docker service create --name <service_name> -p <host_port>:<container_port> <image>
```
Crée un service avec publication de port.

```bash
docker service create --name <service_name> --network <network> <image>
```
Crée un service attaché à un réseau overlay.

```bash
docker service create --name <service_name> --mount type=volume,src=<volume>,dst=<path> <image>
```
Crée un service avec un volume monté.

```bash
docker service create --name <service_name> --constraint 'node.role==worker' <image>
```
Crée un service avec des contraintes de placement (ici uniquement sur les workers).

```bash
docker service create --name <service_name> --env <KEY>=<VALUE> <image>
```
Crée un service avec des variables d'environnement.

```bash
docker service ls
```
Liste tous les services du Swarm.

```bash
docker service ps <service>
```
Liste toutes les tâches (conteneurs) d'un service.

```bash
docker service ps --filter desired-state=running <service>
```
Liste uniquement les tâches en cours d'exécution d'un service.

```bash
docker service inspect <service>
```
Affiche des informations détaillées sur un service.

```bash
docker service inspect --pretty <service>
```
Affiche les informations d'un service dans un format lisible.

```bash
docker service logs <service>
```
Affiche les logs agrégés de toutes les tâches d'un service.

```bash
docker service logs -f <service>
```
Affiche les logs d'un service en temps réel.

### Mise à jour des services

```bash
docker service scale <service>=<number>
```
Change le nombre de réplicas d'un service.

```bash
docker service update --image <new_image> <service>
```
Met à jour l'image d'un service (rolling update).

```bash
docker service update --replicas <number> <service>
```
Met à jour le nombre de réplicas d'un service.

```bash
docker service update --env-add <KEY>=<VALUE> <service>
```
Ajoute une variable d'environnement à un service.

```bash
docker service update --env-rm <KEY> <service>
```
Supprime une variable d'environnement d'un service.

```bash
docker service update --publish-add <port>:<port> <service>
```
Ajoute une publication de port à un service.

```bash
docker service update --publish-rm <port> <service>
```
Supprime une publication de port d'un service.

```bash
docker service update --constraint-add <constraint> <service>
```
Ajoute une contrainte de placement à un service.

```bash
docker service update --update-parallelism <number> <service>
```
Définit le nombre de tâches mises à jour simultanément.

```bash
docker service update --update-delay <duration> <service>
```
Définit le délai entre les mises à jour de tâches (ex: 10s, 1m).

```bash
docker service update --rollback <service>
```
Annule la dernière mise à jour d'un service.

```bash
docker service rollback <service>
```
Effectue un rollback manuel d'un service vers sa configuration précédente.

### Suppression des services

```bash
docker service rm <service>
```
Supprime un service du Swarm.

```bash
docker service rm <service1> <service2>
```
Supprime plusieurs services à la fois.

### Gestion des stacks

```bash
docker stack deploy -c <compose_file> <stack_name>
```
Déploie ou met à jour une stack complète à partir d'un fichier Compose.

```bash
docker stack deploy -c <compose_file1> -c <compose_file2> <stack_name>
```
Déploie une stack en combinant plusieurs fichiers Compose.

```bash
docker stack ls
```
Liste toutes les stacks déployées.

```bash
docker stack ps <stack_name>
```
Liste toutes les tâches d'une stack.

```bash
docker stack services <stack_name>
```
Liste tous les services d'une stack.

```bash
docker stack rm <stack_name>
```
Supprime une stack et tous ses services.

### Gestion des secrets

```bash
docker secret create <secret_name> <file>
```
Crée un secret à partir d'un fichier.

```bash
echo "<secret_value>" | docker secret create <secret_name> -
```
Crée un secret à partir d'une entrée standard.

```bash
docker secret ls
```
Liste tous les secrets du Swarm.

```bash
docker secret inspect <secret_name>
```
Affiche des informations détaillées sur un secret.

```bash
docker secret rm <secret_name>
```
Supprime un secret du Swarm.

```bash
docker service create --name <service> --secret <secret_name> <image>
```
Crée un service avec accès à un secret.

```bash
docker service update --secret-add <secret_name> <service>
```
Ajoute un secret à un service existant.

```bash
docker service update --secret-rm <secret_name> <service>
```
Supprime l'accès à un secret d'un service.

### Gestion des configs

```bash
docker config create <config_name> <file>
```
Crée une configuration à partir d'un fichier.

```bash
docker config ls
```
Liste toutes les configurations du Swarm.

```bash
docker config inspect <config_name>
```
Affiche des informations détaillées sur une configuration.

```bash
docker config rm <config_name>
```
Supprime une configuration du Swarm.

```bash
docker service create --name <service> --config <config_name> <image>
```
Crée un service avec accès à une configuration.

```bash
docker service update --config-add <config_name> <service>
```
Ajoute une configuration à un service existant.

```bash
docker service update --config-rm <config_name> <service>
```
Supprime l'accès à une configuration d'un service.

### Réseaux overlay

```bash
docker network create --driver overlay <network_name>
```
Crée un réseau overlay pour la communication inter-nœuds dans le Swarm.

```bash
docker network create --driver overlay --attachable <network_name>
```
Crée un réseau overlay pouvant être utilisé par des conteneurs standalone.

```bash
docker network create --driver overlay --encrypted <network_name>
```
Crée un réseau overlay avec chiffrement du trafic de données.

```bash
docker network create --driver overlay --subnet <subnet> <network_name>
```
Crée un réseau overlay avec un sous-réseau spécifique.

### Monitoring et diagnostic

```bash
docker service inspect --pretty <service>
```
Affiche l'état détaillé d'un service de manière formatée.

```bash
docker node ps --filter desired-state=running
```
Liste toutes les tâches en cours d'exécution sur tous les nœuds.

```bash
docker service ps --no-trunc <service>
```
Affiche les tâches d'un service sans tronquer les erreurs.

```bash
docker stack ps --no-trunc <stack_name>
```
Affiche les tâches d'une stack sans tronquer les informations.
