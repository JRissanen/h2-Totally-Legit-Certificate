# h2-Totally-Legit-Certificate
This is a repository for Penetration testing course 2023 Tunkeutumistestaus ict4tn027-3009 course exercise h2

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### [PortSwigger: SQL injection](https://portswigger.net/web-security/sql-injection)

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


### [PortSwigger: Cross-site scripting](https://portswigger.net/web-security/cross-site-scripting)

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

### HTTP Basics

Ratkaisin nämä tehtävät ZAPin avulla. </br>
Ensimmäinen kohta oli vain selitys, kuinka HTTP toimii ja mikä on tehtävän tarkoitus. </br>
Toisessa kohdassa piti vain kirjoittaa nimi ja palvelin palautti nimen takaisin väärinpäin. </br>
Kolmas tehtävä oli määrittää kumpaa HTTP-metodia (POST vai GET) WebGoat käytti tässä harjoituksessa. GETiä käytetään, kun pyydetään tietoa tarkasti määritellystä kohteesta. POSTia käytetään kun lähetetään tietoa palvelimelle, joten oikea vastaus on POST. </br>
Magic numberin sai selville ZAPin avulla kun katsoi mitä verkkosivulla tapahtuu kun sen päivittää. Magic Number vaihtui joka kerta päivityksen yhteydessä.

