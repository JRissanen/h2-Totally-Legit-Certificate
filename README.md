# h2-Totally-Legit-Certificate
This is a repository for Penetration testing course 2023 Tunkeutumistestaus ict4tn027-3009 course exercise h2

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### PortSwigger: SQL injection

__Mikä on SQL injektio (SQLi)?__
* SQL-injektio (SQLi) on verkkotietoturvahaavoittuvuus, jonka avulla hyökkääjän on mahdollista häiritä/keskeyttää sovelluksen omaan tietokantaansa tekemiä kyselyitä.
* Mahdollistaa hyökkääjän pääsyn näkemään tietoja, joihin tällä ei normaalisti olisi oikeutta.
  * Muiden käyttäjien tiedot.
  * Mikä tahansa muu tieto, johon vain järjestelmällä on oikeus.
* Monissa tapauksissa hyökkääjät voivat poistaa tai muuttaa tietoja aiheuttaen peruuttamatonta, tai pitkäkestoista, vahinkoa.
* Voi myös toimia DoS-hyökkäyksenä (Denial of Service).

__Mikä on onnistuneen SQL-injektio hyökkäyksen vaikutus?__
* Hyökkääjän on mahdollista saada käsiinsä arkaluontoista tietoa esim:
  * Salasanoja
  * Luottokorttitietoja
  * Henkilökohtaisia tietoja

__SQL-injektio esimerkkejä__
* Salatun tiedon hakeminen.
* Sovelluslogiikan kumoaminen/häirintä/muuttaminen.
* UNION-hyökkäys (mahdollistaa tiedon hakemisen eri tietokannoista).
* Tietokannan tarkkailu.
* Sokea SQL-injektio (hallitun jonon tulokset eivät palaa sovelluksen vastauksina).

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
  * Parametrisoituja kyselyjä voidaan käyttää tilanteissa, joissa epäluotettava syöte näkyy tietona kyselyn sisällä, mutta niitä ei voida käyttää käsittelemään epäluotettavaa syötettä kyselyn muissa osissa, kuten taulukoiden tai sarakkeiden nimissä tai ORDER BY -lauseessa. 
* Jotta SQL-injektio voidaan estää tehokkaasti, kyselyssä käytetyn merkkijonon on aina oltava kovakoodattu vakio, eikä se saa koskaan sisältää muuttuvia tietoja.


### PortSwigger: Cross-site scripting

__Mitä tarkoittaa cross-site scripting (XSS)?__
* 





















## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
