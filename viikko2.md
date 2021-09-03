# Linux viikko 2 tehtäväraportti

Tällä viikolla varasin enemmän aikaa viikon tehtäviin ja aloitin heti tiistaina. Tutustuin parin youtube videon avulla linux logien lukemiseen jolla pääsin hyvin alkuun. Kävin läpi syslogia auth.logia ja user.logia sekä availin niitä eri tavoilla kuten tail- cat- ja less komennoilla.

## Kirjoitan logiin onnistuneen ja epäonnistuneen komennon 

"echo "Hello world" | systemd-cat" komento luo syslogiin 3.9.2021 kello 17:19:37 onnistuneesti tekstin "Hello World".

![image](https://user-images.githubusercontent.com/78149945/132023500-3ae6ea1b-ed9d-4de1-b5be-2b6a4278846a.png)

systemd-cat komento luo syslogiin tarkasteltavaksi viestin.


Kirjottaessani sudo salasanan väärin saan auth.logiin viestin: 

![image](https://user-images.githubusercontent.com/78149945/132023232-cee31ed1-ce4d-46a5-b140-83a9ca65bd0e.png)

virhe on 3.9.2021 kello 17:33:28 tehty. authentication failure tarkoittaa että salasana on väärin. ruser on käyttäjä joka yritti kirjautua ja user tarkoittaa varmaan samaa.

## Asennan yhdellä komentorivillä suosikkiohjelmani linuxiin

Suosikkiohjelmani Steamin asensin katsomalla ohjeita sivulta https://linuxhint.com/install-steamos-on-ubuntu/.

Steamin asennusta varten pitää tarkistaa että multiverse repository on päällä komennolla: sudo add-apt-repository multiverse

Valitettavasti sain virheilmoituksen: "sudo add-apt: command not found".

Yritin silti asentaa Steamin komennolla sudo apt install steam, mutta asennus ei onnistunut.

![image](https://user-images.githubusercontent.com/78149945/132030712-dd9c61f1-a5dc-46dc-a009-245ae8c6f7f9.png)


## Asennan komentokehotteen paketinhallinnasta kolme itselleni uutta komentorivillä toimivaa ohjelmaa

Löytääkseni ohjelmia asennettavaksi käytin sivustoa: https://linuxhint.com/100_best_ubuntu_apps/.

### Synaptic

Asensin ohjelman Synaptic komennolla: sudo apt-get install synaptic. Synaptic on paketinhallintatyökalu, josta voin hakea vaikka web servereitä ja tarkastella niiden tietoja.


