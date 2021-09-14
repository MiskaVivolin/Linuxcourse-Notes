# Linux viikko 4 tehtäväraportti

### a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.

Aloitin Tekemällä paypal accounttia, koska omistan vain debit cardin. Yhdistin Digital oceanin Githubiin ja sain suoraan 100 dollaria käytettäväksi 2 kuukauden ajaksi, sillä olen ottanut käyttöön Githubin student packin. Valitsin Create a droplet kohdan ja valitsin ensimmäiseksi 64 bittisen Debianin 10. Otin sen jälkeen Basic planin ja datacenter regioniksi Amsterdamin. authentication kohdassa valitsin passwordin ja asetin pitkän vahvan salasanan. Annoin hostnamen lopuksi.

### b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.

Katson neuvoja `terokarvinen.com - First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS` sivulta. Aloitan tulimuurin asentamisen kirjoittamalla terminaaliin `ssh root@178.62.212.176`, jonka jälkeen kirjoitan `yes`. Terminaali kysyy IP osoitteen salasanaa jonka kirjoitettuani pääsen palvelimelleni. 
![image](https://user-images.githubusercontent.com/78149945/133263667-c894095f-77f4-47a2-9f7a-8652fbb36858.png)
Tässä vaiheessa avaan uuden terminaalin ja suoritan komennot `sudo apt-get update` ja `sudo apt-get upgrade`. Komennolla `sudo apt-get 
install ufw` asensin ufw:n. syötän komennot `sudo ufw allow 22/tcp` ja `sudo ufw enable`, joilla tein reiän ja aktivoin tulimuurin.


### c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.

### d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.
