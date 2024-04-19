# Travaux menés et à venir pour openApi et Cache

l'objectif est de proposer des solutions pour conforter l'usage du cache http autour d'une API publique sans données personnelles et décrite à l'aide d'une spécification OAS. Ces solutions seront mises en oeuvre dans le cadre de la modernisation de metadata-api

## Existant

- [X] [Fichier open api existant](./metadata-openapi.json) :
  - long et redondant
  - format swagger 2 !
- [ ] Usage du cache 
- [ ] Processus de build existant

## Processus build cible

- [X] OAS first : écrire OAS avec IJ 2023.3 ?
- [X] OAS dans un projet indépendant 
  - [X] avec génération de librairie model (artifact) ?
  - [X] avec génération d'interfaces pour controllers (artifact) ?
  - [ ] avec génération de lib clientes (artifact, npm)
- [X] Projet qui dépend des artifacts générés et qui embarque le fichier OAS

## Refactor existant

- [ ] **RETROUVER L'HISTORIQUE GIT**
- [X] java 21 enable-preview
- [ ] retourner le fichier openapi sur le endpoint GET /openapi
  - [X] charger le fichier et désérialiser dans oas-model de swagger
  - [X] retourner le fichier en indiquant l'url du serveur correspondant à celle de la requête
  - [ ] Tester
- [ ] configuration : spring boot, properties, logs, cnx bdd
- [ ] Spring rdf... pour le sparlq ?
  - Gérer les injections ds les req sparql
- Implémentation des controllers
  - [ ] Ecrire des méthodes de service normées (nommage) par rapport aux controllers
  - [ ] Implémentant les méthodes de controller a minima en cablant explicitement vers la méthode de service
  - [ ] Générer les implémentations de controllers depuis les méthodes de service et les interfaces au runtime
- [ ] Healthcheck (sparql accessible et schema accessible)
- [ ] erreurs et codes retours
- [ ] factorisation / générisation req et mappings csv
- 
- [ ] refactor tests (tests des req sparql ?)
- [X] Implémentation des interfaces controller
- [ ] customisation du OAS (indiquer le serveur pour les try it)

## Mise en place du cache dans les controllers

- [] indiquer la présence de headers cache (extensions OAS)
- [] Générer les annotations (ou autres ?) spécifiant l'utilisation de balises cache pour les controllers
- [] Implémenter des mécanismes qui ajoutent des headers dans les requêtes quand c'est spécifié dans OAS et suivant les spécifications du métier par endpoint
  - comportement par défaut
  - durée par défaut
  - durée spécifiée dans open api
- [] Tests

## Génération d'un client java qui utilise les informations de cache de l'API

- [] Trouver un cache applicatif qui supporte des durées de conservation et de la revalidation
- [] Générer des annotations dans les clients pour utiliser un cache applicatif en lien avec les headers cache http 
- [] Implémenter une lib qui utilise les annotations et les headers http sur les clients pour alimenter un cache applicatif
- [] Rendre paramétrable le choix du cache applicatif avec un choix par défaut et un connecteur par défaut
- [] Tests : utiliser wiremock pour tester ?

## Trouver des cas similaires dans la littérature (au niveau des clients http)

## Quelques liens

https://github.com/OpenAPITools/openapi-generator/blob/master/docs/customization.md
https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator/src/main/resources/Java
https://github.com/OpenAPITools/openapi-generator/blob/master/docs/generators/java.md
https://plugins.jetbrains.com/plugin/8433-openapi-generator
https://openapi-generator.tech/docs/generators/spring/
https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator-maven-plugin
https://openapi-generator.tech/docs/generators/java/
https://github.com/OpenAPITools/openapi-generator/blob/master/modules/openapi-generator/src/main/resources/JavaSpring/api.mustach

## Utiliser également [RAML](raml.org)

- OAS et RAML semblent complémentaires : https://blogs.mulesoft.com/dev-guides/open-api-raml-better-together/
- Conf sur RAML : https://www.youtube.com/watch?v=4oLUXZXUZYc


