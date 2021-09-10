# Linux viikko 3 tehtäväraportti

### a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.
Asensimme tunnilla apachen komennoilla:
![image](https://user-images.githubusercontent.com/78149945/132819195-33663e01-1163-4b1f-bc0a-bd9d1aed6615.png)

Ensin asensin apachen, sitten käynnistin sen ja sen jälkeen katson komentorivillä localhostin sisällön.

Seuraavaksi asetan omat kotisivuni näkymään localhostissa.

![image](https://user-images.githubusercontent.com/78149945/132822656-81fa6388-b972-45ef-b9c6-da898b285d7d.png)

ensin aktivoin käyttäjähakemiston apachen käyttöön, sitten restarttaan apachen jonka jälkeen teen uuden hakemiston "public_html" ja menen sinne "cd public_html" komennolla. Teen lopuksi tekstitiedoston jonne kirjoitan "Hello world". Menen nettiselaimella osoitteeseen localhost/~miskav/ jolloin näen tekstin "Hello world".

### b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.



![image](https://user-images.githubusercontent.com/78149945/132829213-b5acfa14-4496-42fc-821d-e3f79a67cd51.png)

![image](https://user-images.githubusercontent.com/78149945/132829372-350f41b8-c192-476d-bb6a-26ad5a818d2a.png)

### d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.

Navigoin root hakemistosta etc hakemistoon ja sieltä apache 2 hakemistoon. Menen komennolla "sudo nano apache2.conf" muokkaamaan asetustiedostoa ja kirjoitan sinne virhetekstiä, jonka jälkeen tallennan tiedoston. Restarttaan apachen komennolla "sudo systemctl restart apache2" ja saan virheen
![image](https://user-images.githubusercontent.com/78149945/132832473-fc9e49ee-39ce-4750-8c95-12dbe65cd6fd.png)

Navigoin /var/log hakemistoon ja avaan syslogin komennolla "sudo less /var/log/syslog" ja löydän virheilmoituksen

![image](https://user-images.githubusercontent.com/78149945/132834135-9ad70098-7dc7-4868-ae6b-656d74f56fcb.png)

Apache selvästi yrittää käynnistyä, mutta invalid command eli virhekirjoitus pilaa kaiken. Tämän jälkeen apache http server pysähtyy ja yrittää käynnistyä vielä, mutta sekin tietenkin epäonnistuu. Lopuksi tulee vain ilmoitus "Failed to start The Apache HTTP server"
