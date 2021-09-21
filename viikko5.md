# Linux viikko 5 tehtäväraportti

### a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla. 

Päivitin paketit `sudo apt-get update` komennolla ja apachen olen jo asentanut. Suoritan `echo "Default"|sudo tee /var/www/html/index.html` komennon ja saan tekstin `Default` komentoriville. Teen komennolla `sudoedit /etc/apache2/sites-available/miskav.com.conf` uuden tekstitiedoston. Sinne laitan servername:ksi `miskav.com`, serveraliakseksi `www.miskav.com`, documentrootiksi `/home/miskav/publicsites/miskav.com` ja Directoryn sisällä `/home/miskav/publicsites/miskav.com` jonka jälkeen "Require all granted" teksti.

![image](https://user-images.githubusercontent.com/78149945/134183966-5370fb5f-4109-484c-b77a-404dbc273392.png)

Tallennuksen jälkeen enabloin sen komennolla `sudo a2ensite miskav.com.conf` ja restarttaan apachen komennolla `sudo systemctl restart apache2`.

Seuraavaksi luon uuden hakemiston komennolla `mkdir -p /home/miskav/publicsites/miskav.com/` ja teen uuden tekstitiedoston komennolla `sudoedit /home/miskav/publicsites/miskav.com/index.html`. Teen komennolla `echo pyora > /home/xubuntu/publicsites/index.html` testin että index.html tiedostoon menee tekstiä.
