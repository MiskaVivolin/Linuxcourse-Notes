# Linux viikko 2 tehtäväraportti

Tällä viikolla varasin enemmän aikaa viikon tehtäviin ja aloitin heti tiistaina. Tutustuin parin youtube videon avulla linux logien lukemiseen jolla pääsin hyvin alkuun. Kävin läpi syslogia auth.logia ja user.logia sekä availin niitä eri tavoilla kuten tail- cat- ja less komennoilla. Tutustuin linuxiin ja tein tehtäviä arkipäivisin joka päivä ja aikaa meni yhteensä noin 6-8 tuntia.

## Kirjoitan logiin onnistuneen ja epäonnistuneen komennon 

"echo "Hello world" | systemd-cat" komento luo syslogiin 3.9.2021 kello 17:19:37 onnistuneesti tekstin "Hello World".

![image](https://user-images.githubusercontent.com/78149945/132023500-3ae6ea1b-ed9d-4de1-b5be-2b6a4278846a.png)

Komento on 3.9.2021 kello 17:19:37 tehty. systemd-cat komento luo syslogiin tarkasteltavaksi viestin.


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

### Skype

Asensin ohjelman Skype komennolla: sudo snap install skype. Skype on ohjelma jolla voi soittaa tai lähettää viestejä muille skype käyttäjille. Valitettavasti asennuksessa menee jotain pieleen. 

![image](https://user-images.githubusercontent.com/78149945/132033562-7914a9e3-d1e2-4d35-83d3-f45deb5e10d1.png)

Koin useiden ohjelmien kohdalla ongelmia asennuksessa, joista yleisin oli error: “E: Unable to locate package”

### Telegram

Telegramin asennus onnistui terminaalissa

![image](https://user-images.githubusercontent.com/78149945/132122347-4ad86d75-6358-4fb7-8d51-200c454bb56f.png)

En kuitenkaan löydä telegramia application finderista jostain syystä joten en pääse testaamaan sitä. En löydä ratkaisua, joten koitan löytää vastaavan ohjelman linuxille.

### Pigbin

Aseinsin Pigbinin komennolla: sudo apt-get install pidgin. Asennus onnistui ilman ongelmia ja ohjelma toimii normaalisti. Pigbinin avulla voin yhdellä ohjelmalla kirjautua sisään useampaan instant messaging ohjelmaan kuten esim. Google talk, IRC jne.

## Lähdeviitteet

Tero Karvinen. Linux Palvelimet ict4tn021 3016 - Autumn 2021. https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/. Luettu: 31.8.2021

Swapnil Tirthakar. Linuxhints, 100 best Ubuntu apps. https://linuxhint.com/100_best_ubuntu_apps/ Luettu: 3.9.2021

Swapnil Tirthakar. Linuxhints, How to Install Steam in Ubuntu 20.04. https://linuxhint.com/install-steamos-on-ubuntu/ Luettu: 3.9.2021

Jack Wallen. Linux.com, Viewing Linux Logs from the Command Line (18.7.2018). https://www.linux.com/topic/desktop/viewing-linux-logs-command-line/. Luettu 31.8.2021
