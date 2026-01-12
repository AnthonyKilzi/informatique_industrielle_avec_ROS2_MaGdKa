Installation d’Ubuntu sur la Raspberry Pi 5
===========================================

Cette section décrit la procédure d’installation du système
d’exploitation **Ubuntu** sur une **Raspberry Pi 5**.

Dans notre cas, nous disposons d’une **carte micro-SD** initialement
configurée avec **Raspberry Pi OS**, qui sera utilisée pour installer
Ubuntu.  
Du matériel informatique classique (écran, clavier et souris) est
également nécessaire afin d’interagir avec la Raspberry Pi lors de
l’installation.

---

Installation de Raspberry Pi Imager
-----------------------------------

L’outil **Raspberry Pi Imager** est utilisé pour flasher l’image
d’Ubuntu sur la carte micro-SD.

Puisque l’installation est réalisée depuis **Raspberry Pi OS**, la
commande suivante permet d’installer et de lancer l’outil :

.. code-block:: bash

   sudo apt install rpi-imager
   rpi-imager

---

Choix de l’image Ubuntu
-----------------------

Une fois Raspberry Pi Imager lancé, les éléments suivants doivent être
sélectionnés :

- Le modèle de carte : **Raspberry Pi 5**
- Le système d’exploitation : **Ubuntu 24.04**
- Le périphérique de stockage : **carte micro-SD (par défaut)**

Après validation, le logiciel procède au téléchargement et à
l’écriture de l’image sur la carte micro-SD.  
La durée de cette étape dépend principalement de la vitesse de la
connexion Internet.

---

Premier démarrage
-----------------

Une fois l’écriture terminée, la Raspberry Pi doit être redémarrée.
Le système démarre alors automatiquement sous **Ubuntu**.

---

Tentative de partitionnement de la carte micro-SD
-------------------------------------------------

Afin de permettre à chaque groupe de travail d’effectuer ses propres
manipulations, une tentative de partitionnement de la carte micro-SD a
été réalisée à l’aide de l’outil **GParted**.

Installation et lancement de GParted :

.. code-block:: bash

   sudo apt-get install gparted
   sudo gparted

Toutefois, après plusieurs essais, cette méthode de partitionnement ne
s’est pas révélée fonctionnelle et n’a pas été retenue pour la suite
du projet.

---

Référence
---------

Pour plus de détails concernant l’installation des systèmes
d’exploitation sur Raspberry Pi, se référer à la documentation
officielle :

- https://www.raspberrypi.com/documentation/computers/getting-started.html#raspberry-pi-imager
