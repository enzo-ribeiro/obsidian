---
dg-publish: true
dg-home: false
---
Ici nous aurons besoin de un seul switch.
Donc nous allons choisir l'interface que nous voulons sécuriser ici ca sera la GigabitEthernet0/1 :
```IOS
R1> en
R1# conf 
R1(config)# interface G0/1
R1(config-if)# switchport mode access
R1(config-if)# switchport port-security
```

 Ensuite on va pouvoir définir les adresses Mac autorisées :
 On peut autoriser un nombre précis d'adresses MAC, ici on va en mettre 5 
 ```IOS
R1> en
R1# conf 
R1(config)# interface G0/1
R1(config)# switchport port-security maximum 5 
 ```
 
 Les adresses MAC apprises peuvent être **inscrites dynamiquement dans la configuration courante `<running-config>` avec le mot clé `<sitcky>` :
```IOS 
R1(config)# switchport port-security mac-address sticky
 ```

Pour finir on a une 3ème règle qui consiste à autorisé une adresse MAC :
```IOS 
R1(config)# switchport port-security mac-address <@_MAC>
```

En cas de non respect nous pouvons mettre une "sanction":
```IOS 
R1(config)# switchport port-security
violation {protect | restrict | shutdown}
```

-   Mode protect : dès que la “violation” est constatée, le port arrête de transférer le trafic des adresses non autorisées sans envoyer de message de log.
-   Mode restrict : dès que la “violation” est constatée, le port arrête de transférer le trafic des adresses non autorisées et transmet un message de log.
-   Mode shutdown : dès que la “violation” est constatée, le port passe en état err-disabled (shutdown) et un message de log est envoyé.