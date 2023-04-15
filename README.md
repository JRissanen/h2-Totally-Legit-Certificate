# h2-Totally-Legit-Certificate
This is a repository for Penetration testing course 2023 Tunkeutumistestaus ict4tn027-3009 course exercise h2

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### PortSwigger: SQL injection

__Mikä on SQL injektio (SQLi)?__
* SQL-injektio (SQLi) on verkkotietoturvahaavoittuvuus, jonka avulla hyökkääjän on mahdollista häiritä/keskeyttää sovelluksen omaan tietokantaansa tekemiä kyselyitä.

__Mikä on onnistuneen SQL-injektio hyökkäyksen vaikutus?__
* Hyökkääjän on mahdollista saada käsiinsä arkaluontoista tietoa esim:
  * Salasanoja
  * Luottokorttitietoja
  * Henkilökohtaisia tietoja

__Kuinka havaita SQL-injektio haavoittuvuudet?__
* Käyttämällä skanneria kuten Burp Suite's web vulnerability scanner.
* Manuaalisesti testaamalla esim:
  * Syöttämällä yhden lainausmerkin `'` ja tarkkailemalla virhekoodia, tai muuta epänormaalia.
  * Syöttämällä Boolean-ehtoja kuten `OR 1=1` ja tarkkailemalla eroja sovelluksen vastauksissa.
  * Syöttämällä payloadeja, jotka on suunniteltu aiheuttamaan viivettä SQL-kyselyissä, ja sen jälkeen tarkkailemalla vastausaikoja.
  
__SQL-injektio asteet__
* Ensimmäinen aste (First-order):
  * Sovellus ottaa käyttäjän syötteen HTTP-pyynnöstä ja pyynnön käsittelyn aikana sisällyttää syötteessä olleen haitallisen osan osaksi SQL-kyselyä.
* Toinen aste (Second-order), tallennettu SQL-injektio:
  * sovellus ottaa käyttäjän syötteen HTTP-pyynnöstä ja tallentaa sen tulevaa käyttöä varten.

__Kuinka estää SQL-injektio?__
* Useimmat SQL-injektiot voidaan estää käyttämällä parametrisoituja kyselyitä (valmiit lauseet) merkkijonojen yhdistämisen sijaan kyselyn sisällä.
  * Parametrisoituja kyselyjä voidaan käyttää tilanteissa, joissa epäluotettava syöte näkyy tietona kyselyn sisällä, mutta niitä ei voida käyttää käsittelemään epäluotettavaa syötettä kyselyn muissa osissa, kuten taulukoiden tai sarakkeiden nimissä tai `ORDER BY` -lauseessa. 
* Jotta SQL-injektio voidaan estää tehokkaasti, kyselyssä käytetyn merkkijonon on aina oltava kovakoodattu vakio, eikä se saa koskaan sisältää muuttuvia tietoja.


### PortSwigger: Cross-site scripting

__Mitä tarkoittaa cross-site scripting (XSS)?__
* Verkkotietoturvahaavoittuvuus, jonka avulla hyökkääjän on mahdollista kompromisoida/vaarantaa käyttäjien ja sovellusten välinen kommunikointi.

__Miten XSS toimii?__
* Manipuloimalla haavoittuvaa verkkosivustoa niin, että se palauttaa käyttäjille haitallista JavaScriptiä.

__Mihin XSS:ää voi käyttää?__
* Hyökkääjän on mahdollista esimerkiksi:
  * Esiintyä tai naamioitua uhrikäyttäjäksi ja suorittaa/ajaa kaikki toiminnot, jotka käyttäjä voi suorittaa.
  * Lisätä troijalaisia haittaohjelmia verkkosivulle.

__Kuinka havaita XSS haavoittuvuudet?__
* Käyttämällä skanneria kuten Burp Suite's web vulnerability scanner.
* Manuaalisesti:
  * Lähettämällä jonkin yksinkertaisen yksilöllisen syötteen (kuten lyhyen aakkosnumeerisen merkkijonon) jokaiseen sovelluksen sisääntulopisteeseen.
   * Jokaisen sijainnin tunnistamisen, johon lähetetty syöte palautetaan HTTP-vastauksissa.
    * jokaisen sijainnin testaamisen yksitellen määrittämään, voidaanko muotoiltua syötettä käyttää haitallisen JavaScriptin suorittamiseen.

__Kuinka estää XSS hyökkäykset?__
* Sisääntulevan syötteen suodattaminen heti kun se saapuu.
* Lähtevän syötteen salaaminen.
* Käyttämällä asianmukaisia response headereita.
* Sisällön suojauskäytäntö (Content Security Policy).

