## X)

- Tuossa hubacek videossa käytiin läpi URH:ia. Siinä näytettiin sen toiminta ja miten sillä saa tallennettua kaukosäätimen radio taajuuksia työkaluun.
- Näytettiin miten radio taajuus demoduloidaan eli muutettiin bittijonoksi. Ja analysoitiin taajuutta josta saatiin kaukosäätimen koodia selville.

- Cornelius artikkelissa dekoodataan Auriol niminen sääaseman signaalia. Ihan tuolla RTL-433 työkalulla saatiin tunnistettua signaali ja analysointi tapahtuu URH:in kautta.
- Muutettiin omaksi merkkijonoksi tuolla digital analyzis avulla. Siitä saatiin bitit esille.


## b) RTL-433

- Tämä saatiin tunnilla ladattua koneelle ja testattua sillä radio laitteella.
<img width="666" height="73" alt="image" src="https://github.com/user-attachments/assets/1eda98e3-3300-46b7-8582-4760d55717aa" />



## c) Automaattinen Analyysi

- Lataan teron sivulta kyseisen tiedoston ja ajan RTL-433 työkalun, jotta pystyn tutkimaan tiedostoa.

<img width="1095" height="768" alt="image" src="https://github.com/user-attachments/assets/11d3b86b-3860-4e9c-ba0e-15b6097461b2" />

- Ylhäällä lukee, "Test mode active" eli luetaan tällä hetkellä tiedostoa. Sieltä voidaan katsoa esim. Modelit joita on KlikAanKlikUit-Switch, proove-Security, nexa-Security. Nämä tulivat jo vastaan tunnilla, kun tutkimme kaukosäätimen radio taajuutta.
- Sitten näkyy time eli aikaleima jolloin lähetys on tullut kaukosäätimestä. Tuosta huomataan tunniste joka on 8785315. RTL-työkalu tunnistaa jotenkin laitteet eri laitteeksi niin siitä ei ole varmuutta mikä on oikea.


## d) Too complex 16?

- Hieman tutkimalla ja googlettamalla tuo urh:in complex16 tiedoston pystyy muuntamaan suoraan rtl yhteensopivaksi, koska se on sama muoto mutta ei vaan ymmärrettävässä muodossa rtl-433 työkalulle.
````
cp Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded_433.92M_2000k.cs8

````
- Eli ihan -cp komennolla teen uuden kopion tiedostosta ja muutan sen 433.92 taajuuteen ja lisään näytetaajuuden myös tiedoston nimeen eli 2000k. Sitten viel rtl-433 työkalulle ymmärrettävään muotoon eli cs.8.

<img width="630" height="60" alt="image" src="https://github.com/user-attachments/assets/119a418d-20b4-4ccd-8688-e1405ce28540" />

- Huomaan että onnistunut kopio on tehty tiedostosta joten lähden rtl-433 työkalulla sitten tutkimaan niinkuin aikaisemmassa tehtävässä.

<img width="1092" height="755" alt="image" src="https://github.com/user-attachments/assets/06834cc6-e57a-46fc-a641-1387304f1d35" />

- Sitten hetken tätä tiedostoa tutkittua pohdin, että näyttää aika samalta? Kävin id:tä lävitse ja laitteita lävitse niin oli siis sama. Varmistin vielä tekoälyn kautta, että huijaako omat silmäni. Niin tulokset ovat siis samat kuin aikasemmassa. Eli esim. ID house code oli 8785315 joka on täysin sama kuin aikaisemmassa.


## e) Ultimate radio hacker

- Tunnilla asensin URH:in jo koneeseeni. Ihan siis komennolla

````
pipx install urh
````
- Avaan ultiamte radio hackerin ja sen kyseisen tiedoston.

<img width="1418" height="725" alt="image" src="https://github.com/user-attachments/assets/716e6dfa-d960-40da-a896-6b46e721a72f" />


- Tässä on alku kuva tiedostosta kun sen heti avaa.

## f) yleiskuva
- Koitin katsoa URH:ista jos näkyisi. Eli HackRF ja päivämäärä 12.4.2025 klo 11.38.

<img width="467" height="182" alt="image" src="https://github.com/user-attachments/assets/fb69b584-4f81-4ad0-be28-7cc903cf4524" />


- Signaalin taajuus on tuo 433.912 Mhz joka oli myös siinä rtl-433 työkalulla katsottuna. Pituudesta en ole ollenkaan varma.
- 2000k = näytetaajuus ja 2MHz = kaistanleveys
- Kuvan käyrästä päätellen niin kolme painallusta ainakin kaukosäätimellä, kun painalluksen jälkeen on pieni tauko ennen seuraavaa.

## g) Bitit

- Modulaation voi katsoa URH:in kuvasta suoraan. Siellä on ASK-modulaatio.
- Pulssin pituutta on hankala laskea. Tai jotenkin en saa Ultimate radio hacker työkalusta irti sitä. Viimeisenä vaihtoehtona kysyin Claude AI:lta vinkkiä asiaan. Ja sieltä tulee sellainen, että URH:in 500-520 näytettä on noin. 260 µs. Eli sen pulssi.
- Raaka-biteistäkin oli hieman hankaluutta selvittää. Selvittämällä noita bittijonoja joissa usein näkyy 10 ja 100 000 niin se on PPM koodauksen kaksi bittiä.
- Tutkin lähemmäs noita kaukosäätimen pulskeita mutta en saanut selville. 


## Lähteet

- Claude AI-tekoäly
- https://telcochisel.sourceforge.io/tools/urh/ / luettu 4.11.2026
- https://github.com/merbanan/rtl_433  / luettu 5.11.2026 
- https://github.com/jopohl/urh / luettu 5.11.2026 
- https://www.youtube.com/watch?v=MTzFFOBYyZA / luettu 5.11.2026 
- https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s / luettu 5.11.2026
- terokarvinen.com / luettu 5.11.2026
