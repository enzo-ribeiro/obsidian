
Sur une machine Debian 10 installer un serveur NTP
```bash
sudo -s
apt install chrony
```

A partir de ce moment la on doit vérifier le contenu de "chrony.conf"

``` bash
nano /etc/chrony/chrony.conf
```

Ensuite nous devons déclarer nos pool NTP donc nous allons nous rendre à la ligne 3 pour faire ajouter ces modification : 
```
pool 2.debian.pool.ntp.org iburst
```
devient :
```shell
#pool 2.debian.pool.ntp.org iburst"
```
et maintenant nous pouvons ajouter nos pool en entrant les lignes suivantes :
```shell
server 0.fr.pool.ntp.org
server 1.fr.pool.ntp.org
server 2.fr.pool.ntp.org
server 3.fr.pool.ntp.org
```

Une fois cela fait on va pouvoir se rendre un peut plus bas pour vérifier l'existance (ou non) des lignes suivantes:
```shell
# This directive specify the file into which chronyd will store the rate
# information.
driftfile /var/lib/chrony/chrony.drift
local stratum 8
manual
allow 172.25
```
Si ces lignes ne sont pas présente il faudra les rajoutés.

Le "local stratum 8" déclare la "couche" de notre serveur NTP.
Pour terminer cette installation il faut lancer le serveur.

```shell
systemctl start chrony
```
on vérifie si tout fonctionne correctement : 
```shell
systemctl status chrony
```
et ici la commande sert à activer le service à chaque fois que la machine est allumé :
```shell
systemctl enable chrony
```
