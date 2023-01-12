---
dg-publish: true
dg-home: false
---
Pour commencer nous allons créer un VLAN qui servira de VLAN natif aux ports trunk. On va également autoriser les VLANs à passer par ce port (dans mon cas c'est les vlan 10 et  20) : 
```IOS
Switch(config)# vlan 100
Switch(config)# int Gi0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk native vlan 100
Switch(config-if)# switchport trunk allowed vlan 10,20
```

Et voila votre lien trunk est enfin créé.