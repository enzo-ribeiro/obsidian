Ce tuto va servir au cas où il y'a un mot de passe qui bloque l'accès au Switch que vous désirez configurer. En effet il se peut que sur votre parcour il y'ai des switch dont vous n'avez pas le mot de passe il faudra donc executer la méthode si dessous.

Pour commencer il faudra vous connectez avec un câble console (en physique) et appuyer sur le bouton `<Mode>` en façade du Switch jusqu'a ce que la LED `<SYST>` clignote. 
Ensuite vous aurez un menu spécial qui ressemble à ca : 

```IOS
Jan  6 07:53:04.222: %SYS-5-RELOAD: Reload requested by Hulc LED Process. Reload
Boot Sector Filesystem (bs) installed, fsid: 2
Base ethernet MAC Address: d4:a0:2a:96:5c:00
Xmodem file system is available.
The password-recovery mechanism is enabled.

The system has been interrupted prior to initializing the
flash filesystem.  The following commands will initialize
the flash filesystem, and finish loading the operating
system software:

    flash_init
    boot


switch:  
```

Une fois que ce menu est apparu ont peut commencer la réinitialisation du Switch.
```IOS
switch: flas_init

Initializing Flash...
flashfs[0]: 542 files, 19 directories
flashfs[0]: 0 orphaned files, 0 orphaned directories
flashfs[0]: Total bytes: 32514048
flashfs[0]: Bytes used: 11561472
flashfs[0]: Bytes available: 20952576
flashfs[0]: flashfs fsck took 10 seconds.
...done Initializing Flash.
```

Maintenant il manque plus qu'à démarrer le Switch et vous aurez une config vierge.
```IOS
switch: boot   
```

Le Switch va démarrer et vous pourrez faire votre configuration ;)