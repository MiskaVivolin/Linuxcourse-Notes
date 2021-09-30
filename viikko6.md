# Linux viikko 6 tehtäväraportti

### a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.

Luon `home` hakemistoon uuden hakemiston komennolla `mkdir skriptit` johon teen tekstitiedoston komennolla `nano 1_to_10_script` joka laskee kymmeneen. Kirjoitan tekstitiedostoon while loopin joka printtaa aina kyseisen numeron ja menee yhdellä ylöspäin kunnes saa arvokseen yli 10 jolloin ohjelma loppuu. 

![image](https://user-images.githubusercontent.com/78149945/135107758-f16af1e2-2d48-429c-b49e-973c6c86a697.png)

Kutsun skriptiä komennolla `bash 1_to_10_script` ja saan komentoriville luvut onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135107821-956ad62a-16ff-409f-ac3c-0090c1365b2f.png)

Kopioin vielä skriptin bin hakemistoon komennolla `sudo cp -v 1_to_10_script /usr/local/bin` jolloin skriptiä voi kutsua mistä vain hakemistosta millä vain käyttäjällä. Testaan vielä kutsua skriptiä root -hakemistosta ja skripti suoriutuu onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135108292-af5f955f-2423-40b8-9724-57fccdc21dc9.png)


### b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".

Luon `skriptit` hakemistoon uuden tekstitiedoston komennolla `nano greet_script` joka moikkaa henkilöä. Kirjoitan lyhyen echo komennon ja tallennan sen

![image](https://user-images.githubusercontent.com/78149945/135109554-c882ae49-86f1-4c27-a8d1-0ea8a52859b7.png)

Kokeilen ajaa skriptin komennolla `bash greet_script Miska`, jolloin komentoriville tulostuu "Moi miska".

![image](https://user-images.githubusercontent.com/78149945/135109796-8c03909f-950c-409a-ad6b-e4fb6715b284.png)

Kopioin tämänkin skriptin bin hakemistoon komennolla `sudo cp -v greet_script /usr/local/bin` jolloin skriptiä voi kutsua mistä vain hakemistosta millä vain käyttäjällä. Testaan vielä kutsua skriptiä root -hakemistosta ja skripti suoriutuu onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135110163-ba35f968-972b-4d81-8836-778b3f7b4eff.png)

### c) Monta polkua. Tee Flask-ohjelma, jossa on useampi polku. Esim "localhost:5000/foo" näyttää sivun, jolla lukee "Foo" ja "localhost:5000/bar" näyttää sivun, jolla lukee "Bar". Voit käyttää testipalvelinta.

Teen ensin uuden tekstitiedoston komennolla `nano flask_paths.py`, jonne kirjoitan kolme eri endpointtia. `("/")` endpoint on testi joka palauttaa test. `("/greet")` endpoint palauttaa tervehdyksen ja `("/compliment")` palauttaa piristävän kehun. Lisään appiin myös rivin `app.run(debug=True)`, joka mahdollistaa localhostissa testaamisen. 

![image](https://user-images.githubusercontent.com/78149945/135124851-9d0ed531-8b71-4124-a3c8-9c615ddcea7f.png)

Ajan ohjelman komennolla `python3 flask_paths.py` ja tarkistan että jokainen toimii localhostissa.

![image](https://user-images.githubusercontent.com/78149945/135125115-aadff094-e2e8-472f-ad2b-56e39d5e7aa2.png)

![image](https://user-images.githubusercontent.com/78149945/135125162-b61c9bf1-e972-4c43-a62f-0046cb41d28b.png)

![image](https://user-images.githubusercontent.com/78149945/135125205-b5f1fccf-7b24-472b-813c-007d90b8988f.png)


### d) Muotti. Tulosta Flaskilla sivu muotista. Voit käyttää testipalvelinta.

Teen ensin uuden hakemiston komennolla `mkdir templates`. Menen hakemiston sisälle ja teen nanolla uuden html tiedoston `greet.html`. Kopioin sinne yksinkertaisen html pohjan jossa on post methodi mikä postaa käyttäjän kirjoittaman syötteen.

![image](https://user-images.githubusercontent.com/78149945/135128517-28137825-a37b-4df0-95a0-3ed1dd3223cb.png)

Menen hakemiston taaksepäin ja teen uuden python tiedoston komennolla `nano greet.py`. importtaan flaskin, render templaten ja requestin. Asetan `("/")` endpointtiin get ja post metodit ja teen uuden funktion joka hakee greet.html tiedoston jos siinä on request form "side". Lisään appiin myös rivin `app.run(debug=True)`, joka mahdollistaa localhostissa testaamisen. 

![image](https://user-images.githubusercontent.com/78149945/135130337-09e267aa-2bf5-493e-a972-fc11309c9c65.png)

Ajan komennon `python3 greet.py` ja testaan vielä että ohjelma toimii localhostissa.

![image](https://user-images.githubusercontent.com/78149945/135130838-554f0fc0-ca2d-4518-b036-780aaa5cc8b9.png)

Painaessani enteriä sivu lähettää post pyynnön.

![image](https://user-images.githubusercontent.com/78149945/135131174-deb3818a-bbcf-4bca-be70-d1282828eded.png)




