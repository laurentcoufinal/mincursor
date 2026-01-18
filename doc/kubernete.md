# Commandes Principales Kubernetes

## Configuration et Contexte

### kubectl config view
Affiche la configuration complète de kubectl, incluant les clusters, les contextes et les utilisateurs configurés.

### kubectl config get-contexts
Liste tous les contextes disponibles dans votre configuration kubectl. Un contexte définit quel cluster utiliser et avec quelles credentials.

### kubectl config current-context
Affiche le contexte actuellement actif (cluster sur lequel vous travaillez).

### kubectl config use-context [nom-contexte]
Change le contexte actif pour basculer vers un autre cluster Kubernetes.

### kubectl config set-context [nom-contexte] --namespace=[namespace]
Modifie un contexte existant pour définir un namespace par défaut.

## Gestion des Clusters

### kubectl cluster-info
Affiche les informations sur le cluster Kubernetes, notamment l'URL du serveur API et les services système.

### kubectl get nodes
Liste tous les nœuds (nodes) du cluster avec leur statut, rôle et version.

### kubectl describe node [nom-node]
Affiche les détails complets d'un nœud spécifique : capacité, ressources allouées, conditions, pods en cours d'exécution.

### kubectl top nodes
Affiche l'utilisation des ressources (CPU et mémoire) pour chaque nœud du cluster.

## Gestion des Namespaces

### kubectl get namespaces
Liste tous les namespaces du cluster. Les namespaces permettent d'isoler des groupes de ressources.

### kubectl create namespace [nom-namespace]
Crée un nouveau namespace pour organiser vos ressources.

### kubectl delete namespace [nom-namespace]
Supprime un namespace et toutes les ressources qu'il contient.

### kubectl get all -n [namespace]
Liste toutes les ressources dans un namespace spécifique (pods, services, deployments, etc.).

## Gestion des Pods

### kubectl get pods
Liste tous les pods du namespace actuel avec leur statut, nombre de redémarrages et âge.

### kubectl get pods -A
Liste tous les pods de tous les namespaces du cluster.

### kubectl get pods -o wide
Liste les pods avec des informations supplémentaires : IP, nœud d'exécution, etc.

### kubectl describe pod [nom-pod]
Affiche les détails complets d'un pod : conteneurs, volumes, événements, conditions, etc.

### kubectl logs [nom-pod]
Affiche les logs du conteneur principal d'un pod.

### kubectl logs [nom-pod] -c [nom-conteneur]
Affiche les logs d'un conteneur spécifique dans un pod multi-conteneurs.

### kubectl logs [nom-pod] --previous
Affiche les logs du conteneur précédent si le pod a redémarré.

### kubectl logs -f [nom-pod]
Suit les logs d'un pod en temps réel (stream continu).

### kubectl exec -it [nom-pod] -- /bin/bash
Ouvre un shell interactif dans le conteneur d'un pod pour debugging.

### kubectl exec [nom-pod] -- [commande]
Exécute une commande spécifique dans le conteneur d'un pod.

### kubectl delete pod [nom-pod]
Supprime un pod. Si géré par un deployment, il sera automatiquement recréé.

### kubectl delete pod [nom-pod] --grace-period=0 --force
Force la suppression immédiate d'un pod sans attendre sa terminaison propre.

### kubectl port-forward [nom-pod] [port-local]:[port-pod]
Crée un tunnel réseau pour accéder à un port d'un pod depuis votre machine locale.

### kubectl top pods
Affiche l'utilisation actuelle des ressources (CPU et mémoire) pour chaque pod.

## Gestion des Deployments

### kubectl get deployments
Liste tous les deployments avec le nombre de réplicas désirés, actuels et disponibles.

### kubectl describe deployment [nom-deployment]
Affiche les détails complets d'un deployment : stratégie, sélecteurs, réplicas, événements.

### kubectl create deployment [nom] --image=[image]
Crée un nouveau deployment avec une image de conteneur spécifiée.

### kubectl scale deployment [nom-deployment] --replicas=[nombre]
Modifie le nombre de réplicas (pods) d'un deployment pour scaler horizontalement.

### kubectl set image deployment/[nom-deployment] [conteneur]=[nouvelle-image]
Met à jour l'image d'un conteneur dans un deployment (déclenche un rolling update).

