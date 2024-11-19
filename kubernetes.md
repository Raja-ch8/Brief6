# *Contexte du projet*

Vous allez déployer l’application Azure Voting App et sa base de données Redis sur le cluster Kubernetes de Azure : AKS.
Ce brief est individuel. Le rendu sera aussi individuel. Vous êtes bien sûr invités à vous entraider.

# *Modalités pédagogiques*

## **Chapitre 1 : Déployer un cluster AKS**
Créer un cluster AKS avec 2 nodes

## **Chapitre 2 : Déployer un container Redis**
Créer un Deployment avec une image Redis Créer un Service de type LoadBalancer pour exposer le Deployment sur le port 6379 Installer un client Redis sur votre poste de travail Tester la connection au container Redis déployé

## **Chapitre 3 : Déployer un container Voting App**
Créer un Deployment avec une image de l’application Azure Voting App qui dépend de Redis Configurer la variable d’environnement STRESS_SECS à 2 pour le container Voting App Créer un Service de type LoadBalancer pour exposer le container Azure Voting App Modifier le type du Service de Redis pour utiliser ClusterIP (https://learn.microsoft.com/fr-fr/azure/aks/concepts-network) Tester le bon fonctionnement de l’application depuis votre navigateur web

## **Chapitre 4 : Un mot de passe pour Redis**
Configurer le container Redis pour authentifier les clients avec un mot de passe (utiliser --requirepass pour démarrer redis-server) Le mot de passe à utiliser devra être sécurisé dans un Kubernetes Secret Configurer le container Voting App pour utiliser ce mot de passe avec la variable d’environnement REDIS_PWD

## **Chapitre 5 : Configurer un stockage persistent pour Redis**
Supprimer puis recréer le container Redis Constater que le compte de votes est remis à 0 sans avoir à cliquer sur Reset Déduire que le stockage est volatile par défaut Créer un PersistentVolumeClaim pour le container Redis avec une StorageClass adéquate pour permettre le scale out de Redis dans un futur brief Refaire le test des points 1. et 2. et en conclure que le stockage est maintenant permanent
​
## **Chapitre 6 : Utiliser Azure Application Gateway avec AKS**
Supprimer le cluster AKS Recréer un cluster AKS avec l’add-on AGIC et 4 nodes Créer un Ingress dans votre configuration Kubernetes pour l’Application Gateway Modifier le Service Voting App en conséquence Redéployer l’application et sa base de données

## **Chapitre 7 : Un nom de domaine pour Voting App**
Configurer votre zone DNS pour pointer vers l’adresse IP publique de l’Application Gateway Tester avec votre navigateur web

## **Chapitre 8 : Un certificat TLS pour Voting App**
Créer un certificat TLS pour la Voting App en utilisant Certbot et le challenge DNS sur votre poste de travail Updater le certificat de l’Application Gateway Vérifier que le HTTPS fonctionne correctement via votre navigateur web

## **Chapitre 9 : Scaling de la Voting App**
Configurer le nombre de replicas à 2 pour le container Voting App Configurer une règle d’autoscaling à 70% de CPU, max 8 instances (HorizontalPodAutoscaler) Utiliser le script de montée en charge implémenté au brief 4 pour tester une montée en charge
