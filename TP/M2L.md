---
dg-publish: true
dg-home: true
---
Ligue (VLAN) :
- 80 VLAN de 32 @ (modifiable avec VLSM)
#172.16.0.1/27 #172.16.9.254/27

VLAN public wi-fi :
- 4 096 @ 
#172.16.16.1/20 #172.16.31.254/20

Administration : 
- 27 @ (27 prises Ethernet)
#172.16.10.1/27 #172.16.10.30/27

Reprographie : 
- 4 @ (4 prises Ethernet)
#172.16.10.33/27 #172.16.10.62/27

Multimédia :
- 26 @ (26 prises Ethernet)
#172.16.10.65/27 #172.16.10.94/27

Salle de ressources (VLAN "public" filaire) :
 - Amphitéatre (5 prises )
 - Salle de réunion (16 prises Ethernet)
 - Salle de convivialité (0 prise)
#172.16.10.97/27 #172.16.10.126/27

Ecrans :
- 4 @ (3 prises Ethernet)
#172.16.10.129/27 #172.16.10.158/27

DMZ : 
- 3 @ (3 prises Ethernet)
#10.54.0.1/24 #10.54.0.31/24

Management : 
- 12 @ (Switch, Routeurs ... )
#172.16.10.193/27 #172.16.10.222/27
