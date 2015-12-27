Port-serie-sur-ethernet
=======================

remserial
---------

**remserial** est un programme permettant un accés distant au port série  (standard ou USB) d'une machine par ethernet. 
Le programme est disponible sur http://lpccomp.bc.ca/remserial/

Exemple d'usage
---------------

Expmple d'utilisation avec un modem série utlisé par le plugin domogik  **callerid** https://github.com/fritz-smh/domogik-plugin-callerid


* Sur le serveur relié au modem par exmple un Raspberry-Pi B

Lancer le programme comme ceci:

    ./remserial -d -p 23000 -s "19200 raw" /dev/ttyACM0 &
    
Le port du modem étant : /dev/ttyACM0


* Sur le serveur (VM) ou Domogik avec le plugin **callerid** tourne

    ./remserial -d -r vesta -p 23000 -l /dev/modem /dev/ptmx &
    
    
Il suffira de configurer le plugin avec le port **/dev/modem** pour accéder au modem distant.


Modification source
-------------------

Joint les sources modifées:

* Ajout log dans la syslog
* Ajout droit écriture au groupe (tty) du device série créé






