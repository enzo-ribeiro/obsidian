Les ACLs de ce type ne sont liée qu'à l'adreese IP source. Ce sont ces ACLs qui sont idenfiables par les ID de 1 à 99 et 1300 à 1999.

Avec ce type d'ACLs nous pourrons autoriser ou interdire un segment de réseau ou l'adresse IP d'une machine à communiquer avec un autre segment ou autre machine. 

![ACLs_Standars_1.png]

Ici toutes les machines sont sur des segments réseau différents, elles peuvent communiquer entre elles grâce à des routes. Le but ici va être d'interdire au réseau `<10.1.1.0/24>` de communiquer avec le réseau `<10.1.2.0/24>` sans interdire la communication avec le réseau `<10.1.3.0/24>`. Pour ce faire on va se rendre sur l'interface Gi0/2 afin d'interdire les paquets en provenance du réseau `<10.1.1.0/24>`.
```IOS
Router> en
Router# conf t
Router(config)# access-list 1 deny 10.1.2.0 0.0.0.255
```
Ici `<access-list 1>` donne un ID à l'ACL, ensuite on prcise `<deny>` afin de refuser les paquets en direction du réseau `<10.1.2.0>` et pour finir le `<wildcards mask>` (c'est le masque sous réseau mais inversé). (Voir la fin pour explication de la commande)

Mais la on rencontre un problème ... Le ping de `<10.1.1.10>` vers `<10.1.2.20>` est positif : 
![[ACLs_Standars_OK.png]]

Pas de panique cela est normal. Il faut se rendre sur l'interface désiré. Donc nous allons aller sur l'interface Gi0/1 et activer la règle.
```IOS
Router(config)# int Gi0/1
Router(config-if)# ip access-list 1 out
```
Ici `<access-list 1>` donne l'ID de l'ACL que nous voulons transmettre à notre interface. Le `<out>` signifie que la règle s'applique sur les paquets sortant.

![[ACLs_Standars_pas_OK.png]]
Et voilà la règle est bien appliqué car nous ne pouvons pas ping le réseau `<10.1.2.0/24>`. 


Pour info : 
Les règles d'ACLs se constituent comme ci-dessous :
```IOS
Router> en
Router# conf t
Router(config)# access-list <ID> <permit/deny> <@_IP_réseau> <Wildcards_mask>
```
