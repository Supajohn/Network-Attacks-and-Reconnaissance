## a) Aja tunnilla esitetty ARP hyökkäys ja tutki, miten se toimii.

- Aloin käymään itse lävitse ARP hyökkäystä ja laitoin taustat ensin pystyyn moodlesta ohjeiden avulla. Alustetaan mininet virtuaalikone ja laitetaan sinne pyörimään ryu-manageri.
````
ryu-manager ryu.app.simple_switch_13 &
````
Mininet virtuaalikoneessa näyttää tältä 

<img width="512" height="107" alt="image" src="https://github.com/user-attachments/assets/8b80fe55-9c9c-4d80-8bd0-a52c6de4a1a1" />


- Laitoin komennon perään & -merkin jotta se ajaa sitä jatkuvasti taustalla.
- Sitten voidaan jatkaa mininetin komentorivin käyttöä ja ajettiin mininetin hyökkäystä kohti.
````
sudo mn --topo single,3 --mac --switch ovsk --controller remote
````
- Tämän jälkeen testasin järjestelmää **pingall** ja **xterm h1** komennolla. Aluksi oli hieman ongelmia xterm komennon kanssa mutta sain apuja moodlen vinkki osiosta ajamalla **./get_xauth.sh** komennon.

<img width="900" height="72" alt="image" src="https://github.com/user-attachments/assets/0b378eea-6ec9-4829-a37c-67b6edb7fbe1" />

- Sitten vielä laitoin aktiiviseksi tuon cookie valuen.

- Nyt itse tehtävään eli avasin näkymän h1 koneelle ja siitä haettiin **arp -n** komennolla taulukko näkyville. Tässä on siis perusnäkymä.
<img width="531" height="101" alt="image" src="https://github.com/user-attachments/assets/0db5edac-d01f-4641-a048-d6ed782bfe37" />

- Nyt ajetaan komennot node h3 komentoriville, että saadaan hyökkäys aikaan ja tallennettua.
````
sysctl -w net.ipv4.ip_forward=1
iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 22
tcpdump –i h3-eth0 –w arp-p.pcap &
wireshark &
sshesame -port 22 -listen_address 0.0.0.0
````
- Tältä se näyttää kuvassa.

<img width="651" height="236" alt="image" src="https://github.com/user-attachments/assets/06925e75-2b5f-4b3b-8611-9314727da122" />

- Sitten lähdin jo testaamaan toisella h3 node terminaalilla arp.poison.py:n ajamista. Mutta ongelmaksi tulee että on väärä ssh avain käytössä.

<img width="1360" height="632" alt="{DF3DDF29-0813-4F00-BB8D-B860E59C2B80}" src="https://github.com/user-attachments/assets/c0d6736d-5110-442e-9dbf-893b2ef133ee" />

- Joten siellä ilmenee **failed to establish ssh connection ja se estää hyökkäyksen. Korjaan asian ohjeiden mukaan eli **ssh-keygen -R h2** komennolla node h1 komentoriville.

- Tämän jälkeen ajetaan uusiksi ja onnistuu ARP-hyökkäys.
<img
  width="1576" height="566" alt="image" src="https://github.com/user-attachments/assets/f08ae4ab-7570-4382-a751-164ea3e8fb80" />


## b) Samassa hakemistossa on myös ICMP Spoofing ja TCP Session Hijacking. Aja molemmat labrat läpi ja kerro, miten molemmat tekniikat toimivat.

- Tässä ensimmäisenä teen TCMP spoofing tehtävän ja aloittamalla kloonasin tuon annetun annetun repositoryn.
````
git clone https://github.com/ssam246/Network-Security-Lab#
````

- Sen jälkeen lähdin käynnistämään python tiedostoa jotta voidaan minineti:llä tutkia scriptejä.
````
sudo python3 hub_topo.py
````
- Tämän jälkeen avasin **xterm** komennolla nodet h1 ja h2 ja annoin ohjeiden mukaiset tiedot eli sniff pythoni ja pingataan toisessa.

````
h1 pyhton sniff_icmp.py
h2 ping 10.0.0.1
````
- Ja se kyllä onnistuu.

