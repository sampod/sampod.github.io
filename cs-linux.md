# sampod.github.io
Sami Heino's Linux cheat sheet
  eli Linux-lunttilappu!
http://gh.heino.cc

Linux-komentoja
---------------

Hyvä tietopankki suomenkielellä: [Linux.fi wiki](http://linux.fi/wiki).

`ethtool eth0` näyttää tietoja eth0:n tilasta.

`# ethtool -s eth0 speed 100 duplex full` Asettaa eth0:n 100M nopeudelle.

`chmod -R a+rX *` asettaa kaikille lukuoikeudet kaikkiin tiedostoihin sekä hakemistoihin.

`screen /dev/ttyUSB0 115200` avaa sarjaliikenneportin screeniin.

`sdiff -o outfile from-file to-file`\
vertaa tiedostoja *from-file* ja *to-file* sekä antaa valita tiedostoista sisällön tiedostoon *outfile*. Oma suosikkini Arch Linuxin konffitiedostojen päivittämiseen (.pacnew).

`Nmap` perussyntaksi, oman lähiverkon skannaus: `$ nmap -sP 192.168.1.1/24`



`ntpq -p` näyttää ntpd:n tilan.

`ifconfig` näyttää koneen verkkoasetukset, lisäksi lisätietoja voi onkia komennolla `ip` esim. `ip route show`.

`which` näyttää ohjelman koko polun, esimerkiksi `which sh`.

SCP perussyntaksi: `scp ~/.hakemisto/tiedosto palvelin.fi:~/.hakemisto/`

Kiintolevyn partition tablen tyhjentäminen: `dd if=/dev/zero of=/dev/hdx bs=512 count=1`\
**ÄLÄ KÄYTÄ JOS ET TIEDÄ MITÄ TEET!**

Kiintolevyn nopeuden testaaminen: `hdparm -t /dev/sdx`,\
jossa sdx on aseman tunnus.

imagemagick-velhoutta: `mogrify -quality 50 -resize 640 *.jpg`,\
muuntaa kaikki jpg-päätteiset tiedostot 640 pikseliä leveiksi jpg-laatuun 50.

* * * * *

apt-get ongelmat
----------------

Monet apt-get -päivitysongelmat ratkeaa kommennoilla\
`sudo apt-get clean\
sudo apt-get update`\
Yleensä tällä korjaantuvat viat on niitä joihin liittyy "returned error exit status 2"-virheilmo.

* * * * *

### KDE numlockin alkutila

`K-valikko -> system settings -> (hardware) input devices -> keyboard -> hardware-välilehti -> numlock on KDE startup` Tuosta saa valita numlockin alkutilan.

* * * * *

SpamAssassin
------------

Kapsin palvelimilla alkuun pääsee hyvin Kapsin omilla [SpamAssassin-ohjeilla](http://www.kapsi.fi/ohjeet/spamassassin.html). Käy läpi myös ohjesivuston linkit suodattimen opettamiseen liittyen. Ohjeet lienee myös sovellettavissa pienillä muutoksilla muuallakin. Ohessa tärkeimmät komennot, joita voi käyttää kun perusasetukset on tehty ohjeen mukaan:

`sa-learn --spam --mbox mail/Spam`\
opettaa suodattimelle roskapostit Spam-kansiosta.

`sa-learn --ham --mbox mail/Ham`\
opettaa suodattimelle asiaviestit Ham-kansiosta.

`sa-learn --dump magic`\
näyttää tietoja SpamAssassinin toiminnasta.

* * * * *

Encfs ja rsync yhteistyö
------------------------

Seuraavassa vaiheet kryptatun varmuuskopion luomiseen ja siirtoon.\
1) Muodostetaan kryptattu hakemisto\
2) Siirretään kryptatut tiedot palvelimelle rsyncillä\
3) Poistetaan kryptattu hakemisto omalta koneelta\
`encfs --reverse /home /tmp/crypt-home\
rsync -a -v -e ssh --delete --progress /tmp/crypt-home/ user@server:siilo/backup/home/\
fusermount -u /tmp/crypt-home\
`

Kryptattavaan hakemistoon ilmestynyt .encfs6.xml kopioidaan talteen vaikka usbitikulle. Ilman sitä ja salasanaa ei kryptausta saa purettua!

Kryptatun varmuuskopion palautus:\
Siirrä ensiksi kryptattu varmuuskopio palvelimelta hakemistoon /tmp/crypt-view/\
`ENCFS6_CONFIG=/media/foo/.encfs6.xml encfs /tmp/crypt-view /tmp/plain-view`

### Linkkejä aiheesta:

[man encfs\
](http://pwet.fr/man/linux/commandes/encfs)[encfs intro](http://www.arg0.net/encfsintro)\
[linux.com](http://www.linux.com/archive/feed/52820)

python3
-------
 venv luonti\
`sudo python3 -m venv system_sensors/`\
tarvitaan ainakin \
`sudo apt-get install python3-venv  build-essential python3-dev`\
`pip3 install wheel`
