## Analyse du projet : 
---
### Microservices sur le projet : 

#### - Api Gateway : 
    - Dépendances : 
      -  spring-boot-devtools
      -  spring-boot-configuration-processor
      -  spring-boot-starter-actuator
      -  spring-boot-starter-test
      -  spring-cloud-starter-circuitbreaker-reactor-resilience4j
      -  spring-cloud-starter-gateway
      -  spring-cloud-starter-zipkin
      -  wavefront-spring-boot-starter
      -  jolokia-core
      -  lombok
      -  micrometer-registry-prometheus
      -  resilience4j-micrometer
      -  angularjs
      -  jquery
      -  bootstrap
      -  angular-ui-router
      -  webjars-locator-core
      -  junit-jupiter-api
      -  junit-jupiter-engine
      -  mockwebserver
      -  wro4j-maven-plugin
      -  mockito-core
    - Port d'écoute : 8080
    - Variables d'environnement: 
      - ${app.vets.uri}
      - ${app.visits.uri}
      - ${app.customers.uri}
    - Interactions : Cette gateway va recevoir les requêtes du front pour les transférer vers les services demandés 

#### - Customers service : 
    - Dépendances :
      - spring-boot-starter-actuator
      - spring-boot-starter-data-jpa
      - spring-boot-starter-test
      - spring-boot-starter-web
      - spring-boot-starter-validation
      - spring-cloud-starter-zipkin
      - wavefront-spring-boot-starter
      - mysql-connector-java
      - hsqldb
      - jolokia-core
      - lombok
      - micrometer-registry-prometheus
      - junit-jupiter-api
      - junit-jupiter-engine
      - assertj-core
    - Port d'écoute : 8082
    - Variables d'environnement: connexion à mysql
    - Interactions : Va permettre de créer un customer et un animal. L'animal va être lié au service de visite, son id sera stocké dans la table visite. Le front permet de récupérer les animaux d'un customer, de récupérer le propriétaire d'un animal
#### - Vets service : 
    - Dépedances : 
      - spring-boot-starter-web
      - spring-boot-starter-validation
      - spring-boot-configuration-processor
      - spring-boot-starter-actuator
      - spring-boot-starter-cache
      - spring-boot-starter-data-jpa
      - spring-boot-starter-test
      - spring-cloud-starter-zipkin
      - wavefront-spring-boot-starter
      - lombok
      - cache-api
      - ehcache
      - jolokia-core
      - hsqldb
      - mysql-connector-java
      - micrometer-registry-prometheus
      - junit-jupiter-api
      - junit-jupiter-engine
    - Port d'écoute : 8083
    - Variables : chaîne de connexion mysql
    - Interactions : je ne vois pas d'intéraction spécifique entre ce service et les autres. Il n'y a pas d'association en base entre l'animal et le vétérinaire au travers d'un rdv. On peut voir la liste des vétérinaires sur le front. 

#### - Visits service : 
    - Dépendances:
      - spring-boot-starter-actuator
      - spring-boot-starter-data-jpa
      - spring-boot-starter-web
      - spring-boot-starter-validation
      - spring-boot-starter-test
      - spring-cloud-starter-zipkin
      - wavefront-spring-boot-starter
      - lombok
      - hsqldb
      - jolokia-core
      - mysql-connector-java
      - micrometer-registry-prometheus
      - junit-jupiter-api
      - junit-jupiter-engine
    - Port d'écoute : 8084
    - Variables : chaîne de connexion mysql
    - Interactions : permet de créer un rdv avec un animal associé récupéré depuis le service animal

Pour les trois services hors gateway, il faudra passer l'url de la bdd, le username et le password, pour que les différents spring puissent se connecter à leur bdd respectives 