---
dg-publish: true
dg-home: false
---
Voila la maquette dont nous avons besoin pour faire un lien trunk :
![2 Ordinateurs + 1 Switch](1.PNG)

Pour faire un lien trunk nous allons créer 2 VLANs le 10 et le 20.
Nous nous rendons donc sur le Switch afin de créer les deux VLANs :
```IOS
Switch> en
Switch# conf t
Switch(config)# vlan 10
Switch(config)# ex
Switch(config)# vlan 20
Switch(config)# ex
```

Une fois les VLANs créé on assigne les ports aux VLANs : 
```IOS
Switch(config)# int fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# swtichport access vlan 10
Switch(config-if)# ex
Switch(config)# int fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# swtichport access vlan 20
```

Pour commencer nous allons créer un VLAN qui servira de VLAN natif aux ports trunk. 
```IOS
Switch(config)# vlan 100
Switch(config)# int Gi0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk native vlan 100
Switch(config-if)# switchport trunk allowed vlan 10,20
```

Et voila votre lien trunk sur l'interface GigabitEthernet 0/1 est enfin créé.