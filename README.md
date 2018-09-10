# TEST DEVOPS (~ entre 1h et 3h)

Le but de cet exercice est d’automatiser le déploiement de tomcat avec Ansible et de tester ce déploiement dans un conteneur.


- Cloner le [repository Git](https://github.com/itidm/test) et utiliser les ressources présentes dans le [répertoire tomcat_deploy](./tomcat_deploy).

- Ecrire un playbook ansible ```tomcat_deploy.yml``` permettant d’installer un serveur tomcat avec les paramètres suivants:
  - Version tomcat: 8
  - Taille max heap JVM dépendante de l’environnement:

  ```yaml
  DEV: 256Mo
  PROD: 512Mo
  ```

  - War: Déployer le war  ```sample.war```

- Ecrire un script ```tomcat_deploy.sh``` (moins de 10 lignes) permettant de tester la configuration Ansible dans un conteneur Docker. Ce script doit:
  - Construire le conteneur de test à partir du Dockerfile déjà présent dans le repository.
  - Lancer le conteneur et exécuter le script ```tomcat_test.sh``` (déjà présent dans le repository) à l’intérieur du conteneur afin d’exécuter le playbook et de lancer une série de tests.

:warning: **ATTENTION** :warning: :  pour éviter des problèmes de démarrage de service à l’intérieur du conteneur, il faut le lancer avec l’option ```--privileged=true```

Quelques points :
- Le répertoire ```tomcat_deploy``` doit être **monté** en tant que dossier ```/data``` du container Docker afin de lancer le script de test.
- L’environnement (DEV/PROD) est passé en paramètre de la commande Ansible avec ```--extra-vars="env=${ENVIRONMENT}"``` et permettre de configurer la taille maximum de la heap JVM en conséquence.
- L’installation de tomcat, le déploiement du war et le paramétrage de la heap sont les seuls paramètres attendus dans la configuration Ansible (faire au plus simple).
- Votre solution **doit** être rendue sous forme de **repository Git** (GitHub, autre repository Git en ligne, ou zip du repo git local).
- Cet exercice a été testé avec la version **1.13.1** de docker. Si vous utilisez une version différente, veuillez la préciser.


# Questions subsidiaires
- que reprocheriez-vous à ce test ?