---
Olen tehnyt kaikki harjoitukset omalla tietokoneellani. </br>

Koneen infot: </br>
Edition: Windows 10 Pro </br>
Version: 22H2 </br>
OS build: 19045.2728 </br>
Processor: Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz   3.19 GHz </br>
Installed RAM: 16,0 GB </br>
System type: 64-bit operating system, x64-based processor </br>

Virtuaalikoneet ovat Oracle VM VirtualBoxissa, jonka versio on: Version 6.1.40. </br>

Virtuaalikoneiden infot: </br>

Metasploitable: </br>
Type: Linux </br>
Version: Debian (64-bit) </br>
Base Memory: 1024 MB </br>
Video Memory: 16 MB </br>
Processors: 1 CPU

Kali: </br>
Type: Linux </br>
Version: Debian (64-bit) </br>
Base Memory: 2024 MB </br>
Video Memory: 128 MB </br>
Processors: 2 CPU

Varmistan aina ennen tehtävien aloittamista, että molemmat virtuaalikoneet ovat yhteyksissä toisiinsa pingaamalla kali-koneelta metasploitable2-konetta: `ping 192.168.60.3`. </br>
Varmistan myös aina, ettei kumpikaan virtuaalikone saa verkkoyhteyttä pingaamalla google.com sekä googlen ensisijaista dns-serveriä 8.8.8.8: `ping google.com` ja `ping 8.8.8.8`. </br>
Virtuaalikoneet ovat verkossa vain silloin kun tehtävät vaativat sitä, eli kun pitää esimerkiksi ladata jokin ohjelma.

Jos haluat enemmän tietoa minun tunkeutumistestausympäristöstä, niin voit lukea artikkelini: </br>
https://github.com/JRissanen/h1-OmaLabra

---



## a) ZAP! Asenna ZAP välimiesproxy ja näytä, että pystyt sieppaamaan liikennettä selaimesta.

Aloitin avaamalla kali-koneeni ja menemällä selaimella https://www.zaproxy.org/download/ osoitteeseen lataamaan OWASP ZAP paketin. </br>

