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
- [ ] OAS dans un projet indépendant ?
  - [ ] avec génération de librairie model (artifact) ?
  - [ ] avec génération d'interfaces pou controllers (artifact) ?
  - [ ] avec génération de lib clientes (artifact, npm)
- [ ] Projet qui dépend des artifacts générés et qui embarque le fichier OAS

## Refactor existant

- java 21 ?
- [] configuration : spring boot, properties, logs, cnx bdd
- [] refactor tests (tests des req sparql ?)
- [] Implémentation des interfaces controller
- [] customisation du OAS (indiquer le serveur pour les try it)

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
- [] Tests

## Trouver des cas similaires dans la littérature (au niveau des clients http)