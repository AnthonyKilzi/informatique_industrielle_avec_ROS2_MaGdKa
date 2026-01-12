=====================================================
Description du Matériel de notre maquette Pantographe
=====================================================

Dans cette partie nous alons décrire les éléments de la platforme pantographe. Comme vu dans la partie précédente, notre maquette est constitué d'une **Raspberry Pi 5** pour le calcul, un stockage **NVMe haute vitesse** pour la réactivité du système, et des servomoteurs **Dynamixel** pour la partie mécanique.

-----------------------------------------------------

1. Unité de Contrôle et Gestion Thermique
=========================================

Raspberry Pi 5 (`Raspberry Pi 5 datasheet <https://www.raspberrypi.com/products/raspberry-pi-5/>`_)
--------------
C'est l'élément central qui va assurer le traitement des données et le contrôle des moteurs.


- Broadcom BCM2712 2.4GHz quad-core 64-bit Arm Cortex-A76 CPU, with cryptography extensions, 512KB per-core L2 caches and a 2MB shared L3 cache
- VideoCore VII GPU, supporting OpenGL ES 3.1, Vulkan 1.2
- 4Kp60 HEVC decoder
- Dual 4Kp60 HDMI® display output with HDR support
- LPDDR4X-4267 SDRAM (2GB, 4GB, 8GB, and 16GB)
- Dual-band 802.11ac Wi-Fi®
- 2 × USB 3.0 ports, supporting simultaneous 5Gbps operation
- 2 × USB 2.0 ports
- 5V/5A DC power via USB-C, with Power Delivery support
- Bluetooth 5.0 / Bluetooth Low Energy (BLE)
- microSD card slot, with support for high-speed SDR104 mode
- Gigabit Ethernet, with PoE+ support (requires separate PoE+ HAT)
- 2 × 4-lane MIPI camera/display transceivers
- PCIe 2.0 x1 interface for fast peripherals (requires separate M.2 HAT or other adapter)
- Raspberry Pi standard 40-pin header
- Real-time clock (RTC), powered from external battery


Refroidissement à l'aide d'un ventilateur
-------------------------------------
Ensuite, l'utilisaiton d'un ventilateur pour garantir un maintien des performances du processeur :

* **Type** : Radiateur en aluminium anodisé avec ventilateur intégré.
* **Voltage d'entrée** : 5V DC (fourni via le port ventilateur dédié sur Raspberry Pi 5)
* **Contrôle** : Gestion automatique par PWM via le port ventilateur dédié.
* **Performance** : 8000 RPM ± 15% et 1.09 CFM(pieds cubes par minute).

-----------------------------------------------------

2. Solution de Stockage Haute Performance
=========================================

En intégrant un SSD NVMe dans notre maquette, cela permet d'avoir de meilleures performances de stockage en temps réel. Cela améliore donc la réactivité et la fiabilité tout en réduisant les temps de latence.


SSD Adata Legend 700 (`Adata Legend 700 datasheet <https://www.adata.com/en/consumer/category/ssds/solid-state-drives-legend-700/>`_)
--------------------
* **Format** : M.2 2280 sur interface PCIe Gen3 x4.
* **Capacité** : 256 GB.
* **Performances** :
    * **Lecture séquentielle** : Jusqu'à 2000 MB/s.
    * **Écriture séquentielle** : Jusqu'à 1600 MB/s.
* **Durabilité** : 480 TBW (*Total Bytes Written*) et MTBF de 1,5 million d'heures.
* **Température de fonctionnement** : 0°C à 70°C.


-----------------------------------------------------

3. Actionneurs 
===========================

Le pantographe est articulé par des servomoteurs Dynamixel AX-12A permettant un retour d'information précis. (`AX-12A Dynamixel datasheet <https://emanual.robotis.com/docs/en/dxl/ax/ax-12a/>`_)

+--------------------------+----------------------------------------------------------+
| Caractéristique          | Spécification                                            |
+==========================+==========================================================+
| **Couple à l'arrêt** | 1.5 N.m (à 12V, 1.5A)                                    |
+--------------------------+----------------------------------------------------------+
| **Vitesse à vide** | 59 tr/min (à 12V)                                        |
+--------------------------+----------------------------------------------------------+
| **Angle de rotation** | 0° à 300° (ou rotation continue)                         |
+--------------------------+----------------------------------------------------------+
| **Résolution** | 0.29°                                                    |
+--------------------------+----------------------------------------------------------+
| **Tension d'entrée** | 9V à 12V (Recommandé : 11.1V / 12V)                      |
+--------------------------+----------------------------------------------------------+
| **Communication** | Bus TTL Multi-drop (Série asynchrone half-duplex)        |
+--------------------------+----------------------------------------------------------+
| **Retour d'information** | Position, Température, Charge, Tension                   |
+--------------------------+----------------------------------------------------------+

