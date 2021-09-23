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

Tallennettuani rivit Namecheap sanoi että muutoksessa voi kulua hetki ennen kuin se astuu voimaan. Odotettuani tunnin miskavivolin.xyz näyttää onnistuneesti oman kotisivuni.

![image](https://user-images.githubusercontent.com/78149945/134474848-84246969-f7a8-4c9c-99bd-f8b517296b51.png)


### c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.

Käytän Terokarvinen.com - Hello Flask - Write a Python Web App ohjeita. Aloitan asentamalla Flaskin terminaalissa `sudo apt-get -y install python3-flask` komennolla. Teen uuden python tiedoston komennolla `nano hello.py`.

![image](https://user-images.githubusercontent.com/78149945/134471404-a07a1946-a287-4db9-bb38-62ba1affe88b.png)

Ajan ohjelman komennolla `python3 hello.py` ja ohjelma suoriutuu onnistuneesti. Komentoriville tulostuu osoite jossa näkyy ohjelman tuloste. Siirtymällä osoitteeseen näkyy teksti `Hello world` onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/134472028-d53f48df-76af-479a-9643-72ce5391b707.png)

![image](https://user-images.githubusercontent.com/78149945/134472109-ccd47dd1-c1e4-49ef-90b3-6e56ee3c6182.png)

### d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')

Aloitan tehtävän uuden käyttäjän luomisella komennolla `sudo adduser miskawsgi` ja asetan uuden hyvän salasanan. En laita user information osiossa mitään tietoja ja vahvistan käyttäjän luomisen. Otan sisäänkirjautumisen pois käytöstä komennolla `sudo usermod --lock miskawsgi`. Lisään perus käyttäjäni miskawsgi ryhmään komennolla `sudo adduser $(whoami) miskawsgi`. Teen uuden conf tiedoston `miskawsgi.conf` osoitteeseen `/etc/apache2/sites-available/` jossa käytän mallina terokarvinen.com wsgi pohjaa ja muutan terowsgi:t miskawsgi:ksi.

![image](https://user-images.githubusercontent.com/78149945/134480299-09d78d4e-94d7-4e95-a110-a3f3b095feb1.png)

Tallennettuani tiedoston aktivoin sen komennolla `sudo a2ensite miskawsgi` ja poistan aiemmat conf tiedostot käytöstä komennolla `sudo a2dissite miskav.com` ja `sudo a2dissite 000-default.conf`. Asennan wsgi moduulin komennolla `sudo apt-get -y install libapache2-mod-wsgi-py3` ja restarttaan apachen. Lopuksi ajan vielä configtestin komennolla `apache2ctl configtest` ja saan varoituksia, mutta syntax näyttää olevan kunnossa.

![image](https://user-images.githubusercontent.com/78149945/134492628-0bac13e7-ec45-485b-85e9-843eefadc97c.png)

Testaan mitä komentoriville tulostuu `curl localhost` komennolla ja saan 403 errorin, ilmeisesti koska käyttäjälläni ei ole oikeuksia miskawsgi käyttäjään. Ajan myös komennon `tail -1 /var/log/apache2/error.log`

![image](https://user-images.githubusercontent.com/78149945/134493464-159fbec0-1635-4ca4-967c-23e2db5fdb0b.png)

Ajamalla `groups` komennon en löydä `miskawsgi` ryhmää, mutta näen miskav ryhmän. Kokeilen ajaa komennon `groups miskav` ja saan komentoriville näkyviin miskawsgi.

![image](https://user-images.githubusercontent.com/78149945/134494663-2094ee3c-142d-43e9-8ac0-5b41c10f49a9.png)

Seuraavaksi teen uuden hakemiston komennolla `sudo mkdir /home/miskawsgi/public_wsgi`. Muutan oikeuksia niin, että kotihakemistoon pääsee ilman sudoa `sudo chown miskawsgi:miskawsgi /home/miskawsgi/public_wsgi`. Muutan oikeuksia myös niin, että kaikki voivat muokata tiedostoja jotka kuuluvat miskawsgi ryhmään.

![image](https://user-images.githubusercontent.com/78149945/134495749-2c2d387e-fd42-4613-a582-c07874727985.png)

Ajan komennon curl localhost ja saan `error 404` tulokseksi. Teen uuden tekstihakemiston komennolla nano /home/miskawsgi/public_wsgi, mutta en kuitenkaan saa kirjoitusoikeuksia joten suoritan saman komennon sudolla. Kirjoitan sivulle Terokarvinen.com mallin mukaan ja tallennan tiedoston.

![image](https://user-images.githubusercontent.com/78149945/134497343-c51d3f01-96b4-405b-9b3d-cd23c0fbaeed.png)

Testaan ajaa localhostia komentorivillä ja saan error 500. Teen vielä uuden tiedoston komennolla sudo nano /home/miskawsgi/public_wsgi/hello.py

![image](https://user-images.githubusercontent.com/78149945/134498605-9ae2729e-0026-41e4-99b3-c21f9290bc6d.png)

Kokeilen komentorivillä ajaa localhostin ja saan tulokseksi `Hello world!` Kokeilen vielä web browserissa localhostia ja saan saman tulosteen.

![image](https://user-images.githubusercontent.com/78149945/134498827-a4173274-6686-4bce-911f-0068ee85a57c.png)

### yhteenveto

Tein tehtäviä noin 6-7 tuntia eikä niiden kanssa esiintynyt suurempia ongelmia. Ymmärrän paremmin miten name based virtual hosting ja julkisen palvelimen asentaminen toimii. Flask vaikuttaa myös mielenkiintoiselta.

### Lähteet

https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/

https://terokarvinen.com/2020/hello-flask-python-web-app/

https://terokarvinen.com/2020/deploy-python-flask-to-production/

https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars
