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
