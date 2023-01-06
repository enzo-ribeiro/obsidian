
Pour ce TP nous utilisons un serveur RSysLog hébergé par une machine debian. 
```IOS
Switch> en
Switch# conf t
Switch(config)# logging <@_IP_RSysLog>
```

Et voilà c'est fait vos log serons hébergé par le serveur RSysLog.

```Shell
cat /var/log/Switch/forwarded-logs.log
Jan  6 13:24:16 172.25.193.35 34: Jan  6 12:24:15.205: %LINK-5-CHANGED: Interface FastEthernet0/20, changed state to administratively down
Jan  6 13:24:17 172.25.193.35 35: Jan  6 12:24:16.211: %SYS-6-LOGGINGHOST_STARTSTOP: Logging to host 172.25.193.34 Port 514 started - CLI initiated
```
Voici le résultat final sur le shell de Debian
