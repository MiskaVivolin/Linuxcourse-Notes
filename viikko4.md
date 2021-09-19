# Linux viikko 4 tehtäväraportti

### a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.

Aloitin tekemällä paypal accountin, koska omistan vain debit cardin. Yhdistin Digital oceanin Githubiin ja sain suoraan 100 dollaria käytettäväksi 2 kuukauden ajaksi, sillä olen ottanut käyttöön Githubin student packin. "Create a droplet" kohdasta valitsin ensimmäiseksi 64 bittisen Debianin 10:nen. Otin sen jälkeen Basic planin ja datacenter regioniksi Amsterdamin. authentication kohdassa valitsin passwordin ja asetin pitkän vahvan salasanan. Annoin hostnamen lopuksi, joka ei johda nimeeni.

### b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.

Katson neuvoja `terokarvinen.com - First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS`-sivulta. Aloitan tulimuurin asentamisen kirjoittamalla terminaaliin `ssh root@178.62.212.176`, jonka jälkeen kirjoitan `yes`. Terminaali kysyy IP osoitteen salasanaa jonka oikein kirjoitettuani pääsen palvelimelleni terminaalissa.
![image](https://user-images.githubusercontent.com/78149945/133263667-c894095f-77f4-47a2-9f7a-8652fbb36858.png)
Suoritan komennot `sudo apt-get update` ja `sudo apt-get upgrade`. Komennolla `sudo apt-get 
install ufw` asensin ufw:n. syötän komennot `sudo ufw allow 22/tcp` ja `sudo ufw enable`, joilla tein reiän ja aktivoin tulimuurin.

Seuraavaksi teen komennolla `sudo adduser jorma` uuden käyttäjän ja tälle hyvän salasanan. En anna tarkempaa infoa käyttäjälle ja painan `y`. Lisään uuden käyttäjän sudoon komennolla `sudo adduser jorma sudo`. Annan vielä käyttäjälle admin oikeudet komennolla `sudo adduser jorma adm`. Suoritan komennon `ssh jorma@178.62.212.176` ja annan käyttäjän salasanan, jolloin pääsen käyttäjällä palvelimelle. 

![image](https://user-images.githubusercontent.com/78149945/133277153-66fc3345-ed16-48fd-9bd9-b5fffb0f3dcd.png)

Seuraavaksi syötän komennon sudo usermod --lock root ja annan käyttäjän salasanan. syötän komennon sudo nano /etc/ssh/sshd_config ja muutan PermitRootLogin `yes` arvon `no` arvoksi.

![image](https://user-images.githubusercontent.com/78149945/133278927-f1b447ac-a688-434a-ae07-e0ede9f57f49.png)

Tallennan tiedoston ja poistun jonka jälkeen syötän komennon sudo service ssh restart. Lopuksi syötän varmuuden vuoksi komennot `sudo apt-get update` ja `sudo apt-get upgrade`.

### c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.

Syötän komennon `sudo apt-get install apache2` ja annan salasanan. Apache asentui onnistuneesti niin käynnistän sen komennolla `sudo systemctl start apache2`. Syötän seuraavaksi komennon `sudo ufw allow 88/tcp` Tarkistan toimiiko sivuni menemällä web browseriin ja antamalla hakukenttään IP osoitteeni. Apachen oletussivu tulee näkymiin, joten menen terminaalissa osoitteeseen `/etc/apache2/sites-available`. Tutkin eri tiedostoja ja tein konfigurointi-tiedostosta uuden kopion komennolla `sudo cp 000-default.conf mywebsite.conf`. Siirryn muokkaamaan uutta tiedostoa komennolla `sudo nano mywebsite.conf`. kirjoitin tekstitiedostoon servername (ip-osoite) ja serveralias (ip-osoite). Asetin myös DocumentRoot kohtaan `/home/jorma/public_html` ja kirjoitin lopuksi `<Directory /home/jorma/public_html> all granted </Directory>`, jolla annoin oikeudet tähän käyttäjähakemistoon. Lopuksi tallensin ja suljin tiedoston. 
![image](https://user-images.githubusercontent.com/78149945/133593957-c09ab77e-9f59-426e-82ea-ac73f665b58a.png)

Daniel Tarsalainen antoi neuvoa äskeisessä kohdassa, koska koin ongelmia samantyylisessä tehtävässä viime viikolla. Aktivoin vielä nettisivuni komennolla `sudo a2ensite mywebsite.conf`. Menen osoitteeseen `/home/jorma` ja luon hakemiston `public_html`, jonka jälkeen teen sinne uuden tekstitiedoston `sudo nano index.html` komennolla. Kirjoitan testiviestin "MOIIII" ja restarttaan vielä apachen komennolla `sudo systemctl restart apache2`. Kokeilen nyt mennä web browserilla ip-osoitteeseeni ja saan sivuni näkyviin onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/133594917-2e47c816-f354-4cb9-9439-f7dc464e649d.png)

### d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.

![image](https://user-images.githubusercontent.com/78149945/133932782-892bef37-d805-4dc7-a8da-8bc92164f62d.png)

19.9 klo 00:18:27 palvelimelle on yritetty päästä IP-osoitteesta 218.92.0.201

![image](https://user-images.githubusercontent.com/78149945/133932912-0ae42289-ca15-4ea0-b200-06f1c490494d.png)

19.9 klo 00:38:18 käyttäjänimi on kirjoitettu väärin tunkeutuessa.

![image](https://user-images.githubusercontent.com/78149945/133932830-d99d714c-617a-48ec-9b3f-3e49713c2b78.png)

19.9 klo 00:35:21 tunnistautuminen on epäonnistunut. 



