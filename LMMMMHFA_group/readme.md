## Recherche sur les données GTFS

## **1. Recherche préalable** 

### *Historique*
General Transit Feed Specification permet de communiquer sur les données des horaires de transports en commun. Est présent des données comme les emplacements des arrêts, des tracés de lignes. 
GTFS est conçu originellement par Bibiana McHugh, responsable SI chez TriMet, qu’est l’autorité organisatrice des transports urbains de l’agglomération de Portland en collab avec Google initialement nommé Google Transit Feed Specification



C’est une base de données relationnelle, qui permet, grâce à des arrêts, des lignes et des trajets à identifiants uniques, de modéliser des itinéraires dans des applications de transports, de gérer le réseau et mettre à jour les horaires, et un grand nombre d’autres usages

Informations sur le format 
format conçu par Google  → Flux GTFS

Format : 
 (Données Statique)GTFS Schedule : format contenant les infos sur les itinéraires, les horaires, le tarif etc..  sous forme d’un fichier txt un format simple. Archives Zip (fichiers CSV et txt)
(Donnée Temps Réel)GTFS Realtime :  format contenant mise à jour des trajets, positions, et les alertes de service (arrêts déplacés, événements imprévus affectant une station, un itinéraire ou l'ensemble du réseau).



### *Structuration des données*

En statique :\
\_\_\_\_\_\_\_\_\_\_\_\_\_

Les données sont écrites au format .txt et structurées selon un *MCD* de référence standardisé \
Puis elles sont rassemblées dans un ZIP


En temps réel :\
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
Utilisation de l'API 

### *Principaux fichiers*
Un fichier par type de données : arrêts, calendriers, horaires, itinéraires, agences

 (*O : Obligatoire F : Facultatif*)
- O  agency.txt regroupe les informations sur le service de transport (compagnies de transport, nom du réseau)
- O calendar.txt et  F calendar_dates.txt qui contiennent le calendrier de circulation
- O  routes.txt présente le nom et la direction des routes (au sens d'une origine-destination)
- O  stops.txt liste tous les points d'arrêt et propose d'éventuelles informations
- O  trips.txt détaille les courses, sous la forme d'une table de liaison entre les services (agency), les routes et les régimes de circulation (calendar.txt et calendar_dates.txt)
- O stops_times.txt présente les horaires des courses aux points d'arrêt
- F transfers.txt présente les correspondances entre plusieurs points d'arrêt
shapes.txt permet le tracé d'une route sur une carte
- F frequencies.txt indique le temps entre deux courses d'une ligne (pour celles qui n'ont pas d'horaires fixes aux points d'arrêts)
- F fare_attributes.txt , fare_rules , shapes.txt , feed_infos.txt
lien.


### *Contenu*
Informations sur les agences de transport, les itinéraires, les arrêts, les horaires, les voyages, les tarifs et d'autres éléments essentiels pour comprendre et utiliser un système de transport en commun.



## MCD GTFS
![A cat from an other website](data:image/png;base64,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)




## **2. Exemples**

lien exemple : https://developers.google.com/transit/gtfs/examples/gtfs-feed?hl=fr



### *Quels sont les principaux fichiers composant un ensemble de données GTFS ?* 
Fait au dessus

### *Quel est le but de chaque fichier GTFS ?*
(Soutenir une plus grande interopérabilité des données de transport en commun)\
Améliorer l'expérience de l'utilisateur final dans les applications de transport public.\
Faciliter le déploiement et la mise à l'échelle des applications, produits et services par les développeurs de logiciels.\
(Faciliter l'utilisation de GTFS dans diverses catégories d'applications (au-delà de son objectif initial de planification des trajets)
### *Quels sont les types d'informations qui peuvent être trouvés dans un fichier GTFS ?*
Horaires théoriques : Informations sur les itinéraires, les horaires, les tarifs et les détails géographiques des transports publics.\
Mise à jour des trajets : Données en temps réel sur les retards, les annulations, les itinéraires modifiés.\
Alertes de service : Informations sur les arrêts déplacés, les événements imprévus affectant une station, un itinéraire ou l'ensemble du réseau.\
Positions des véhicules : Détails sur les véhicules, y compris leur emplacement et le niveau de congestion.\
Ces informations variées permettent aux utilisateurs d'accéder à des données actualisées sur les horaires, les trajets et les services de transport en commun, améliorant ainsi leur expérience et leur planification lors de leurs déplacements


### *Comment les données GTFS sont-elles utilisées dans les applications de transport en commun ?*
Pour la planification des trajets : planifier les déplacements en fonction des temps de trajet etc\
Pour l’affichage des horaires : Afficher les retards éventuels et connaître les futurs passages.\
Suivi des véhicules : Connaître en temps réel la position des transports en commun pour estimer le temps d’attente et d’arrivée.\
Alertes de services : Permet les usagers des transports en commun d’éventuels incidents, des travaux ou événements spéciaux.

### *Quels sont les avantages et les limites du format GTFS ?*
Maintenir les données dans le temps , actualisation peut être un frein 
Mise à jour  régulière 
qui corrige? qui entre les données ? qui actualise ? qui publie ?

Mon seul avantage est de travailler avec Margaux la nigaut <3 

## 3. Analyse des données GTFS RealTime

Nous avons choisi les données de Angers Métropoooole !!! 
en **RealTime** grâce à son Api.\
Nous avons téléchargé les données en one-shot pour visualiser les résultats

### *Informations clés*
- Plusieurs données s'offrent à nous, obligatoires et facultatives
- Deux (2) avec une géométrie (MULTIPOINT) (shapes.txt et stops.txt)
- Les attributs des différentes données sont de types 
  - Booléens (0 ou 1) 
  - Text
  - Décimal 
  - DateTime
- Notre données comporte des tables dites facultatives, qui nous permettent d'avoir une connaissance plus fine sur les horaires de passage (calendar_dates.txt) 
-  En se référant au MCD nous avons pu créer des jointures sur les différentes couches 



A la différence des **GTFS schedules**, nous avons accès aux données en temps réel permettant d'avoir des informations en direct sur les trajets référencés.
Les **GTFS RealTime** nous permet d'avoir la position exacte des véhicules de transport en commun, la mise à jour des trajets et les alertes de service

### *Structuration des données GTFS-rt*
**Le fichier général :** gtfs-realtime.proto

Défini la structure des données et des messages pour les flux\
Utilise un code source qui permet de lire les données\
Synchronise avec les gtfs-static 

**Plusieurs informations disponibles :**

Position du véhicule : Indique la position géographique actuelle d'un véhicule en mouvement. (latitude, longitude, vitesse, direction, etc)

Mise à jour de trajet :Informations sur l'état actuel d'un trajet spécifique. (retards, avances, changements d'itinéraire,  temps d'attente prévus aux arrêts, etc.)

Informations sur les arrêts : Indiquent les prochains arrêts prévus pour un véhicule donné. (l'heure estimée d'arrivée,  retards éventuels,  informations sur les plateformes, etc.)

Alertes : Informations sur les perturbations ou les alertes qui pourraient affecter le service de transport en commun. (fermetures de routes, retards généralisés, pannes de véhicules, travaux de maintenance, etc.)




![oupsi petit probleme de connexion](GFTs-TR.png "VIVE THOMAS LE BOOMER <3")