### kubectl rollout status deployment/[nom-deployment]
Affiche le statut du déploiement en cours (rolling update).

### kubectl rollout history deployment/[nom-deployment]
Affiche l'historique des révisions d'un deployment.

### kubectl rollout undo deployment/[nom-deployment]
Annule le dernier déploiement et revient à la révision précédente.

### kubectl rollout undo deployment/[nom-deployment] --to-revision=[numéro]
Revient à une révision spécifique du deployment.

### kubectl rollout restart deployment/[nom-deployment]
Force le redémarrage de tous les pods d'un deployment.

### kubectl delete deployment [nom-deployment]
Supprime un deployment et tous les pods qu'il gère.

## Gestion des Services

### kubectl get services
Liste tous les services du namespace actuel avec leurs types et IPs.

### kubectl get svc
Raccourci pour `kubectl get services`.

### kubectl describe service [nom-service]
Affiche les détails complets d'un service : sélecteurs, ports, endpoints.

### kubectl expose deployment [nom-deployment] --port=[port] --type=[type]
Crée un service pour exposer un deployment (types : ClusterIP, NodePort, LoadBalancer).

### kubectl delete service [nom-service]
Supprime un service.

## Gestion des ConfigMaps et Secrets

### kubectl get configmaps
Liste tous les ConfigMaps qui stockent des données de configuration non sensibles.

### kubectl describe configmap [nom-configmap]
Affiche le contenu et les métadonnées d'un ConfigMap.

### kubectl create configmap [nom] --from-file=[fichier]
Crée un ConfigMap à partir d'un fichier.

### kubectl create configmap [nom] --from-literal=[clé]=[valeur]
Crée un ConfigMap avec des paires clé-valeur directement en ligne de commande.

### kubectl get secrets
Liste tous les Secrets qui stockent des données sensibles (mots de passe, tokens, clés).

### kubectl describe secret [nom-secret]
Affiche les métadonnées d'un Secret (pas le contenu par défaut pour sécurité).

### kubectl create secret generic [nom] --from-file=[fichier]
Crée un Secret à partir d'un fichier.

### kubectl create secret generic [nom] --from-literal=[clé]=[valeur]
Crée un Secret avec des paires clé-valeur directement en ligne de commande.

## Gestion des Volumes et PersistentVolumes

### kubectl get pv
Liste tous les PersistentVolumes (PV) du cluster, qui représentent le stockage physique.

### kubectl get pvc
Liste tous les PersistentVolumeClaims (PVC), les demandes de stockage par les pods.

### kubectl describe pv [nom-pv]
Affiche les détails d'un PersistentVolume : capacité, mode d'accès, statut.

### kubectl describe pvc [nom-pvc]
Affiche les détails d'un PersistentVolumeClaim et son binding avec un PV.

## Gestion des Ingress

### kubectl get ingress
Liste tous les Ingress qui gèrent l'accès HTTP/HTTPS externe vers les services.

### kubectl describe ingress [nom-ingress]
Affiche les détails d'un Ingress : règles de routage, backend services, TLS.

## Application de Manifestes YAML

### kubectl apply -f [fichier.yaml]
Applique la configuration définie dans un fichier YAML (crée ou met à jour les ressources).

### kubectl apply -f [dossier]/
Applique récursivement tous les fichiers YAML d'un dossier.

### kubectl apply -f [url]
Applique une configuration depuis une URL distante.

### kubectl create -f [fichier.yaml]
Crée des ressources depuis un fichier YAML (échoue si elles existent déjà).

### kubectl delete -f [fichier.yaml]
Supprime les ressources définies dans un fichier YAML.

### kubectl replace -f [fichier.yaml]
Remplace une ressource existante par la configuration du fichier YAML.

## Inspection et Debugging

### kubectl get events
Liste les événements récents du cluster (utile pour diagnostiquer les problèmes).

### kubectl get events --sort-by=.metadata.creationTimestamp
Liste les événements triés par date de création.

### kubectl get all
Liste toutes les principales ressources du namespace actuel.

### kubectl get [ressource] -o yaml
Affiche la configuration complète d'une ressource au format YAML.

### kubectl get [ressource] -o json
Affiche la configuration complète d'une ressource au format JSON.

### kubectl get [ressource] -o wide
Affiche des informations supplémentaires sur une ressource.

