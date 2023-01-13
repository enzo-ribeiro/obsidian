---
dg-publish: true
dg-home: false
---
Le VTP est un protocole qui permet une distribution des VLAN aux switchs faisant parti du domaine  
VTP et ayant les identifiants du switch VTP serveur. Le VTP passe par les liaisons trunk.

Pour commencer nous allons prendre une maquette réalisé avec packet tracer : 
![[Cisco/Switch/Image/1.PNG]]

Nous allons nous rendre sur Switch6 pour créer nos VLAN :
```IOS 
Switch> en
Switch# conf t
Switch(config)# vlan 10
Switch(config-vlan)# ex
Switch(config)# vlan 20
Switch(config-vlan)# ex 
Switch(config)# vlan 30
Switch(config-vlan)# ex
```

Une fois créé on va pouvoir faire nos liens trunk :
Voici le lien du "tuto" :
- [[Comment faire un lien trunk]]

Une fois les liens trunk réalisé nous pouvons commencer la réalisation du serveur VTP. Rendez-vous sur le Switch6.

```IOS
Switch> en
Switch# conf t
Switch(config)#vtp mode server
Switch(config)#vtp domain <ndd_de_votre_choix>
```
Pour plus de sécurité il est possible d'ajouter un mot de passe avec la commande :
```IOS
Switch(config)#vtp password <P@550wRd>
```

A partir de maintenant on va se rendrez sur les switch qui nous interèsse pour taper les commandes suivantes :
```
Switch> en
Switch# conf t
Switch(config)#vtp mode client
Switch(config)#vtp domain <ndd_choisi>
```
et évidemment si vous avez mis un mot de passe  : 
```IOS
Switch(config)#vtp password <P@550wRd>
```
avec la commande 
```IOS
Switch# sh vlan
```
On peut voir les VLAN existant donc on se rend sur le Switch8 (Switch client) et taper la commande voila le résultat. 
![[Cisco/Switch/Image/2.PNG]]
 Et voila votre serveur VTP est fonctionnel.