![Screenshot 2023-04-15 153303](https://user-images.githubusercontent.com/116954333/232224130-04936330-af79-49e2-89c5-32d615c2689d.png)

### Developer Tools

Osion Developer Tools-kohdat 1-3 ja 5 kertoivat, miten selaimen Developer Tool-työkalu yksinkertaistettuna toimii. </br>
Kohdan 4 sain ratkaistua ohjeita seuraamalla. Avasin Developer Toolin F12 näppäimellä ja menin "Console" välilehdelle. </br>
Tyhjensin konsolin näppäinyhdistelmällä: `Ctrl + Shift + L` ja kirjoitin tyhkään kenttään "allow pasting", niin pystyin copy pasteamaan tekstiä konsoliin. </br>
Sitten vain seurasin ohjeita ja kopioin tehtävän funktion ja syötin sen konsoliin. Kopion funktion antaman numeron tekstikenttään ja harjoitus meni läpi.

![Screenshot 2023-04-15 154959](https://user-images.githubusercontent.com/116954333/232226129-1603ba92-2398-45dc-b71f-f99d7bf3a5f6.png)

Kohdan 6 sain ratkaistua ohjeita seuraamalla. Avasin Developer Toolin F12 näppäimellä ja menin "Network" välilehdelle. </br>
Tyhjensin näkymän vasemmassa yläreunassa olevasta roskakori-kuvakkeesta ja painoin "Go!" näppäintä. </br>
Tyhjennetystä näkymästä oli helppo havaita oikea HTTP-pyyntö. Se oli lisäksi ainoa POST-metodin pyyntö sekä tiedostotyypiltään "network". </br>
Sitä klikkaamalla näkymä aukesi developer Toolin oikeaan reunaan ja menemällä "Request" välilehdelle, löysin etsimäni numeron ja syötin sen harjoituksen tekstikenttään.

![Screenshot 2023-04-15 160429](https://user-images.githubusercontent.com/116954333/232226479-821696f8-a61a-45c4-a8f1-cc48a67e6fb8.png)

## f) SELECT * FROM student. Ratkaise [SQLZoo:sta:](https://sqlzoo.net/wiki/SQL_Tutorial) 0 SELECT basics, 2 SELECT from World kohdat 1-5.

Näiden osioiden harjoitukset olivat niin suoraviivaisia, että en koe tarpeelliseksi avata ratkaisuja sen enempää. Laitan vain kuvat omista oikeista vastauksistani. </br>
Kun luki tehtävän ohjeistuksen ja sitten sovelsi logiikkaa harjoitukseen, niin kaikki onnistui ongelmitta.

### 0 SELECT basics
![Screenshot 2023-04-15 165249](https://user-images.githubusercontent.com/116954333/232228817-8e9f336d-7dfe-431a-9597-f7d39d538f8a.png)
![Screenshot 2023-04-15 165333](https://user-images.githubusercontent.com/116954333/232228825-56247b29-4b2b-4b89-904c-8e45267bc3a8.png)
![Screenshot 2023-04-15 165359](https://user-images.githubusercontent.com/116954333/232228829-56b8c220-3cb8-4431-9dfb-bb535659651d.png)

### 2 SELECT from World kohdat 1-5
![Screenshot 2023-04-15 164921](https://user-images.githubusercontent.com/116954333/232228856-442272b5-8d18-4b0d-b2de-a9b416695738.png)
![Screenshot 2023-04-15 165015](https://user-images.githubusercontent.com/116954333/232228862-935be843-e972-430d-b966-619556612237.png)
![Screenshot 2023-04-15 165054](https://user-images.githubusercontent.com/116954333/232228864-8c0624a3-aed0-4927-af0b-2c8d49574bf2.png)
![Screenshot 2023-04-15 165119](https://user-images.githubusercontent.com/116954333/232228866-a3bfacf8-4022-45eb-9570-5afd0c939b94.png)
![Screenshot 2023-04-15 165143](https://user-images.githubusercontent.com/116954333/232228872-cf6915ae-18e7-41ef-a42f-c348bc41d47f.png)


## g) Ratkaise WebGoatista*

### A1 Injection (intro)

Kohdat 1 ja 6-8 kertoivat, miten SQL-injectioita käytetään. </br>
Kohdassa 2 haluttiin "Bob Franco" nimisen työntekijän osasto selville. </br>
SQLZoo:sta opittujen harjoitusten kautta sovelsin oppimaani tähänkin kohtaan ja ratkaisu oli suoraviivainen. </br>
Valitaan komennolla `select` halutun tiedon kategoria `department` taulukosta `employees`</br>
Annetaan ehdoksi `where` jokin Bob Francon tiedoista `first_name = 'Bob'`.
![Screenshot 2023-04-15 172134](https://user-images.githubusercontent.com/116954333/232230239-e2728140-fc67-442e-bd3a-ce872e649e12.png)

Kolmannessa kohdassa piti tarkistaa sivun vinkeistä, miten SQL-injektio piti muodostaa ja tajusin, että piti käyttää `set` komentoa, jonka jälkeen aiemmin opittua logiikkaa soveltamalla tehtävä ratkesi.
![Screenshot 2023-04-15 173233](https://user-images.githubusercontent.com/116954333/232230749-fba615eb-89c0-4e86-bb44-b19be06a2c43.png)

Neljännessä kohdassa piti käyttää komentoja `alter` ja `add`.
![Screenshot 2023-04-15 174124](https://user-images.githubusercontent.com/116954333/232231143-a8a80cec-8aab-4866-9d9d-7f28976bcac6.png)

Viidennessä kohdassa piti antaa oikeudet taulukkojen muokkaamiseen komennolla: `grant`.
![Screenshot 2023-04-15 174747](https://user-images.githubusercontent.com/116954333/232231895-f61b952c-0511-40dc-b724-31b6b1b36dc5.png)

Yhdeksännessä kohdassa piti vain valita oikeat vaihtoehdot, jotta saa yhden käyttäjän sijasta kaikkien tiedot.
![Screenshot 2023-04-15 175237](https://user-images.githubusercontent.com/116954333/232232195-797e9bc1-7102-4dcb-a5df-e0e3db669696.png)

10 tehtävässä piti käyttää numeerisia SQL-injektioita. Otin mallia ysi kohdan tehtävästä sekä kutos kohdan lopussa olevista esimerkeistä ja informaatiosta. Antamalla `or 1=1` palvelin lukee tiedon `TRUE` arvona ja palauttaa kaikkien käyttäjien tiedot.

![Screenshot 2023-04-15 182940](https://user-images.githubusercontent.com/116954333/232234307-4a902bce-ef67-4565-b8b6-577e247e9151.png)

![Screenshot 2023-04-15 180112](https://user-images.githubusercontent.com/116954333/232232776-2873987e-0a58-4822-9fde-7fe3e67a8a74.png)

11 tehtävässä piti soveltaa samaa logiikkaa kuin 10 tehtävässäkin.
![Screenshot 2023-04-15 180703](https://user-images.githubusercontent.com/116954333/232235529-92fdc149-768d-4cc2-834d-52293df136de.png)


12 tehtävässä piti soveltaa aiemmmin opittua logiikkaa. Vinkki neuvoi aloittamaan SQL-injeltion käyttämällä `'; update` alkua, jonka jälkeen `set` komennolla sai annettua isomman arvon palkalle. Sitten hyödynsin 10. tehtävää ja otin `auth_tan='3SL99A'` koko SQL:n kohteeksi ja lopuksi annoin `--`, joka määritti loppu osan kommenteiksi, eli sitä ei palvelin edes lue ja tehtävä meni läpi. </br>
Lopullinen SQL: `'; update employees set salary='99999' where auth_tan='3SL99A' --`.
![Screenshot 2023-04-15 185523](https://user-images.githubusercontent.com/116954333/232235487-f786ea19-2098-4f54-aead-bbf330a13565.png)

13 tehtävä ratkesi samalla logiikalla kuin 12 tehtävä. Ensin `';`, joka ohittaa nimikyselyn ja sen jälkeen kohdassa neljä opetettu `drop`, joka poistaa tiedot. Lopullinen SQL: `'; drop table access_log --`
![Screenshot 2023-04-15 190607](https://user-images.githubusercontent.com/116954333/232236391-e77c9de5-dba4-488a-8842-a632fc02749e.png)

### A2 Broken authentication: Authentication bypasses: 2 2FA Password Reset

Tehtävän annosssa mainittiin proxyn käyttäminen, joten tutkin liikennettä ZAPin kautta. </br>
Aluksi laitoin ZAPista liikenteen katkaisun päälle vihreää palloa painamalla ja sen jälkeen syötin A2 harjoituksen molempiin tekstikenttiin pelkän yksittäisen merkin `'`. Sen jälkeen painamalla "Next Break Point" painiketta pääsin "Break" välilehdellä aina seuraavaan kohtaan, kunnes näkyviin tuli antamani syötteiden tulostus.

![Screenshot 2023-04-15 215018](https://user-images.githubusercontent.com/116954333/232249474-2b03568f-f52b-49a6-abd3-e72a84adb801.png)

![Screenshot 2023-04-15 215209](https://user-images.githubusercontent.com/116954333/232249612-9c2ad3d7-9db7-4ca3-a4fc-1173166e0059.png)

Katsoin tehtävän vinkeistä apua ja siellä neuvottiin suraavaa:
![Screenshot 2023-04-15 215500](https://user-images.githubusercontent.com/116954333/232249655-5a9e6ff5-699c-4086-86c6-a2ed6f320893.png)

Vinkkien mukaan ei tullut poistaa koko "secQuestion0" kohtaa, vaan vain sen parametria tarvitsisi muuttaa. </br>
Muutinkin sitten ZAPista "Break" välilehdellä näkyvää syötettä siten, että vaihdoin "secQuestion0" & "secQuestion1" -> "secQuestion5" & "secQuestion6", sekä antamani syötteen `'` vaihdoin tekstiin `pass`.
![Screenshot 2023-04-15 215310](https://user-images.githubusercontent.com/116954333/232249839-070e7367-d653-4f13-be50-fee4ef67b26d.png)

Tehtävä meni onnistuneesti läpi.
![Screenshot 2023-04-15 220000](https://user-images.githubusercontent.com/116954333/232249861-b81ab7d0-31ac-4ffe-baa9-f842577b501c.png)
![Screenshot 2023-04-15 215930](https://user-images.githubusercontent.com/116954333/232249867-8b6fbac6-3469-418e-bfce-6bff64418fe0.png)

### A3 Sensitive data exposure: Insecure Login: 2 Let's try

Aloitin taas laittamalla ZAPista liikenteen katkaisun päälle ja painamalla harjoituksen ohjeistamana "Log in" painiketta. </br>
"Break" välilehdellä ollessani taas klikkailin "Next Break Point" painiketta kunnes näkyviin tuli jotain mielenkiintoista. </br>
Käyttäjänimi oli "CaptainJack" ja salasana "BlackPearl". Kirjoitin nämä harjoituksen tekstikenttiin ja tehtävä onnistui.
![Screenshot 2023-04-15 224344](https://user-images.githubusercontent.com/116954333/232250525-70bc3c58-84e3-496d-80f8-d5c9678a7262.png)
![Screenshot 2023-04-15 224238](https://user-images.githubusercontent.com/116954333/232250531-e2283333-6ccd-4012-99d6-d0e0cb3803e0.png)
![Screenshot 2023-04-15 224144](https://user-images.githubusercontent.com/116954333/232250543-3edaa8ad-ec2b-4f0e-b73d-bb4ad917e379.png)


### A7 Cross Site Scripting (XSS): Cross site scripting

#### 2 What is XSS?

Tehtävässä piti testata javascript alertia. </br>
En onnistunut tekemään ohjeiden mukaan syöttämällä alertin `javascript:alert(document.cookie);` haku kenttään, joten käytin Developer Toolin konsolia. Cookiet olivat samat molemmilla sivuilla.</br>
![Screenshot 2023-04-16 112001](https://user-images.githubusercontent.com/116954333/232286472-d3d8352f-0b4e-40b3-8fa5-d2c2dc9fecdd.png)
![Screenshot 2023-04-16 112418](https://user-images.githubusercontent.com/116954333/232286481-c8544a16-085a-4ea7-95be-fca3822e7acc.png)


#### 7 Try It! Reflected XSS

Tehtävässä piti selvittää XSS:lle altis tekstikenttä ja syöttää siihen scripti. </br>
Käytin hyödyksi kohdassa kaksi neuvottua scriptin pätkää ja kirjoitin kohdan "Enter your credit card number:" tekstikenttään: `<script>alert("Alert Test")</script>`. </br>
![Screenshot 2023-04-16 113309](https://user-images.githubusercontent.com/116954333/232286965-10812b24-04e6-49e5-ab2e-adabdcb18034.png)
![Screenshot 2023-04-16 113112](https://user-images.githubusercontent.com/116954333/232286973-37f829f3-d4ae-4fc9-ad29-52956ad82ea3.png)


### A8:2013 Request Forgeries: Cross-Site Request Forgeries

#### 3 "Basic Get CSRF Exercise"








## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
https://www.zaproxy.org/download/ </br>
https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/?fromSearch=owasp </br>
https://github.com/miljonka/Tunkeutumistestaus/wiki/h2_Totally-Legit-Sertificate </br>
https://github.com/WebGoat/WebGoat/issues/1216 </br>
https://sqlzoo.net/wiki/SQL_Tutorial </br>













