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

## d) Vuohi. Asenna WebGoat ja kokeile, että pääset kirjautumaan sisään.







## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
https://www.zaproxy.org/download/ </br>
https://www.youtube.com/playlist?list=PLH8n_ayg-60J9i3nsLybper-DR3zJw6Z5 </br>