### kubectl api-resources
Liste tous les types de ressources disponibles dans le cluster avec leurs noms courts.

### kubectl explain [ressource]
Affiche la documentation d'une ressource Kubernetes.

### kubectl explain [ressource].[champ]
Affiche la documentation d'un champ spécifique d'une ressource.

## Gestion des Labels et Annotations

### kubectl label pod [nom-pod] [clé]=[valeur]
Ajoute ou modifie un label sur un pod.

### kubectl label pod [nom-pod] [clé]-
Supprime un label d'un pod.

### kubectl get pods -l [clé]=[valeur]
Filtre les pods par label.

### kubectl annotate pod [nom-pod] [clé]=[valeur]
Ajoute ou modifie une annotation sur un pod.

## Gestion des StatefulSets

### kubectl get statefulsets
Liste tous les StatefulSets, utilisés pour les applications avec état (bases de données, etc.).

### kubectl describe statefulset [nom-statefulset]
Affiche les détails complets d'un StatefulSet.

### kubectl scale statefulset [nom-statefulset] --replicas=[nombre]
Modifie le nombre de réplicas d'un StatefulSet.

## Gestion des DaemonSets

### kubectl get daemonsets
Liste tous les DaemonSets qui exécutent un pod sur chaque nœud du cluster.

### kubectl describe daemonset [nom-daemonset]
Affiche les détails complets d'un DaemonSet.

## Gestion des Jobs et CronJobs

### kubectl get jobs
Liste tous les Jobs, tâches qui s'exécutent jusqu'à complétion.

### kubectl describe job [nom-job]
Affiche les détails d'un Job.

### kubectl get cronjobs
Liste tous les CronJobs, tâches planifiées périodiquement.

### kubectl describe cronjob [nom-cronjob]
Affiche les détails d'un CronJob et son planning.

## Gestion des Ressources RBAC (Sécurité)

### kubectl get serviceaccounts
Liste tous les comptes de service du namespace.

### kubectl get roles
Liste tous les rôles définissant les permissions dans le namespace.

### kubectl get rolebindings
Liste tous les liens entre rôles et utilisateurs/groupes dans le namespace.

### kubectl get clusterroles
Liste tous les rôles au niveau du cluster.

### kubectl get clusterrolebindings
Liste tous les liens entre rôles cluster et utilisateurs/groupes.

## Commandes Avancées

### kubectl patch [ressource] [nom] -p '[json-patch]'
Modifie partiellement une ressource avec un patch JSON.

### kubectl edit [ressource] [nom]
Ouvre l'éditeur par défaut pour modifier directement une ressource.

### kubectl drain [nom-node]
Évacue tous les pods d'un nœud avant maintenance (cordon + evict).

### kubectl cordon [nom-node]
Marque un nœud comme non-schedulable (empêche de nouveaux pods).

### kubectl uncordon [nom-node]
Marque un nœud comme schedulable à nouveau.

### kubectl taint nodes [nom-node] [clé]=[valeur]:[effet]
Ajoute une taint sur un nœud pour contrôler quels pods peuvent y être planifiés.

### kubectl proxy
Démarre un proxy local vers le serveur API Kubernetes.

### kubectl version
Affiche la version du client kubectl et du serveur Kubernetes.

## Helm (Gestionnaire de Packages)

### helm install [nom-release] [chart]
Installe une application Kubernetes depuis un chart Helm.

### helm list
Liste toutes les releases Helm installées.

### helm upgrade [nom-release] [chart]
Met à jour une release Helm existante.

### helm uninstall [nom-release]
Désinstalle une release Helm et ses ressources.

### helm rollback [nom-release] [revision]
Revient à une révision précédente d'une release Helm.

## Tips et Raccourcis

### alias k=kubectl
Crée un alias pour taper plus rapidement (à ajouter dans votre .bashrc ou .zshrc).

### kubectl run [nom] --image=[image] --restart=Never
Crée un pod simple sans deployment.

### kubectl run [nom] --image=[image] --rm -it --restart=Never -- /bin/bash
Crée un pod temporaire interactif qui sera supprimé à la sortie.

### kubectl auth can-i [verbe] [ressource]
Vérifie si vous avez la permission d'effectuer une action sur une ressource.

### kubectl api-versions
Liste toutes les versions d'API disponibles dans le cluster.
