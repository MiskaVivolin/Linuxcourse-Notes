# Linux viikko 5 tehtäväraportti

### a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla. 

Katson mallina Terokarvinen.com Name Based Virtual Hosts on Apache -sivustoa. Päivitin paketit `sudo apt-get update` komennolla ja apachen olen jo asentanut. Suoritan `echo "Default"|sudo tee /var/www/html/index.html` komennon ja saan tekstin `Default` komentoriville. Teen komennolla `sudoedit /etc/apache2/sites-available/miskav.com.conf` uuden tekstitiedoston. Sinne laitan servername:ksi `miskav.com`, serveraliakseksi `www.miskav.com`, documentrootiksi `/home/miskav/publicsites/miskav.com` ja Directoryn sisällä `/home/miskav/publicsites/miskav.com` jonka jälkeen "Require all granted" teksti.

![image](https://user-images.githubusercontent.com/78149945/134183966-5370fb5f-4109-484c-b77a-404dbc273392.png)

Tallennuksen jälkeen enabloin sen komennolla `sudo a2ensite miskav.com.conf` ja restarttaan apachen komennolla `sudo systemctl restart apache2`.

Seuraavaksi luon uuden hakemiston komennolla `mkdir -p /home/miskav/publicsites/miskav.com/` ja teen uuden tekstitiedoston komennolla `sudoedit /home/miskav/publicsites/miskav.com/index.html`. Teen komennolla `echo pyora > /home/xubuntu/publicsites/index.html` testin että index.html tiedostoon menee tekstiä. 

![image](https://user-images.githubusercontent.com/78149945/134189538-191e2367-f6bf-4430-b58e-297b2e8b865f.png)

Testaan `curl -H 'Host: pyora.example.com' localhost` komennolla komentorivin kautta, mitä tekstiä index.html tulostaa ja saan tekstin `nuudeliwokki`. Testaan vielä komentoa curl localhost ja saan tekstin `Default`. Menen hosts polkuun komennolla `sudoedit /etc/hosts` ja lisään sinne uuden osoitteen jolla pääsen uudelle nettisivulle.

![image](https://user-images.githubusercontent.com/78149945/134190969-cd5ef4da-d768-4053-9cf4-ff3c94582bf4.png)

![image](https://user-images.githubusercontent.com/78149945/134191061-3d781fa4-1408-40c2-b82c-7f973ae4007e.png)

### b) Julkinen nimi. Laita julkiselle palvelimellesi julkinen domain-nimi. Käytä oikeaa nimeä (joko vuokrattua tai ilmaispalvelusta). Tee Apachelle Name Based Virtual Host tälle nimelle. Kokeile eri laitteelta (esim. kännykältä), että nimi oikeasti toimii.

Päätin ostaa namecheapistä uuden domainin omalla nimellä miskavivolin.xyz. Mietin aluksi ilmaisia domaineja, mutta luettuani mielipiteitä internetistä päädyin halpaan domainiin namecheapistä. Menin Digitaloceaniin ja lisäsin palvelimelleni uuden domain osoitteen `miskavivolin.xyz`. Digitalocean ehdotti mitä tehdä seuraavaksi ja tarjosi linkin ohjeille. Menin seuraavaksi Namecheapin sivuille muokkaamaan domain tietoja. Lisäsin nameservers riveille digitaloceanin neuvomat rivit.

![image](https://user-images.githubusercontent.com/78149945/134464833-2f57c3fc-ba61-4efe-a365-1225a2cc95fe.png)

