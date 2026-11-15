# h4 NFC ja RFID


# a) Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?

- Tässä heti ajateltuna niin ensimmäisinä asioita mitä käytän eniten ovat:
````
- Maksukortit ja erilaiset jäsenyys kortit kuten salikortti.
- Henkilökortti
- Oma avain (iLoq)
- Puhelin
- Älykello
````
- Tässä kun ajattelee niin en ole ihmeemmin suojannut itseäni RFID urkinnalta. Maksukorteissa on suhteellisen turvallinen se suojaus ja henkilökortit kuten passi niin sehän biometrinen suojaus.
- Kuitenkin nuo erilaiset jäsenyyden kortit on varmaan helpompi kopioida. Jos nämä käyttävät siis vanhempaa tekniikkaa. Täten en siis ole kovin suojautunut näiden suhteen.
- Sitten älylaitteet kuten puhelin ja älykello niin näissä on omat suojaus tekniikkansa. Niin en ole koskaan sen ihmeellisemmin ajatellut tarkemmin asiaa, kuin että tietoni pysyvät tallessa.
- Ehdottomasti voisin suojautua paremmin esim. maksukorttien ja muiden korttien suhteen hommaamalla sellaisen RFID suojatun lompakon. Mutta ei ole vielä sattunut mitään joten en ole hommannut sellaista.


# b)  Tutustu APDU komentojen rakenteeseen

- Hyödynsin Claude tekoälyä APDU -tutustumiseen.
- Lyhkäisesti siis Application Protocol Data Unit on standardien mukainen viesti muoto, millä lukija ja älykortti keskustelevat toisensa kanssa. Eli se miten tiedonsiirto käy näiden välillä.
- Näitä käytetään esimerkiksi: maksukorteissa, NFC-laitteet ja kortit ja SIM-kortit.
- Application Protocol Data Unit:illa on tietynlainen perusrakenne. Ne ovat siis :
 
````
CLA - eli määritellään komennon luokka
INS - kertoo suoritettavan toiminnon.
P1 - Ensimmäinen komentoon tarkoitettu parametri
P2 - Toiseen komentoon tarkoitettu parametri
````
- Jonka lisäksi tähän saisi lisättyä myös muita komentoja. Mutta ne eivät ole välttämättömiä.

- APDU komennon rakenne liittyy kovasti siihen, mitä komentoja suoritetaan sillä. Sen takia ei tarvita jokaista APDU- komentoriviä mukaan.
Kun NFC-kortti tai älykortti saa parametrin niin se käsitellään ja vastataan takaisin lukijalle. Palauttavassa datassa on lisättynä tilakoodeja joilla pystytään määritellä onko se onnistunut vai ilmenikö ongelmia tiedonsiirrossa.



# c) Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. 

- Itse selailin hieman hackernews sivuja ja menin taaksepäin ajassa. Tämä on parin vuoden takaa 2024 ja kyseessä on taka-ovi RFID kortteihin jolla pystyy heti kloonaamaan sen tiedon.
Tällainen ranskalainen turva-yritys **Quarkslab** löysi kiinalaisen yrityksen **Shanghai Fudan Microelectronics Group** valmistamista RFID sirukorteista valtavan taka-oven. Ja siis tarkennuksena esim. mihin tämän yrityksen valmistamat RFID-kortit käyvät ovat lukuisat hotellit ja eri toimistopaikat.
Eikä yrityksen myyneet RFID koodit koske vain kiinassa olevia, koska nämä ovat myyneet omia RFID korttejaan eurooppaan sekä amerikkaan.

- Taka-ovi toimii siis siten, että hyökkääjä tarvitsee vain pari minuuttia lähietäisyydeltä kohde RFID-korttiin ja tämän jälkeen hän saa itselleensä täydellisen kloonatun kortin. Artikkeli kertoo ongelman vakavuuden johtuvan siitä, että tämän hyökkäyksen pystyy ketjuttamaan ja skaalaamaan erilaiselle tasolle.
Samalla kun tutkittiin asiaa lisää, niin tuli ilmi, että laitteisto takaportti antaa authentikointi pääsyn **tuntemattomalla** avaimella. Tässä juuri painotetaankin sitä, että yritykset eivät ole varmaan tietoisia omista RFID-korteistaan jotka ovat juuri tulleet esim. tältä yritykseltä joka myy.





# Lähteet

RFID takaportin artikkeli - https://www.securityweek.com/major-backdoor-in-millions-of-rfid-cards-allows-instant-cloning/
Backdoor in RFID cards - https://news.ycombinator.com/item?id=41312975
Application Protocol Data Unit (APDU) - https://www.cardlogix.com/glossary/apdu-application-protocol-data-unit-smart-card/
What is RFID technology? - https://idesco.fi/home/about-us/what-is-rfid-technology/
RFID and NFC difference - https://iotjourney.orange.com/en/support/faq/what-is-the-difference-between-nfc-and-rfid