![Screenshot 2023-04-08 144837](https://user-images.githubusercontent.com/116954333/230719986-6028c7ff-9850-40f9-98aa-5ffe86a0fa17.png)

Seuraavaksi meninin työpöydälläni olevaan kotihakemistoon ja "Downloads" kohdassa oli juuri lataamani ZAP_2.12.0 zip-tiedosto. </br>
Hiiren oikeaa painiketta zip-tiedoston kohdalla ja sen jälkeen "Extract Here", niin sain zip-tiedoston purettua ja varsinaisen kansion näkyviin. </br>
Sen jälkeen avasin terminaalin ja siirryin "Downloads" hakemistoon ja edelleen "ZAP_2.12.0" hakemistoon: `cd /Downloads/ZAP_2.12.0`. </br>
ZAP-hakemstossa oli README-tiedosto, jossa sanottiin, että ZAPin saa auki "zap.sh" skriptin ajamalla. ".sh" päätteiset tiedostot ovat ajettavissa `bash` komennolla, joten ajoin tiedoston: `bash zap.sh` ja OWASP ZAP aukesi. </br>
Valitsin, että haluan session tallennettavaksi oletuspaikkaan (home/kali/.ZAP/sessions) aikaleima nimenä ja jätin lisäksi terminaalin auki, koska OWASP ZAP vaatii sen toimiakseen.

![Screenshot 2023-04-08 150757](https://user-images.githubusercontent.com/116954333/230722157-2659cb3b-c002-4a00-b249-1cbe48166fa8.png)

Sen jälkeen valitsin ZAPista: Manual Explore -> URL to explore (käytin tässä Multillidaen etusivua) -> Launch Browser. </br>
Verkkosivu aukesi, sain kaapattua liikennettä ja Multillidae tuli ZAPin "Sites" kohtaan näkyviin.

![Screenshot 2023-04-12 125833](https://user-images.githubusercontent.com/116954333/231428243-bcac9972-627a-4104-b589-712029b56b8e.png)

Päivittämällä verkkosivun ja tutkimalla sitten vastausta eli yläpalkin "Response" kohtaa, sain esimerkiksi sivuntekijöiden jättämän HTML-kommentin näkyviin.

![Screenshot 2023-04-12 144454](https://user-images.githubusercontent.com/116954333/231448736-ed524031-18df-4454-9944-a788944ccab2.png)

## b) Totally Legit Sertificate. Asenna ZAP:n generoima CA-sertifikaatti selaimeen ja osoita testillä, että pystyt sieppaamaan HTTPS-salakirjoitettua liikennettä.

Aloitin menemällä ZAP:ssa yläpalkkiin: Tools -> Options -> Network -> Server Certificates -> Generate -> OK -> Save </br>
Näin sain tehtyä ja tallennettua uuden CA-sertifikaatin.

![Screenshot 2023-04-12 145854](https://user-images.githubusercontent.com/116954333/231451559-5ae67957-27d5-48ef-a5bb-c79192043092.png)

Seuraavaksi avataan selain (käytin Mozilla FireFoxia) ja mennään asetusten kautta sertifikaatteihin ja lisätään OWASP ZAPin sertifikaatti muiden sertifikaattien joukkoon: </br>
FireFox -> kolme päällekkäistä viivaa -> Settings -> Privacy & Security -> Certificates -> Viev Certificates -> Import -> </br>
Valitse: Trust this CA to identify websites -> OK -> OK.

![Screenshot 2023-04-12 170429](https://user-images.githubusercontent.com/116954333/231484459-101f07bc-82e7-4631-84f9-a8dbd1632550.png)

Nyt kun katsoin sertifikaatteja uudestaan, OWASP Root CA:n alta löytyi onnistuneesti lisätty sertifikaatti.

![Screenshot 2023-04-12 170956](https://user-images.githubusercontent.com/116954333/231485009-f35e7ba0-e725-43e5-8b38-b62d6475f326.png)

ZAPin mukaan, jos avaa selaimen ZAPin kautta (niinkuin aiemmin tein kohdasta "Manual Explore -> Launch Browser"), niin proxy asetukset ovat silloin automaattisesti oikein. ZAP määrittää localhostin portin 8080 proxy serveriksi, jonka läpi kaikki liikenne kulkee. Tämän informaation sain menemällä selaimessa osoitteeseen `https://localhost:8080`.

![Screenshot 2023-04-13 202548](https://user-images.githubusercontent.com/116954333/232200842-32490c28-ba95-43a8-a339-586106e96cd3.png)

Lopuksi kirjoitin googleen vain sanan "haku" ja katsoin onnistuinko sieppaamaan liikennettä. Mitään ongelmia ei ainakaan ollut sertifikaattien kanssa ja kaikki siepatut tiedot tulivat ZAPiin näkyviin, joten kai se onnistui.

![Screenshot 2023-04-13 204622](https://user-images.githubusercontent.com/116954333/232200969-6929c81b-4fa2-48fb-8023-ca82d5d6a21a.png)

## c) Intercept. Pysäytä hakupyyntö, muokkaa sitä ja päästä se palvelimelle.

Tässä tehtävässä kirjauduin ensin DVWA:n (Damn Vulnerable Web Application, v1.0.7) sivuille, sen antamilla tunnuksilla (käyttäjä: admin, salasana: password). </br>
Aikomukseni oli kokeilla, pystynkö muuttamaan sivun "Security Level" tasoa tasolta "High" tasoon "Low", kaappaamalla liikenteen sivun päivittyessä ja muuttamalla tietoa.

![Screenshot 2023-04-15 113924](https://user-images.githubusercontent.com/116954333/232202533-c058c77d-f3b9-44f8-9cd5-23356bae9119.png)

Nyt kun DVWA on selaimessa auki, siirryin ZAPin näkymään ja painoin yläpalkissa olevaa pientä vihreää palloa, joka katkaisee kaikki verkkosivun pyynnöt ja vastaukset. Pallo myös muuttui väriltään punaiseksi.

![Screenshot 2023-04-15 115107](https://user-images.githubusercontent.com/116954333/232202619-60e7d54f-255c-478c-8d91-4a3065c8a43b.png)

Sitten siirryin takaisin DWVA:n verkkosivulle ja painoin "Refresh" nappia ja huomasin, että sivu jäi lataamaan, koska ZAP on tällä hetkellä pysäyttänyt kaiken liikenteen.

![Screenshot 2023-04-15 115318](https://user-images.githubusercontent.com/116954333/232202704-f115d824-c5d0-46f9-a089-e419e5edb296.png)

Seuraavaksi tutkin ZAP:ssa login.php näkymää "Break" välilehdeltä. </br>
Tässä näkymässä näkyvää tekstiä voi itse editoida ja huomasin kohdan "Cookie:" vieressä olevan "security=high" määrityksen.

![Screenshot 2023-04-15 120351](https://user-images.githubusercontent.com/116954333/232203236-22c1a48f-9ae8-4c99-af14-b12ea6c65f09.png)

Vaihdoin määrityksen lukemaan "security=low" ja painoin ZAPin yläpalkissa olevaa "play" nappia, joka lopetti verkkosivun liikenteen pysäyttämisen ja päästi sen taas eteenpäin.

![Screenshot 2023-04-15 121152](https://user-images.githubusercontent.com/116954333/232203887-e3a9ff2f-9bcf-413a-8afe-49391480c711.png)

Siirryin takaisin DVWA:n verkkosivulle ja sivu latautui normaalisti, mutta kohdassa "Security Level:" luki nyt "low", joten pyynnön kaappaus ja muuttaminen onnistui omalta osaltani.

![Screenshot 2023-04-15 121728](https://user-images.githubusercontent.com/116954333/232205435-21f8becb-8e87-473c-948e-37bfd498cbc3.png)

Muutos ei kuitenkaan ollut pysyvä, koska jos nyt päivitin sivun uudestaan, se muuttui takaisin tasolle "high", mutta tehtävän kannalta kokeilu oli silti onnistunut. </br>
DVWA:n sivuilta pystyy myös kohdasta "DVWA Security" muuttamaan sivun suojauksen itse joko high/medium/low, jolloin sivu myös tallentaa valitun tason.

## d) Vuohi. Asenna WebGoat ja kokeile, että pääset kirjautumaan sisään.

Seurasin tässä tehtävässä Tero Karvisen [Install Webgoat 8 - Learn Web Pentesting](https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/?fromSearch=owasp) artikkelia.

Aluksi tuli asentaa työkaluja/ohjelmia, jotta WebGoatin käyttö onnistuisi ja olisi turvallista: </br>
__openjdk-11-jre__ mahdollistaa Java-sovellusten pyörittämisen, esim. WebGoat. </br>
__ufw__ on palomuuri, jonka käyttö on suotavaa haavoittuvaisen WebGoatin kanssa. </br>
__wget__ mahdollistaa tiedostojen lataamisen suoraan verkkosivuilta. `wget https://<verkkosivu>/<tiedosto>`. </br>
__bash-completion__ täyttää komennot automaattisesti tabulaattoria-nappia painaessa.

Kaikki nämä työkalut latasin ohjeiden mukaan: </br>
```
$ sudo apt-get update
$ sudo apt-get -y install openjdk-11-jre ufw wget bash-completion
```

Laitoin äsken asennetun __ufw__ palomuurin päälle komennolla: `sudo ufw enable`. </br>
Se onkin ilmeisesti jo päällä ja menee päälle aina kun järjestelmä käynnistetään. 

![Screenshot 2023-04-15 140241](https://user-images.githubusercontent.com/116954333/232210125-7c01f9d9-b1f5-4d7f-8db5-a567edd793e2.png)

Seuraavaksi latasin WebGoatin Teron sivuilta: </br>
`$ wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar`.

![Screenshot 2023-04-15 140809](https://user-images.githubusercontent.com/116954333/232210339-f5446543-f1c3-4cb2-b438-05c116642bff.png)

Teron artikkelia lukiessani huomasin, että WebGoatin oletus portti on sama kuin ZAPilla, 8080, joten sain vinkin erään kurssilaiseni raportista: </br>
[Miika](https://github.com/miljonka/Tunkeutumistestaus/wiki/h2_Totally-Legit-Sertificate) oli huomannut saman porttiongelman ja löytänyt ratkaisun [WebGoatin GitHub-sivuilta](https://github.com/WebGoat/WebGoat/issues/1216).

Eli käytin itsekin komentoa: `WEBGOAT_PORT=8081 java -jar webgoat-server-8.0.0.M26.jar`, jotta portti ei olisi ZAPin käyttämä 8080, vaan siitä seuraava 8081. </br>
Terminaalissa kaikki näytti olevan kunnossa ja menemällä selaimella osoitteeseen `http://localhost:8081/WebGoat/login`, pääsin sisäänkirjautumis sivulle.

![Screenshot 2023-04-15 142053](https://user-images.githubusercontent.com/116954333/232212019-b7eedec2-8353-41bc-8a12-d206368e1397.png)

Loin itselleni käyttäjän ja pääsin kirjautumaan sisään.

![Screenshot 2023-04-15 143357](https://user-images.githubusercontent.com/116954333/232213883-904b2876-d8f8-4b56-934a-68a452649f9e.png)


## e) Vauvavuohi. Ratkaise WebGoatista tehtävät "HTTP Basics" ja "Developer tools".










## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
https://www.zaproxy.org/download/ </br>
https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/?fromSearch=owasp </br>
https://github.com/miljonka/Tunkeutumistestaus/wiki/h2_Totally-Legit-Sertificate </br>






