#########################################################
Fonctionnement des Dynamixels
#########################################################

********************************************************
Branchement des moteurs
********************************************************

Les moteurs Dynamixel sont connectés en série (daisy chain). Chaque moteur a une adresse unique pour être contrôlé séparément. Assurez-vous que les câbles d'alimentation et de données sont bien branchés.

La communication entre la Raspberry Pi et les moteurs passe généralement par un convertisseur USB, par exemple l'U2D2.

.. note::

   Voir la documentation_ pour les détails de branchement et la description de l'U2D2.


********************************************************
Préparation des fichiers
********************************************************

Après avoir branché les moteurs et l'U2D2, préparez votre espace de travail et les fichiers nécessaires :

#. Créez un workspace ROS 2 :

   .. code-block:: bash

      mkdir -p ~/ros2_ws/src
      cd ~/ros2_ws/src

#. Clonez le SDK Dynamixel :

   .. code-block:: bash

      git clone -b $ROS_DISTRO-devel https://github.com/ROBOTIS-GIT/DynamixelSDK

   .. note::
      Si la variable `$ROS_DISTRO` pose problème, remplacez-la par votre version (par ex. Jazzy).

#. Compilez le workspace :

   .. code-block:: bash

      cd ~/ros2_ws
      ros2_build

#. Vérifiez le port USB et ajoutez les permissions si nécessaire :

   .. code-block:: bash

      ls /dev/tty*
      sudo usermod -aG dialout <votre_compte>

   .. note::
      Pour connaître votre compte :

      .. code-block:: bash

         whoami


********************************************************
Adapter le code pour nos moteurs
********************************************************

Les exemples du SDK ciblent souvent des modèles Xseries (XL430, etc.). Pour des moteurs AX-12, adaptez quelques paramètres dans `read_write_node.cpp` (dans `~/robotis_ws/src/DynamixelSDK/dynamixel_sdk_examples/src` si vous avez suivi l'organisation ci-dessus).

Modifiez les adresses de la table de contrôle en remplaçant les constantes par celles des AX-12, par exemple :

.. code-block:: cpp

   // Exemples d'adresses (vérifiez la datasheet pour AX-12)
   #define ADDR_TORQUE_ENABLE 24
   #define ADDR_GOAL_POSITION 30
   #define ADDR_PRESENT_POSITION 36

Consultez le tableau "Control Table of RAM Area" dans la datasheet_ pour les adresses exactes.

Changez aussi la version du protocole si nécessaire :

.. code-block:: cpp

   #define PROTOCOL_VERSION 1.0

Et mettez le `baudrate` adapté à vos moteurs (par ex. 115200 si besoin).

Le fichier modifié est fourni en ressource :

:download:`read_write_node.cpp <resources/read_write_node.cpp>`


********************************************************
Mise en route
********************************************************

Sourcez le workspace et rebuild si besoin :

.. code-block:: bash

   cd ~/robotis_ws && source install/setup.bash
   ros2_build


Lancez la node d'exemple :

.. code-block:: bash

   ros2 run dynamixel_sdk_examples read_write_node

Dans un autre terminal, vous pouvez commander ou lire la position d'un moteur :

.. code-block:: bash

   # commander le moteur 1 à la position 1000
   ros2 topic pub -l /set_position dynamixel_sdk_custom_interfaces/SetPosition "{id: 1, position: 1000}"

.. code-block:: bash

   # récupérer la position du moteur 2
   ros2 service call /get_position dynamixel_sdk_custom_interfaces/srv/GetPosition "id: 2"


.. _logiciel: https://emanual.robotis.com/docs/en/software/dynamixel/dynamixel_wizard2/
.. _tutoriel: https://www.youtube.com/watch?v=E8XPqDjof4U
.. _datasheet: https://emanual.robotis.com/docs/en/dxl/ax/ax-12a/
.. _documentation: https://emanual.robotis.com/docs/en/parts/interface/u2d2/