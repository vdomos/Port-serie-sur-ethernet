Port-serie-sur-ethernet
=======================

remserial
---------

**remserial** est un programme permettant un accés distant au port série  (standard ou USB) d'une machine par ethernet. 
Le programme est disponible sur http://lpccomp.bc.ca/remserial/

Exemple d'usage
---------------

Expmple d'utilisation avec un modem série utlisé par le plugin domogik  **callerid** https://github.com/fritz-smh/domogik-plugin-callerid


* Sur le serveur relié au modem 

Par exemple sur un Raspberry-Pi B. Le port du modem étant /dev/ttyACM0 et 2300 un port IP libre:

    ./remserial -d -p 23000 -s "19200 raw" /dev/ttyACM0 &
    


* Sur le serveur ou Domogik tourne avec le plugin **callerid**:

Dans mon exemple sur VM Domogik:

    ./remserial -d -r hostname-ou-@IP_rpi -p 23000 -l /dev/modem /dev/ptmx &
    
    
* Test du modem

Le "user" utlisant le modem  doit appartenir au groupe 'tty'

    $ picocom -b 19200 -d 8 -f n -p n /dev/modem
    picocom v1.7
    port is        : /dev/modem
    flowcontrol    : none
    baudrate is    : 19200
    ...
    Terminal ready
    ATZ
    OK
    ATI3
    CX93001-EIS_V0.2002-V92

* Sous domogik

Il suffira de configurer le plugin avec le port **/dev/modem** pour accéder au modem distant.


Modification source
-------------------

Joint les sources modifées:

* Ajout log dans la syslog
* Ajout droit écriture au groupe (tty) du device série créé


    




