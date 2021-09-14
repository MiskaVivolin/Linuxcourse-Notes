# Linux viikko 3 tehtäväraportti

### a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.
Asensimme tunnilla apachen komennoilla:

![image](https://user-images.githubusercontent.com/78149945/132819195-33663e01-1163-4b1f-bc0a-bd9d1aed6615.png)

Ensin asensin apachen, sitten käynnistin sen ja sen jälkeen katson komentorivillä localhostin sisällön.

Seuraavaksi asetan omat kotisivuni näkymään localhostissa.

![image](https://user-images.githubusercontent.com/78149945/132822656-81fa6388-b972-45ef-b9c6-da898b285d7d.png)

ensin aktivoin käyttäjähakemiston apachen käyttöön, sitten restarttaan apachen jonka jälkeen teen uuden hakemiston "public_html" ja menen sinne "cd public_html" komennolla. Teen lopuksi tekstitiedoston jonne kirjoitan "Hello world". Menen nettiselaimella osoitteeseen localhost/~miskav/ jolloin näen tekstin "Hello world".

### b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.

Kirjoitin hakukoneeseen onnistuneen sivunlatauksen "localhost/~miskav" ja epäonnistuneen sivunlatauksen "localhost/~miskavgg" jonka jälkeen navigoin logeihin (/var/log). Koitan päästä  apache2 hakemiston sisään, mutta saan viestin: permission denied. Etsin googlesta mitä logeja apache2 hakemisto sisältää. Teen tämän jälkeen komennon "sudo cat apache2/access.log" josta löydän oikeat logit.

![image](https://user-images.githubusercontent.com/78149945/132829213-b5acfa14-4496-42fc-821d-e3f79a67cd51.png)

Palvelin sai onnistuneesti 10.8.2021 klo 11:21:44 HTTP GET pyynnön sivulta localhost/~miskav. Web-selaimena oli Google Chrome versio 92.0.4515.159 64-bittisellä linuxilla. En ymmärrä miksi logiin tulostuu mozilla, safari ja apple webkit vaikka käytän Chromea.

![image](https://user-images.githubusercontent.com/78149945/132829372-350f41b8-c192-476d-bb6a-26ad5a818d2a.png)

Palvelin epäonnistui 10.8.2021 klo 11:21:56 HTTP GET pyynnössä sivulla localhost/~miskavgg. URL-osoite oli siis kirjoitettu väärin. Web-selaimena oli Google Chrome versio 92.0.4515.159 64-bittisellä linuxilla. 

### d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.

Navigoin root hakemistosta etc hakemistoon ja sieltä apache 2 hakemistoon. Menen komennolla "sudo nano apache2.conf" muokkaamaan asetustiedostoa ja kirjoitan sinne virhetekstiä, jonka jälkeen tallennan tiedoston. Restarttaan apachen komennolla "sudo systemctl restart apache2" ja saan virheen
![image](https://user-images.githubusercontent.com/78149945/132832473-fc9e49ee-39ce-4750-8c95-12dbe65cd6fd.png)

Navigoin /var/log hakemistoon ja avaan syslogin komennolla "sudo less /var/log/syslog" ja löydän virheilmoituksen

![image](https://user-images.githubusercontent.com/78149945/132834135-9ad70098-7dc7-4868-ae6b-656d74f56fcb.png)

Apache selvästi yrittää käynnistyä, mutta invalid command eli virhekirjoitus pilaa kaiken. Tämän jälkeen apache http server pysähtyy ja yrittää käynnistyä vielä, mutta sekin tietenkin epäonnistuu. Lopuksi tulee vain ilmoitus "Failed to start The Apache HTTP server"

Lopuksi käyn poistamassa virheen asetustiedostosta, tallennan sen ja käynnistän onnistuneesti apachen uudelleen.

### i) Kuinka monta eri HTTP Status:ta (200, 404, 500…) saat aiheutettua lokeihin? Selitä, miten aiheutit tilanteet ja analysoi yksi rivi kustakin statuksesta.

Tein onnistuneen http statuksen samalla tavalla kuin aikaisemmin:
![image](https://user-images.githubusercontent.com/78149945/132845856-d2cf065b-e324-4385-937e-529d008c078d.png)

Epäonnistuneen tein myös samoin kun b) tehtävässä:
![image](https://user-images.githubusercontent.com/78149945/132845957-313ec9ec-5506-4370-9a36-f2011e067667.png)

Huomasin logeissani error 408 ja googletin mistä se johtuu. Error 408 tulee kun error 404 ikkuna on ollut hetken aikaa käynnissä ja selain haluaisi sulkea sen.

![image](https://user-images.githubusercontent.com/78149945/132847993-8c815501-c8db-4115-a2b2-0da16bb7c8f7.png)


Sain tänään jossain vaiheessa http error 304, mutta en tiedä miten se tuli tai miten sen aiheuttaisin tarkoituksella
![image](https://user-images.githubusercontent.com/78149945/132846342-43cf02f8-e1e0-4ffe-999f-f6349c5f7906.png)S

Error 304 logitietoja tarkastellessa huomaa että ne näyttävät täysin samalta 404 erroreihin verrattuna. Sivulla Airbrake.io sanotaan 304 errorin ilmaisevan sitä että pyydettyä resurssia ei ole muokattu viimeisen siirron jälkeen, joten sitä ei tarvitse uudelleenlähettää sivustolle.

### m) Vaihda Apachen oletussivu. Eli laita palvelimen etusivulla (ilman tildeä) näkyvä sivu niin, että alkuperäinen on jonkun käyttäjän kotihakemistossa ja voit muokata sitä ilman pääkäyttäjän oikeuksia.

Menin ensin hakemistoon "/var/www" ja tein uuden tekstitiedoston komennolla "sudo nano uusi.html"

![image](https://user-images.githubusercontent.com/78149945/132858445-8328d42c-8704-4704-bf2e-32426bbdd646.png)

Yritin vaihtaa oletussivua digitalocean.com sivulla olevien neuvojen mukaan. Tein uuden tekstitiedoston osoitteeseen /etc/apache2/sites-available/yourdomain.conf. Nimesin rivit uudelleen ja muutin DocumentRoot rivin oman html sivuni osoitteeksi.

![image](https://user-images.githubusercontent.com/78149945/132858817-920a426b-3aaa-4ab4-9311-e643d49175df.png)

Valitettavasti se ei toiminut ja saan silti Apache2 Debian Default Pagen oletuksena.

## Yhteenveto

Tehtäviin meni noin 6 tuntia ja opin niistä taas paljon uutta. Ei ollut tarvetta tehdä vaikeampia tehtäviä kun osaamiseni ei ole vielä niin edistynyttä.

## Lähteet

Tero Karvinen. Linux Palvelimet ict4tn021 3016 - Autumn 2021. https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/. Luettu: 10.9.2021

DigitalOcean. How do i remove Apache2 Ubuntu Default Page? 2021 https://www.digitalocean.com/community/questions/how-do-i-remove-apache2-ubuntu-default-page Luettu: 10.9.2021

developer.mozilla.org. 408 Request Timeout. 2021 https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/408
Luettu: 10.9.2021

Airbrake. 304 Not Modified: What It Is and How to Fix It. December 7, 2017 https://airbrake.io/blog/http-errors/304-not-modified Luettu: 10.9.2021
