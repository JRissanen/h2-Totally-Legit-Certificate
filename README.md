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

==
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

Jos haluat enemmän tietoa minun tunkeutumistestausympäristöstä, niin voit lukea artikkelini: </br>
https://github.com/JRissanen/h1-OmaLabra
==


## a) ZAP! Asenna ZAP välimiesproxy ja näytä, että pystyt sieppaamaan liikennettä selaimesta.




















## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
