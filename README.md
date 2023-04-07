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
  * Syöttämällä payloadeja, jotka on suunniteltu aiheuttamaan viivettä SQL-jonoissa, ja sen jälkeen tarkkailemalla vastausaikoja.
  
__























## Lähteet
https://terokarvinen.com/2023/tunkeutumistestaus-2023-kevat/#h2-totally-legit-sertificate </br>
https://portswigger.net/web-security/sql-injection </br>
https://portswigger.net/web-security/cross-site-scripting </br>
