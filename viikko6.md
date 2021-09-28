# Linux viikko 6 tehtäväraportti

### a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.

Luon `home` hakemistoon uuden hakemiston komennolla `mkdir skriptit` johon teen tekstitiedoston komennolla `nano 1_to_10_script` joka laskee kymmeneen. Kirjoitan tekstitiedostoon while loopin joka printtaa aina kyseisen numeron ja menee yhdellä ylöspäin kunnes saa arvokseen yli 10 jolloin ohjelma loppuu. 

![image](https://user-images.githubusercontent.com/78149945/135107758-f16af1e2-2d48-429c-b49e-973c6c86a697.png)

Kutsun skriptiä komennolla `bash 1_to_10_script` ja saan komentoriville päivämäärän ja ajan onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135107821-956ad62a-16ff-409f-ac3c-0090c1365b2f.png)

Kopioin vielä skriptin bin hakemistoon komennolla `sudo cp -v 1_to_10_script /usr/local/bin` jolloin skriptiä voi kutsua mistä vain hakemistosta millä vain käyttäjällä. Testaan vielä kutsua skriptiä root -hakemistosta ja skripti suoriutuu onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135108292-af5f955f-2423-40b8-9724-57fccdc21dc9.png)


### b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".

Luon `skriptit` hakemistoon uuden tekstitiedoston komennolla `nano greet_script` joka moikkaa henkilöä. Kirjoitan lyhyen echo komennon ja tallennan sen

![image](https://user-images.githubusercontent.com/78149945/135109554-c882ae49-86f1-4c27-a8d1-0ea8a52859b7.png)

Kokeilen ajaa skriptin komennolla bash greet_script Miska, jolloin komentoriville tulostuu "Moi miska".

![image](https://user-images.githubusercontent.com/78149945/135109796-8c03909f-950c-409a-ad6b-e4fb6715b284.png)

Kopioin tämänkin skriptin bin hakemistoon komennolla `sudo cp -v greet_script /usr/local/bin` jolloin skriptiä voi kutsua mistä vain hakemistosta millä vain käyttäjällä. Testaan vielä kutsua skriptiä root -hakemistosta ja skripti suoriutuu onnistuneesti.

![image](https://user-images.githubusercontent.com/78149945/135110163-ba35f968-972b-4d81-8836-778b3f7b4eff.png)
