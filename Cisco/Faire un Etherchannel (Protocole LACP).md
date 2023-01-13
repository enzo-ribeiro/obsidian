---
dg-publish: true
dg-home: false
---
Le lienEthercahnnel va nous servir à multiplier le débit possible sur un Switch/Router par 2.

![[Etherchannel.png]]

Pour ce genre de configuration nous aurons besoin de au moins Switch, Nous allons nous rendre sur le SW1 :
```IOS
SW1> en
SW1# conf t
Sw1(config)# int range g0/1-2
SW1(config-if-range)#channel-group 1 mode active
```
Ensuite nous allons sur le SW2 : 
```IOS
SW2> en
SW2# conf t
Sw2(config)# int range g0/1-2
SW2(config-if-range)#channel-group 1 mode passive
```

Maintenant on peut vérifier la configuration avec la commande :
```IOS
Switch# sh etherchannel 1 port-channel
```
