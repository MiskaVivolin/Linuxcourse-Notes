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

Seuraavaksi syötän komennon sudo usermod --lock root ja annan käyttäjän salasanan. Menen osoitteeseen /etc/ssh/sshd_config ja muutan PermitRootLogin ´yes´ arvon ´no´ arvoksi.

![image](https://user-images.githubusercontent.com/78149945/133278927-f1b447ac-a688-434a-ae07-e0ede9f57f49.png)


### c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.

### d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.
