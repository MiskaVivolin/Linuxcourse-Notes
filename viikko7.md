
# Linux laboratorioharjoitusraportti


### Linuxin asennus

Aloitan asennuksen painamalla Oracle virtualbox managerissa `new` kuvaketta. Asetan "name" sarakkeeseen nimen `Miska4000`, "Type" sarakkeeseen `Linux` ja Version sarakkeeseen `Debian 64-bit`.

![image](https://user-images.githubusercontent.com/78149945/136256320-0ad6a7d3-f171-4212-a7ec-260eb7b66f92.png)

Muistiksi asetan 4096MB.

![image](https://user-images.githubusercontent.com/78149945/136256509-911a2ce0-fe34-4ffe-b74c-e1a361c7f4e7.png)

Hard disk:iksi valitsen `Create a virtual hard disk now` sillä en halua että omasta kovalevystäni poistuisi kaikki tiedot. Seuraavalla sivulla valitsen `VDI (Virtual disk image)` vaihtoehdon. Sen jälkeen valitsen `Dynamically allocated`, jolloin muisti täyttyy vain jos sen pitää. Lopuksi asetan Hard disk muistiksi 40GB ja painan "create".

![image](https://user-images.githubusercontent.com/78149945/136257115-1bf3fd57-68c1-459d-839f-acb87814cc77.png)

Käynnistän uuden virtuaalikoneen ja valitsen `debian-live-11.0.0-amd64-xfce+nonfree.iso`. Seuraavaksi valitsen main menu:sta ensimmäisen vaihtoehdon ja odottelen muutaman minuutin.

![image](https://user-images.githubusercontent.com/78149945/136257503-e4750d8c-6b7c-499e-9720-9ebf3dd6068d.png)

![image](https://user-images.githubusercontent.com/78149945/136258912-d62a11d4-0808-47ff-8bcd-c783dc730bb1.png)

Virtuaalikoneen käynnistyttyä valitsen "Install Debian" kuvakkeen aloittaakseni Debianin asennuksen. Valitsen ensimmäiseksi kielekseni American English. Sijainniksi valitsen Helsingin. Näppäimeksi valitsen Suomalaisen default näppäimistön. Partitions kohdassa valitsen "Erase disk" vaihtoehdon ja tarkistan vielä ylhäältä että Linux asennetaan Virtuaali levylle. Users kohdassa asetan nimeni ja luon hyvän salasanan jolla kirjautua virtualboxiin.

![image](https://user-images.githubusercontent.com/78149945/136259797-252bc824-3681-45b2-8b9d-40d290bb4ec9.png)


Lopuksi tarkistan että tiedot ovat oikein ja painan `Install`. Odottelen hetken kun Debian asentuu.

![image](https://user-images.githubusercontent.com/78149945/136264783-637da2f3-40aa-4465-b8eb-2adf781fb1f1.png)

Debianin asennuttua restarttaan sen. 


### Palomuurin asennus

Asennan ensin ufw:n komennolla `sudo apt-get install ufw`. Sen jälkeen suoritan komennon `sudo ufw allow 22/tcp`. Lopuksi suoritan komennon `sudo ufw enable` ja käynnistän virtuaalikoneen uudelleen jolloin palomuuri aktivoituu. 

![image](https://user-images.githubusercontent.com/78149945/136269759-905bab62-92f9-4eb5-91ee-ee3a4d76e62e.png)

### Etähallintaa

Asennan salt-minionin komennolla `sudo apt-get -y install salt-minion`. Sen jälkeen suoritan komennon `echo -e "master: 172.28.171.13\nid: $(whoami)"|sudo tee -a /etc/salt/minion`. Restarttaan vielä salt minionin komennolla `sudo service salt-minion restart`.

### Työntekijät

Suoritan ensin komennot `sudo apt-get update` ja `sudo apt-get upgrade`. Sen jälkeen asennan apachen komennolla `sudo apt-get install apache2` ja laitan sen käyntiin `sudo systemctl start apache2` komennolla. Lisään uuden käyttäjän sudo adduser jormamahkyla ja asetan hyvän salasanan. Menen käyttäjän jormamahkyla kotihakemistoon ja teen uuden hakemiston `public_html`, minne luon tekstitiedoston `public.html`, jonne kirjoitan `jormamahkyla.` Suoritan vielä komennon `sudo a2enmod userdir` ja restarttaan apachen komennolla `sudo systemctl restart apache2`. Menen osoitteeseen http://localhost/~jormamahkyla/ ja saan käyttäjän kotisivut näkyviin.

![image](https://user-images.githubusercontent.com/78149945/136344548-c58592f2-2034-415f-b9b5-47634d1a4190.png)

Luon uuden käyttäjän pekkahurme ja menen hänen kotihakemistoon tekemään uuden `public_html` hakemiston jonne teen public.html tekstitiedoston. Menen osoitteeseen http://localhost/~pekkahurme/ ja saan käyttäjän kotisivut näkyviin.

![image](https://user-images.githubusercontent.com/78149945/136345606-147d3abb-20c7-424b-94c9-4da1cde4f987.png)

Luon uuden käyttäjän ronaldosmith ja menen hänen kotihakemistoon tekemään uuden `public_html` hakemiston jonne teen public.html tekstitiedoston. Menen osoitteeseen http://localhost/~ronaldosmith/ ja saan käyttäjän kotisivut näkyviin.

![image](https://user-images.githubusercontent.com/78149945/136345939-71739a62-98d5-405e-8084-3cda6278d4b1.png)

### Koodaajan koti

Teen uuden tiedoston `Helloworld.py` jonne kirjoitan koodin `print(Hello world!)`. suoritan koodin komennolla `python3 helloworld.py` ja saan konsoliin tekstin `Hello world!`

![image](https://user-images.githubusercontent.com/78149945/136347918-2c5eca1a-bcdb-4f79-b127-97e99f899617.png)

Teen uuden tiedoston `Helloworld.js` jonne kirjoitan koodin `console.log(Hello world!)`. Asennan noden komennolla `sudo apt install nodejs` ja suoritan koodin komennolla `node helloworld.js`, jolloin saan konsoliin tekstin `Hello world!`.

![image](https://user-images.githubusercontent.com/78149945/136348157-eefa0338-727e-4a40-a5ed-35fde57ab6ce.png)







https://terokarvinen.com/2018/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-8-maanantai-alkukevat-2018-5-op/?fromSearch=laboratorio
