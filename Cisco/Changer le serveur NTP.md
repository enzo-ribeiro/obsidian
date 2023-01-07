Le serveur NTP est hébergé sur une machine virtuelle Debian 10.
On se retoruve sur mon Switch :
```IOS
Switch> en
Switch# sh clock
*00:02:01.198 UTC Mon Mar 1 1993
```
Donc maintenant il faut déclarer le serveur NTP à notre Switch/Routeur
```IOS
Switch(config)# ntp server 172.25.193.34
```

Une fois la déclaration de notre serveur NTP fait il faut changer la date et l'heure du Switch/Routeur:
```IOS
Switch# clock set 13:07:54 06 Jan 2023
```

Après ca on vérifie que le serveur NTP soit bien déclaré avec la commande :
```IOS
Switch#sh ntp assoc

	   address         ref clock     st  when  poll reach  delay  offset    disp
 ~172.25.193.34    0.0.0.0          16     -    64    0     0.0    0.00  16000.
 * master (synced), # master (unsynced), + selected, - candidate, ~ configured
```
il est bien déclaré maintenant il manque plus qu'a attendre un petit peu que devant le `<~>` l'étoile de `<master>` apparaisse.

```IOS
Switch#sh ntp assoc

      address         ref clock     st  when  poll reach  delay  offset    disp
*~172.25.193.34    162.159.200.123  16    59    64    1     3.0   -0.84     0.9
 * master (synced), # master (unsynced), + selected, - candidate, ~ configured
```
Et voici le résultat final.