Sur une machine Debian 10 installer un serveur TFTP 
```bash
sudo -s
apt install xinetd tftpd tftp
```

Une fois le service installer il faut se créer un fichier de conf : 
```bash
nano /etc/xinetd.d/tftp
```
et ajouter les lignes suivantes : 
```bash
service tftp
{
protocol    	= udp
port        	= 69
socket_type 	= dgram
wait        	= yes
user        	= nobody
server      	= /usr/sbin/in.tftpd
server_args 	= /tftpboot
disable     	= no
}
```

Maintenant il faut créer un répertoire du nom de /tftpboot à la racine, il faudra également lui donner des droit :
```bash 
sudo mkdir /tftpboot
sudo chmod -R 777 /tftpboot
sudo chown -R nobody /tftpboot
```

Ensuite il faut redémarrer le service :
```bash
sudo /etc/init.d/xinetd restart
```

# Facultatif selon ce que vous souhaitez faire (ici on fait un TFTP de sauvegarde pour les Switchs/Routeurs)


Pour la suite il va falloir créer un fichier qui contiendra les fichiers :
```shell
touch /tftpboot/<nom_du_routeur-ou-switch>
```
Puis nous allons également lui donner les droits :
```shell
chmod 777 /tftpboot/<nom_du_routeur-ou-switch
```

Ensuite nous nous redons sur le Switch/Routeur :
```IOS
Switch> en
Switch# copy running-config tftp
## Cette commande vous posera 2 question:
1- @ IP du TFTP
2- La destination du fichier soit /tftpboot/<nom_du_routeur-ou-switch>
```

Une fois cela fait nous nous rendons sur la machine debian qui héberge le service tftp :
```shell
cat /tftpboot/<nom_du_routeur-ou-switch
```

