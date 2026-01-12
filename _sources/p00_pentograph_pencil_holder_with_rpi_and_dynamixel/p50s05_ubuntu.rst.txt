###################################################
 Installation de ROS2 sur la Rasberry Pi 5
###################################################

Puisque nous avons installé **Ubuntu version 24.04**, il faut installer la version **Jazzy** de **ROS2**. Pour cela, il faut suivre les étapes décrites dans cette documentation_ en prenant soin de remplacer par **Jazzy** là où il est nécessaire.

Voici la liste des commandes à effectuer :

.. code-block:: bash
    
    locale  # check for UTF-8

    sudo apt update && sudo apt install locales
    sudo locale-gen en_US en_US.UTF-8
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    export LANG=en_US.UTF-8

    locale  # verify settings

    sudo apt install software-properties-common
    sudo add-apt-repository universe

    sudo apt update && sudo apt install curl -y
    sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

    sudo apt update

    sudo apt upgrade

    sudo apt install ros-humble-desktop

    sudo apt install ros-humble-ros-base

    source /opt/ros/rolling/setup.bash

Après installation, on teste le bon fonctionnement de **ROS2** à l'aide de **TurtleSim** dans un nouveau terminal :

.. figure:: resources/img/TurtleSim.png
    :width: 50%
    :align: center

.. _documentation: https://ros2docs.robook.org/rolling/Installation/Ubuntu-Install-Debs.html