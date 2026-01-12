Installation d’Ubuntu sur la Raspberry Pi 5
===========================================

Cette section décrit les étapes nécessaires pour installer
**Ubuntu 22.04 LTS (64 bits)** sur une **Raspberry Pi 5**,
en vue de l’utilisation de **ROS 2 Humble**.

---

Matériel requis
---------------

- Raspberry Pi 5
- Carte micro-SD (32 Go minimum recommandé)
- Lecteur de carte SD
- Alimentation USB-C (5 V – 5 A recommandé)
- Clavier, souris, écran (ou accès SSH)
- Connexion Internet

---

Téléchargement de l’outil d’installation
-----------------------------------------

L’outil recommandé est **Raspberry Pi Imager**.

Installation sur Ubuntu :

.. code-block:: bash

   sudo apt update
   sudo apt install rpi-imager

---

Flash de l’image Ubuntu
-----------------------

1. Lancer l’outil :

.. code-block:: bash

   rpi-imager

2. Sélectionner :
   
   - **OS** → *Other general-purpose OS*
   - **Ubuntu**
   - **Ubuntu Server 22.04 LTS (64-bit)**

3. Sélectionner la carte micro-SD
4. Cliquer sur **Write**
5. Attendre la fin du flash

---

Premier démarrage
-----------------

1. Insérer la carte micro-SD dans la Raspberry Pi 5
2. Connecter :
   - alimentation
   - écran
   - clavier

3. Démarrer la carte

Identifiants par défaut :

- **Utilisateur** : ubuntu
- **Mot de passe** : ubuntu

⚠️ Le système demandera de changer le mot de passe au premier login.

---

Configuration initiale
----------------------

Mise à jour du système :

.. code-block:: bash

   sudo apt update
   sudo apt upgrade -y

Configuration du fuseau horaire :

.. code-block:: bash

   sudo timedatectl set-timezone Europe/Paris

Vérification de la version d’Ubuntu :

.. code-block:: bash

   lsb_release -a

---

Configuration du réseau (optionnel)
-----------------------------------

Vérifier la connexion réseau :

.. code-block:: bash

   ip a

Tester l’accès Internet :

.. code-block:: bash

   ping -c 3 google.com

---

Activation de l’accès SSH (optionnel)
-------------------------------------

Installer le serveur SSH :

.. code-block:: bash

   sudo apt install openssh-server

Vérifier le statut :

.. code-block:: bash

   systemctl status ssh

---

Conclusion
----------

À l’issue de ces étapes, Ubuntu 22.04 est correctement installé
et configuré sur la Raspberry Pi 5.

Le système est maintenant prêt pour l’installation de **ROS 2 Humble**
et le déploiement des applications robotiques.
