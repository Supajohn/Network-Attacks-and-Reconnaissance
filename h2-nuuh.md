## x) 

- Wireshark on sovellus työkalu jolla pystyy katsoa verkkoliikenteen toimintaa ja analysoida sitä.
- Sillä pystytään kaappaamaan liikenteestä erilaisia paketteja ja katsoa verkon informaatiota.
- Display filtterit ovat apukomentoja joilla voidaan rajata verkon näkymää.

- Karvinen 2025 Network interface eli verkkoliitäntä on periaatteessa melkein kuin verkkokortti.
- Eri nimet tulevat systemd:ltä kuten : en = langallinen ethernet, wl = WLAN ja lo = loopback.
- Omia komentoja on esim ip a ja ip route.

## a) Linux
- Hops löytyy Debian 13 Trixie.

## b) Ei voi kalastaa

- Virtuaalikoneesta pystyy helposti katkaisemaan verkon yhteyden napautuksella.

<img width="182" height="72" alt="image" src="https://github.com/user-attachments/assets/0cba6305-d6e3-42c4-9d7f-fd6f1fd82f56" />

- Wireshark pysähtyy kokonaan ja verkkosivut myös eivät lataudu enää.


## c) Wireshark

- Wiresharkin saa ladattua aika helposti linux komentojen avulla.

````
sudo apt-get update
sudo-apt get install wireshark
````
Wireshark auki ja sieltä voi alkaa kaapata liikennettä.

<img width="1342" height="153" alt="image" src="https://github.com/user-attachments/assets/9e4a6c6d-fd4c-44f7-b831-46e614d73952" />

## d) TCP/IP

- Kuvassa näkyy neljä kerrosta paketissa.

<img width="950" height="102" alt="image" src="https://github.com/user-attachments/assets/1643cf1f-252d-450f-8de1-6d79feca1d68" />

- Elikkäs kuvan kerrokset menevät alhaalta ylös.
- Alimpana 4. Domain Name System eli DNS. Sovelluskerros jossa on varsinainen viesti.
- 3. on Transport layer eli kuljetus kerros UDP / TCP. Paketti ohjaantuu oikeaan sovellukselle portin avulla. Omassa näkyykin portti 53.
- 2. Internet kerros eli IPV4. Paketti menee koneelta verkon ylitse ja tässä kohdassa näkyy lähettäjän ja vastaanottajan ip-osoitteet.
- 1. Link layer eli linkki kerros. Kehys liikkuu samassa lähiverkossa. Ja tässä näkee sitten vastaanottajan ja lähettäjän MAC-osoitteet.

## e) Mitäs tuli surffattua?

- Avaan tuon annetun surfing-secure.pcap tiedoston wiresharkissa.
- Ainakin statistics endpoints työkalulla katsoin, niin sain että siellä olisi kaksi laitetta lähiverkossa.
- Ja paketteja ei oikein paljon eli 283 pakettia. Joten sen verran lyhyt surffaushetki.
<img width="37" height="22" alt="image" src="https://github.com/user-attachments/assets/a6439eee-035b-4bc6-b105-671565d97622" />

- Sivuja mitä huomasin jossa surffailtiin oli : terokarvinen.com ja commentero.karvinen.com sitten vielä www.google.com. Vieläpä suurin osa TCP paketteja ja pieni osa UDP:tä.

## g) Minkä merkkinen verkkokortti käyttäjällä on?

- Hieman katselin ja tutkiskelin käyttäjän MAC-osoitetta ja sen ip osoitetta.
  
<img width="987" height="143" alt="image" src="https://github.com/user-attachments/assets/ed8f8f82-0066-48e3-9bf9-3625314ee5a6" />

- Tähän en osaa sanoa varmaa vastausta. Tuon alkuosoitteen alku osa on OUI, ja se ei ainakaan herätä mitään kelloa että olisi fyysinen. Joten veikkaisin sen olevan virtuaalinen verkkokortti.

## h) Webbipalvelin

- DNS ainaki näkee, että on käyty terokarvinen.com sivulla.
<img width="520" height="30" alt="image" src="https://github.com/user-attachments/assets/4b33c8d0-f08f-4478-8e79-a8553fd904bf" />

- Sit toinen mitä tulee selville on commentero.terokarvinen.com joka on myös samassa osoitteessa.
<img width="627" height="32" alt="image" src="https://github.com/user-attachments/assets/8571f970-7d3d-4672-b3bd-796bf70a2a3a" />


## i) Analyysi

- Käyn tämän kohdan lävitse.
<img width="934" height="44" alt="{5BEDF877-4A68-4534-9210-0EDE6EB6F76D}" src="https://github.com/user-attachments/assets/e442d7a1-2917-47af-a6f6-87bc8ae65913" />


- Tässä siis olen koneellani avannut jo youtuben ja laittamassa videota pyörimään. Mutta youtuben ja googlen mainos tuleekin edelle pyörimään. Kuvassa nimeltään googlevideo.com ja youtube.com.
- Kuvassa on virtuaalikoneeni osoite ja sitten reitittimeni osoite josta en laittanut kuvaa.
- Protokollana DNS muuttaa annetun nimen IP-osoitteeksi eli "standard query". Sitten eri kyselytyypi eli A kysyy nimen IPv4-osoitetta. Sitten taas AAAA kysyy IPv6-osoitetta. Koska jos IPv6 on käytössä niin sitä käytetään mielummin.
- Eri tunnisteet kuvassa kuten 0xd743 ja 0x4b41 ovat eri. Tämä antaa koneen yhdistää vastauksen oikeaan kysymykseen.
- Ajan perusteella paketit olivat aika nopeita edestakaisin.
- Muuta en osaa enää oikein sanoa.



## Lähteet

- https://www.freedesktop.org/software/systemd/man/latest/systemd.net-naming-scheme.html - Luettu 31.10.2026
- https://terokarvinen.com/network-interface-linux/ - Luettu 1.11.2026
- https://terokarvinen.com/wireshark-getting-started/ - Luettu 1.11.2026
- https://hackercoolmagazine.com/beginners-guide-to-wireshark/?v=75778bf8fde7 - Luettu 31.10.2026
- https://www.freecodecamp.org/news/use-wireshark-filters-to-analyze-network-traffic/ - Luettu 31.10.2026
- https://www.youtube.com/watch?v=a_4MjV_-7Sw - Luettu 31.10.2026
