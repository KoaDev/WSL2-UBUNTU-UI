# WSL2-UBUNTU-UI
Mettre en place l'interface graphique d'Ubuntu sous WSL2

## **Mettre a jour vos dépôts :**
```sh
$ sudo apt update && sudo apt -y upgrade
```

## **Paquet a installer :**
```sh
$ sudo apt install xrdp

$ sudo apt install -y xfce4
(Quand demandé choisir le display manager 'gdm3')

$ sudo apt install -y xfce4-goodies
```

## **Configuration de XRDP :**
**Exécutez les commandes suivantes :**
```sh
$ sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak

$ sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
$ sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
$ sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini

$ echo xfce-session > ~/.xsession
```
```
$ sudo nano /etc/xrdp/startwm.sh
```
**A la fin du fichier commentez les deux dernières lignes :**
```
test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec /bin/sh /etc/X11/Xsession
```
**Et ajoutez :**
```
# xfce
startxfce4
```
 **Enfin démarrez XRDP :**
```sh
$ sudo /etc/init.d/xrdp start
```
## **Coté Windows :**
**Démarrez l'application suivante** 

```
Remote Desktop Connection
```

**Dans le champ 'Computer' écrivez :** 
```
localhost:3390
```

**Enfin connectez vous, et vous entrerez vos information de connexion UNIX dans les champs :**
```
[!] NE TOUCHER PAS LE CHAMPS SESSION [!]
username
password
```
