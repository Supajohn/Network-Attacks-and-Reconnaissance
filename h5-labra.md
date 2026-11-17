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
<img width="1576" height="566" alt="image" src="https://github.com/user-attachments/assets/f08ae4ab-7570-4382-a751-164ea3e8fb80" />


## b) Samassa hakemistossa on myös ICMP Spoofing ja TCP Session Hijacking. Aja molemmat labrat läpi ja kerro, miten molemmat tekniikat toimivat.

- 4


## c) Hakemistossa 02-SDN-DDos_Simulation tryout-kansiossa on työkalut, jotta voit ajaa TCP SYN-Flood-hyökkäyksen turvallisesti. Kirjoita, miten ajoit hyökkäyksen ja miten kyseinen hyökkäys toimii.

- k
