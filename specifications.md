---
layout: default
title: Spécifications
nav_order: 2
has_children: false
---

Valise Multicapteurs
====================
Cahier des charges fonctionnel
------------------

### Fonctionnalités :

#### Energie :

- Etre mis sous/hors tension :
	+ Interrupteur.

#### Traitement des données

- Mesurer :
	+ Température.
	+ Conductivité (salinité).
	+ O2 dissous.
	+ Turbidité.
	+ Chlorophylle.
	+ pH.
- Mesures géoréférencées et horodatées :
	+ Calcul de position, date, heure (Décodeur GNSS RTK + réseau Cenipède).
- Stockage sur un serveur central distant :
	+ Envoi des données à un serveur central (Internet : clé 4G ou Wifi).
- Stockage local (pas d'accès internet) :
	+ BDD locale.
	+ Synchronisation des données locales sur le serveur central.
- Stockage backup sur la station :
	+ Stockage sur carte SD.
- Visualisation des données pour utilisateurs locaux et distants.

#### Commande système :

- Demande de calibration.
- Demande de mesure.
- Ordre de mise en veille.
- Ordre de mise hors tension :
	+ Interrupteur piloté / Relai.

#### Interface utilisateur
- Visualisation :
	+ Par grandeur.
	+ En direct (valeur actuelle d'une sonde).
	+ Sur une période.
- Calibration.
	
### Contraintes :

#### Flexibilité

- Architecture système flexible :
	+ Système autonome : Station unique et récupération des données via carte SD / WiFi. Autonomie maximale sur batterie.
	+ Système temps réel : Station avec serveurs local et distant. Station sur batterie et serveur local sur secteur.

#### Installation :

- Facile à installer :
	+ Hardware :
		*	Facile à se procurer.
		*	Facile à monter.
	+ Software :
		* Facile à installer et configurer.
	+ Instalation à bord facile.

#### Energie :

- Source d'alimentation difficile d'accès pour la station de mesure :
	+ Fonctionner sur batterie.
	+ Rechargeable.
- Autonomie maximale :
	+ Economie d'énergie :
		* Mise en veille de la station.
		* Protocoles économes (BLE, Zigbee, etc.).

#### Coût :

- Système à prix abordable (à définir) :
	+ Composants abordables.
	+ Mesures exploitables à faible coût :
		* Capteurs low cost mais fiables.
- Faible maintenance :
	+ Capteurs à faible maintenance (pas de membranes -> optiques).

#### Milieu marin :

- Etanche et résistant :
	+ Capteurs étanches, robustes.
	+ Boîtier étanche (station).

#### Interactions utilisateur :

- User friendly :
	+ Interface d'aide à la calibration simple.
	+ Visualisation des données aisée.
	+ Commande du système simple.


### Diagramme des flux global du système :
	
![Diagramme des flux du système](assets/schema/flux_diagram_latest.png "Diagramme des flux du système")

### Idées :

#### Serveur local :

- Raspberrry Pi.

#### Station de mesure :
- Boards candidates :

| Board | Protocoles de communication | Interfaces |
|-------|-----------------------------|-------|
| [**Teensy**](https://www.pjrc.com/teensy/) + [**Module Zigbee**](https://www.pjrc.com/teensy/td_libs_XBee.html) | Zigbee | 7-8 série, 2-3 SPI, 3 I²C |
| [**SparkFun Thing Plus XBee3 Micro**](https://www.sparkfun.com/products/15454) | Zigbee | UART, SPI, I²C |
| [**LilyGO T-Zigbee**](https://www.lilygo.cc/products/t-zigbee-esp32-c3-tlsr8258) | ES32C3 : WiFi, Bluetooth <br><br> TLSR8258 : Zigbee, BLE5 | 2 UART, 1 I²C, 3 SPI<br><br> UART, I²C, SPI, USB|
| [**ESP32**](https://www.espressif.com/en/products/devkits) | Bluetooth, WiFi |
| [**Wio-E5 mini**](https://wiki.seeedstudio.com/LoRa_E5_mini/) | LoRa | 3 UART, 1 SPI, 1 I²C |
