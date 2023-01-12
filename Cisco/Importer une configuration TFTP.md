---
dg-publish: true
dg-home: false
---

Pour importer une configuration TFTP depuis un routeur Cisco il faut :
```IOS
Router# copy tftp running-conf
## Cette commande vous posera 3 questions :
1- @ IP du TFTP
2- La source du fichier soit /tftpboot/<nom_du_routeur-ou-switch>
3- La destination du fichier soit running-config
```

Cette note fait suite à celle ci-dessous : 
- [[TFTP]]
