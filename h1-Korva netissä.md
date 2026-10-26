## X) Spektrini

- Tässä on omasta tekemästäni sähkömagneettinen Spektri

<img width="944" height="431" alt="{85DB9DB2-408F-4524-A9BB-DB77CAA8F90A}" src="https://github.com/user-attachments/assets/799bea71-0300-43d7-8b4b-109f0582c0e3" />

- Eli lyhkäisyydessään aallonpituus kasvaa jos taajuus pienenee. Läpäisevyys riippuu taas taajuudesta ja siitä mitä materiaaleja on ohessa. Tiedonsiirronkannalta suurempi taajuus liikuttaa enemmän tietoa mutta sen nopeus ei ole suurempi.

## a) WebSDR

- Siirryin WebSDR sivulle ja aloin katsomaan radiokanavia.

<img width="2243" height="147" alt="{6FDE6421-2C40-42D2-B81F-20866F3EAF00}" src="https://github.com/user-attachments/assets/7b955053-4834-4282-9872-673cfac951e4" />

- Siirryin tällaiselle Kreikassa olevaan sparta radioon.

<img width="1058" height="750" alt="{4E4361A0-E08B-4909-922D-C04AF527C427}" src="https://github.com/user-attachments/assets/8da15e2a-6328-4b28-a8aa-e701fd1e17c7" />

- Hieman jouduin säätämään asetuksia ja eri modulaatioiden välillä jotta sain selkeää radiopuhetta. Sain selkeää yhden henkilön puhumista.
- Kuvassa on siis taajuus 3735 kHz ja LSB modulaatio. Filtterinä 2,85 kHz.
- Aallonpituuden laskemiseen käytin everythinRF : sivun laskinta joka laskee taajuudesta aallonpituuden ja sen tulos on 80mm.

<img width="714" height="212" alt="{BF94F2A7-9365-4543-B7B5-8CBC782C5A7D}" src="https://github.com/user-attachments/assets/1a289e71-893a-4ed3-b5bb-d67335e8c88a" />

## b) Moduwhat?

- Pysyin samalla Spartasdr.gr sivuilla ja muutin modulaatiota FM:ksi. Puheesta tuli epäselvää mutta esim. CW modulaatiosta sai puheesta hieman selvää mutta tuntui kuin puhuisi puhelinkopista.
- Seuraavasta kohdasta 3715 taajuudelta löytyi kanava josta kuului hyvin selkeästi ja oli eri henkilön puhetta.
  
<img width="1018" height="314" alt="{066CC26B-E05D-4CCF-9AF6-9B50AF76BF9B}" src="https://github.com/user-attachments/assets/323323a5-9176-4ab6-a353-1004d5f73314" />
(Kuva muunnettu kun vahingossa laitoin väärän screenshotin)

## c) ADS-B

- Selailin ADS-B Exchange sivua ja koitin etsiä mieleistä lentokonetta jota tutkia. Otin lähi-idästä Dubaihin saapuvan lentokoneen Qatar Airways.

<img width="839" height="598" alt="{3524E553-B195-4DDA-8E16-CB8AB82BC510}" src="https://github.com/user-attachments/assets/2b2f98b7-27ba-4871-8f4a-a12ee680c1bb" />

- Siitä tietokoneesta kaikki tiedot eli (Hyödynsin claudea varmistamaan, että tiedot ovat oikein listalla vs ADS-B exchangen sivulla.

````
Kutsutunnus: QTR5Y
Rekisteri: A7-AOA
Lentoyhtiö: Qatar Airways
Tyyppi: A35K
Tyypinkuvaus: L2J
Malli: Airbus A-350-1000
Pituus: 242.5 ft = 73,9 metriä
Korkeus: 56 ft = 17.06 metriä
Siipiväli: 212.5 ft = 64.7 metriä
Polttoaineenkulutus: 1441.2 gal/hr = 5 455,54 l/h
````
- Oheessa kuva lentokoneen tiedoista. 

<img width="1140" height="568" alt="{23C34436-A49B-4D14-81EF-BDC15CB9E8C3}" src="https://github.com/user-attachments/assets/9aef2711-4a5b-4004-bb30-fceb15851da4" />



# Lähteet

- https://www.britannica.com/science/electromagnetic-spectrum - elektromagneettinen spektrumi
- http://websdr.org/ - WebSDR
- http://sv3gcb.ddns.net:8905/ - SpartaSDR radio
- https://globe.adsbexchange.com/ - taajuus aallonpituus muunnin
- ClaudeAI käytetty lentokoneen tietojen selventämiseen.