<img width="827" height="612" alt="image" src="https://github.com/user-attachments/assets/847456d8-b6c8-4d4f-9c97-70a0a4dff806" />

- Eli tässä lyhkäisyydessään siis hyökkääjä muodostaa paketin jonka lähettää, mutta siinä paketissa hyökkääjän ip-osoite on **väärennettynä**. Sitten kohdekoneessa paketti ei voi olla varma tämän lähettäjän henkilöllisyydessä.


** TCP Session Hijacking** ajoin eri nodeissa h1, h2 ja h3 eri omat komentonsa ohjeiden mukaisesti.
- Tässä seurasin kyllä ohjeita mutta en oikein saanut selvää.
<img width="1255" height="502" alt="image" src="https://github.com/user-attachments/assets/064e1121-8aa5-4b68-a807-3e622e2a6a76" />

- Ajoin jokaisen nodessa omat komentonsa mutta se ei tuottanut mitään. Joten jäin hieman hämmentyneeksi tämän tehtävän suhteen.


## c) Hakemistossa 02-SDN-DDos_Simulation tryout-kansiossa on työkalut, jotta voit ajaa TCP SYN-Flood-hyökkäyksen turvallisesti. Kirjoita, miten ajoit hyökkäyksen ja miten kyseinen hyökkäys toimii.

- Eli koitetaan luoda DoS eli Denial of Service hyökkäys. Eli hyökkääjä lähettää paljon avoimia paketteja jotka ruuhkauttavat ja kuormituttaa palvelimen. Isoin vahinkona on siis palvelimen kaatuminen tai ainakin varmasti hidastuminen.

- Lähdin tässä hieman tekoälyn voimin Claude AI:lta. Kyseessä on siis simppeli http pakettien lähettäminen.
- Aloitin luomalla virtuaalisen verkko ympäristön ja sen sai suoraan komennolla. Tämä luo siis yhden avoimen kytkimen ja 3 kpl hosteja sekä verkon joka yhdistää kaiken.

````
sudo mn --topo single,3 --mac --switch ovsk --controller 
````
<img width="946" height="307" alt="image" src="https://github.com/user-attachments/assets/6a1a878a-bedb-4882-a08d-7f430a8d3237" />

- Valitsin host 2 olevan tämä "uhri" eli kenelle pystytin TCP-palvelimen komennolla. Ja vielä pyörimään taustalle.
````
h2 python3 -m http.server 8080 &
````
<img width="380" height="22" alt="image" src="https://github.com/user-attachments/assets/c39a9c41-acab-499e-bd15-6b9de2310b5c" />


- Sitten latasin tällaisen **hping3** komennon joka siis simuloi TCP pakettien lähettämistä. Eli pystyy generoimaan sen lähettämiseen tarvittavat paketit.
````
h1 hping3 -S -p 8080 -c 100 10.10.X.X
````
<img width="622" height="35" alt="image" src="https://github.com/user-attachments/assets/359e6705-f10f-4ba6-9b75-0ff93abaafe2" />

- Tällaisellä komennolla lähdin sitten paketteja kohti kohdetta eli host 2 pystyttämää palvelinta.
- Tuossa siis **-S** on TCP-SYN flag, porttina 8080, **-c** argumentilla voidaan valita paljonko paketteja niin otin 100. Sitten kohde ip-osoite.
- Toki nyt ei tuolla 100 paketilla se host palvelin kaatunut mutta tämä oli hyvä kokeilla.


# Lähteet

- https://github.com/santhisenan/SDN_DDoS_Simulation - DDoS simulaatio
- Moodle
- https://github.com/ssam246/Network-Security-Lab - Security lab
- https://www.cloudflare.com/learning/ddos/glossary/denial-of-service/ - Denial of service
- Claude tekoäly
- https://www.azion.com/en/learning/ddos/what-is-smurf-attack/ - TCMP Spoof hyökkäys
- https://www.sciencedirect.com/topics/computer-science/session-hijacking - Session hijacking
- https://www.youtube.com/watch?v=cZ-7R8juECk - ARP middle-man attack
