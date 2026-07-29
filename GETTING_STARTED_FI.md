# Scoutlyn aloitusopas

[Guide in English](GETTING_STARTED.md)

Scoutly seuraa julkisten verkkosivujen hintoja, saatavuutta, tekstiä ja muita hyödyllisiä arvoja. Windows-sovellus toimii pääasiallisena työtilana. Scoutly Mobile voi käyttää samaa salattua työtilaa ja tehdä yhteensopivia tarkistuksia Androidissa.

## Scoutlyn asentaminen

Lataa nykyinen paketti [uusimmasta julkaisusta](https://github.com/luaksone/scoutly-releases/releases/latest):

- Windows-asennusohjelma on tavallinen valinta tietokoneelle.
- Windowsin siirrettävää sovellusta voi käyttää asentamatta.
- Androidin APK asennetaan sen ladanneen selaimen tai tiedostonhallinnan kautta. Android saattaa pyytää luvan sovellusten asentamiseen.

Windows-paketteja ei ole tällä hetkellä allekirjoitettu, joten Windows voi näyttää SmartScreen-varoituksen. Lataa Scoutly vain tästä repositoriosta ja vertaa tiedoston SHA-256-tiivistettä [SHA256SUMS.txt](SHA256SUMS.txt)-tiedostoon.

## Ensimmäisen seurannan luominen

1. Avaa **Seurannat** ja valitse **Uusi seuranta**.
2. Liitä seurattavan julkisen sivun osoite.
3. Anna seurannalle kuvaava nimi.
4. Testaa sivu ennen tallennusta. Varmista, että esikatselussa näkyy oikea tuotteen hinta, saatavuus, teksti tai muu haluamasi arvo.
5. Valitse tarkistusväli ja tallenna seuranta.

Käytä järkevää tarkistusväliä. Verkkokaupan tarkistaminen muutaman sekunnin välein on harvoin hyödyllistä ja voi johtaa pyyntöjen rajoittamiseen tai estämiseen.

Vertaa hintaseurannan tulosta sivulla näkyvään tuotteen hintaan. Älä hyväksy ostoskorin loppusummaa, rahoituksen kuukausierää, yliviivattua vanhaa hintaa tai yksikköhintaa päähinnaksi. Scoutly torjuu tällaisia arvoja automaattisesti, mutta monimutkainen tai usein muuttuva sivu voi silti vaatia arvon valitsemista käsin.

Dynaaminen sivu saattaa edellyttää selainrenderöintiä. Tavallinen eli staattinen tarkistus kuluttaa vähemmän resursseja ja on parempi valinta silloin, kun se toimii oikein.

## ntfy-ilmoitusten määrittäminen

ntfy voi välittää tietokoneen Scoutly-hälytykset puhelimeen tai sähköpostiin.

1. Asenna ntfy-mobiilisovellus tai avaa ntfyn verkkosovellus.
2. Valitse pitkä ja yksityinen, vaikeasti arvattava aiheen nimi ja tilaa täsmälleen sama aihe.
3. Avaa Windowsin Scoutlyssa **Asetukset** ja etsi **Ilmoitukset**.
4. Säilytä palvelimena `https://ntfy.sh` tai syötä oman ntfy-palvelimesi osoite.
5. Syötä sama aihe, ota puhelinilmoitukset käyttöön ja tallenna.
6. Lähetä testi Scoutlyn testipainikkeella.

Käsittele suojaamattoman aiheen nimeä salasanan tavoin: nimen tietävä henkilö saattaa pystyä tilaamaan aiheen tai julkaisemaan siihen. Syötä suojattua aihetta varten ntfy-tilin tai palvelimen ylläpitäjän antama käyttöoikeustunnus.

Jos haluat sähköposti-ilmoituksia, lisää ja vahvista vastaanottaja ntfyssä, ota sähköposti-ilmoitukset käyttöön Scoutlyssa ja lähetä uusi testi. Tilien ja sähköpostien ehdot riippuvat käytetystä ntfy-palvelimesta.

Tietokoneelta välittäminen toimii, kun Scoutly on käynnissä myös ilmaisinalueella ja tietokone on hereillä. Scoutly Mobile voi näyttää Androidin järjestelmäilmoituksia myös puhelimessa paikallisesti tehdyistä yhteensopivista tarkistuksista. Ne eivät tarvitse ntfyä.

## Salatun Supabase-synkronoinnin määrittäminen

Supabase välittää tiedot laitteiden välillä. Scoutly salaa työtilan tiedot laitteella ennen lähettämistä. Supabaseen tallennetaan salatekstiä, eikä palvelu voi lukea seurantojen nimiä, osoitteita, valitsimia, hintoja tai hälytyksiä ilman parituskoodiasi.

### Supabasen valmistelu

1. Luo projekti osoitteessa [supabase.com](https://supabase.com/).
2. Avaa Windowsin Scoutlyssa **Asetukset** ja sitten **Synkronointi**.
3. Valitse **Tallenna asennuksen SQL-tiedosto**.
4. Avaa Supabase-projektin **SQL Editor**, liitä tallennetun tiedoston sisältö ja suorita se.
5. Kopioi Supabase-projektin asetuksista **Project URL** ja **Publishable key**. Myös vanha anonyymi avain toimii.

SQL-asennus luo vain Scoutlyn tarvitsemat tietorakenteet ja käyttöoikeussäännöt. Jos myöhempi Scoutly-versio ilmoittaa etärakenteen olevan vanhentunut, tallenna ja suorita uusin SQL-asennustiedosto uudelleen.

### Työtilan luominen ja parittaminen

1. Syötä Windowsin Scoutlyyn projektin osoite, julkaistava avain ja laitetta kuvaava nimi.
2. Valitse **Luo salattu työtila**.
3. Pidä luotu parituskoodi salassa. Koodi ja Supabase-yhteystiedot mahdollistavat työtilan avaamisen.
4. Avaa Scoutly Mobilessa **Asetukset** ja **Scoutly-synkronointi**.
5. Skannaa tietokoneella näkyvä QR-koodi tai liitä paritustiedot.
6. Käynnistä ensimmäinen synkronointi.

Parituksen jälkeen seurannat, kansiot, historia, hälytykset, kiinnitykset ja opitut sivustosäännöt voivat siirtyä laitteiden välillä. Valitse kullekin seurannalle suorittava laite:

- **Tietokone** tarkistaa seurannan vain tietokoneella.
- **Android** tarkistaa seurannan vain puhelimessa.
- **Kumpi tahansa** antaa vapaan laitteen tehdä seuraavan tarkistuksen.
- **Molemmat** sallii tarkistamisen molemmilla laitteilla.

Vältä **Molemmat**-valintaa, ellet halua päällekkäisiä tarkistuksia. Käyttöjärjestelmä päättää Androidin taustatöiden tarkan ajankohdan. Poista Scoutly akkukäytön optimoinnista ja salli ilmoitukset, jos puhelimen tarkistusten ajoitus on tärkeä.

Parituskoodin nollaaminen poistaa aiemmin paritettujen laitteiden oikeuden ja salaa jaetun työtilan uudelleen. Etätyötilan poistaminen ei poista laitteelle jo tallennettuja paikallisia tietoja.

## Ongelmatilanteet

- **Tunnistettu hinta on väärä:** testaa seuranta uudelleen ja valitse näkyvä tuotteen hinta. Varmista, ettei Scoutly valinnut yksikköhintaa, ostoskorin summaa, kuukausierää tai yliviivattua vanhaa hintaa.
- **Tietokoneen ilmoitus ei saapunut:** pidä Scoutly käynnissä ilmaisinalueella, varmista että tietokone on hereillä ja lähetä ntfy-testi Asetuksista.
- **Androidin taustatarkistus viivästyy:** salli ilmoitukset, poista Scoutlyn akkukäytön optimointi ja varmista, että seurannan suorittava laite sisältää Androidin.
- **Synkronointi epäonnistuu:** tarkista projektin osoite ja avain, suorita uusin SQL-asennustiedosto ja varmista, että laitteilla on samat paritustiedot.
- **Sivusto lakkaa äkillisesti toimimasta:** sivun rakenne tai automatisoinnin estot ovat voineet muuttua. Testaa seuranta uudelleen ja pidennä tarkistusväliä, jos sivusto rajoittaa pyyntöjä.

Lataukset ja Scoutlyn yleisesittely löytyvät [README-tiedostosta](README.md).
