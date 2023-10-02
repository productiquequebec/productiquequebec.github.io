# Projet

Ce projet démontre un prototype fonctionnel d'une série de technologie mise en place ensemble pour moderniser un exercice de Répétabilité de Reproductibilité des instruments de mesure (Gage R&R) classique. Dans ce projet, la session se déroule au travers de la réalité augmentée programmée grâce au Unity Engine le tout supporté par le casque HoloLens. 

## Table des matières

- [Fonctionnalités](#fonctionnalités)
- [Utilisation](#utilisation)
- [Contact](#contact)
  - [Résolution de problèmes et support](#résolution-de-problèmes-et-support)
- [Feuille de route](#feuille-de-route)
- [Bogues connus](#bogues-connus)
- [Crédits](#crédits)
- [Droits d'auteur et licence](#droits-dauteur-et-licence)
- [Notes et références](#notes-et-références)
  - [Dépendances](#dépendances)
  - [Recommendations](#recommendations)
  - [Suggestions](#suggestions)
  - [Plus d'informations](#plus-dinformations)

## Fonctionnalités

L'application permet d'afficher exactement l'endroit où les mesures doivent être prises grâce à la réalité augmentée. Cela permet à l'opérateur d'être certain d'effectuer le Gage R&R correctement, en plus de faire un suivi des mesures prises de façon automatisée. L'opérateur possède également un menu interactif, permettant de naturellement annuler la dernière mesure, changer de nom d'utilisateur ou même de reprendre la session au complet.

Les données sont ensuite transférer par MQTT sur un *topic* défini lors de la compilation du projet. Les données acquises par des instruments de mesures externes sont également acheminées par MQTT sur un *topic* différent, créant ainsi une interface standard pour les entrées et sorties. 

Finalement, du code est disponible pour créer des tableaux intéressants basé sur Plotly, en JavaScript. Ceux-ci traduisent l'information essentiel pour tirer des conclusions de la session Gage R&R, notamment où se situe les facteurs de variance.

**Ce répertoire contient principalement le code source de l'application Unity** et les fichiers de configuration nécessaires pour l'interface avec MQTT. Il contient également les scripts pour construire les figures, en utilisant la librairie Plotly.

**Ce répertoire ne contient pas :**
- Une instance d'un serveur (ou d'un broker) MQTT
- Un service de  base de donnée capable de stocké de la donnée provenant de session différentes
- Un service de télémétrie ou de tableau de bord capable d'afficher la donnée captée

## Utilisation

Pour utiliser ce projet, la scène doit être monté et lancé sur un appareil supporté. Présentement, le HoloLens 2 a été testé et jugé fonctionnel pour le projet. L'application peut alors être lancée depuis l'appareil. Voici quelques images démontrant les aspects intéressants de la réalité augmenté. 

- La position et l'état des mesures à prendre sont rendus clair grâce aux indicateurs visuels.

  ![](./images/Rotation_autour_piece_stable.gif)

- La prise de mesures automatique avec rétroaction visuelle garantit le bon déroulement de la session.

  ![](./images/Prise_mesures.gif)

- L'utilisation est devenu simplifiée en mettant de côté code QR et autre grâce à la détection de la géométrie de la pièce.

  ![](./images/Detection_piece.gif)
  
- L'interface MQTT permet d'utiliser une grande variété d'outils connectable.

  ![](./images/Multi-outils.gif)


## Contact

Auteur du projet : [Anthony Gauthier](anthony.gauthier@productique.quebec)

### Résolution de problèmes et support

Pour tout problèmes, vous pouvez contacter l'auteur du projet. Notons que certaines fonctionnalités peuvent être indisponibles ne se sont pas supportées.

## Feuille de route

Le projet est en soit un prototype démontrant les applications possibles ainsi que les enjeux entourant ces technologies. Des l'ajout des fonctionnalités suivantes pourrait grandement aider au potentiel de la mise en service d'un tel projet.

- Modularité des mesures : créer une interface simplifié pour changer la quantité et les noms des mesures
- Modularité des pièces : créer un guide simple ou un processus automatisé pour l'ajout de différente pièce
- Interface descente : possibilité à recevoir des instructions pour les pièces et leurs mesures
- Menu interactif avancé : produire davantage d'information au travers du menu interactif
- Amélioration du système de détection : fournir une détection plus fiable et constante

## Bogues connus

**Q: La pièce n'est pas détectée par l'application, que faire ?**

R: La technologie en charge de la détection de pièce est le Vuforia Engine : Model Target. Plusieurs facteurs affectent la détection de la pièce, notamment l'éclairage, l'angle et la distance. Essayer de positionner la pièce de face comme dans la section [utilisation](#utilisation) à une distance allant de 10 à 15 cm du casque HoloLens, le tout centré dans le champs visuel.  

## Crédits

- [anthony.gauthier@productique.quebec](anthony.gauthier@productique.quebec) - auteur

## Droits d'auteur et licence

- [Licence MIT](MIT-LICENSE)
- Productique Québec Copyright © 2023


## Notes et références

### Dépendances

- [Plateforme de développement en temps réel Unity \| Moteur pour la 2D, 3D, RV et RA](https://unity.com/fr) - Plateforme de développement RA
- [MQTT - The Standard for IoT Messaging](https://mqtt.org/) - Protocol d'échange et communication
- [HoloLens 2—Overview, Features, and Specs \| Microsoft HoloLens](https://www.microsoft.com/en-us/hololens/hardware#document-experiences) - Technologie supportant la réalité augmentée
- [Model Targets \| Vuforia Library](https://library.vuforia.com/objects/model-targets) - Technologie pour la détection de pièce

### Recommendations

- [Gage R&R — Wikipédia](https://fr.wikipedia.org/wiki/Gage_R%26R) - Contexte pour l'outils statistique
- [Plotly Open Source Graphing Libraries](https://plotly.com/graphing-libraries/) - Librairie pour créer des figures scientifiques

### Suggestions

- [MQTTX: Your All-in-one MQTT Client Toolbox](https://mqttx.app/) - Client MQTT avec UI pour rapidement et facilement tester les communications 
- [MongoDB Compass \| MongoDB](https://www.mongodb.com/fr-fr/products/compass) - Client MongoDB avec UI pour rapidement et facilement tester des *queries* et l'insertion de donnée 
- [Plotly panel plugin for Grafana \| Grafana Labs](https://grafana.com/grafana/plugins/ae3e-plotly-panel/) - Plugin supportant les figures Plotly sur Grafana
