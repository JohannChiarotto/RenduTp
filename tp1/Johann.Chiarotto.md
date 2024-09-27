# TP1 : Les premiers pas de bébé B1

#
## I. Récolte d'informations
#
🌞Adresses IP de ta machine

- affiche l'adresse IP que ta machine a sur sa carte réseau WiFi
```
PS C:\Users\chiar> ipconfig

[...]

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.79.1
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```

-  affiche l'adresse IP que ta machine a sur sa carte réseau ethernet

```
J'ai pas de carte éthernet
```
#
🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...

- affiche l'adresse IP de la passerelle du réseau local

```
PS C:\Users\chiar> ipconfig /all

[...]

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   Adresse physique . . . . . . . . . . . : A8-41-F4-EA-29-B5
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.79.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:12:36
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:12:36
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 111690228
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-DA-E5-26-00-DE-AB-CA-AB-72
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

- affiche l'adresse IP du serveur DNS que connaît ton PC

```
PS C:\Users\chiar> ipconfig /all

[...]

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   Adresse physique . . . . . . . . . . . : A8-41-F4-EA-29-B5
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.79.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:12:36
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:12:36
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 111690228
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-DA-E5-26-00-DE-AB-CA-AB-72
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

- affiche l'adresse IP du serveur DHCP que connaît ton PC

```
PS C:\Users\chiar> ipconfig /all

[...]

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC
   Adresse physique . . . . . . . . . . . : A8-41-F4-EA-29-B5
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.79.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:12:36
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:12:36
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 111690228
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-DA-E5-26-00-DE-AB-CA-AB-72
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
#
🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine








#
# II. Utiliser le réseau
#

🌞 Envoie un ping vers...

- toi-même !
```
PS C:\Users\chiar> ping 10.33.79.1

Envoi d’une requête 'Ping'  10.33.79.1 avec 32 octets de données :
Réponse de 10.33.79.1 : octets=32 temps<1ms TTL=128
Réponse de 10.33.79.1 : octets=32 temps<1ms TTL=128
Réponse de 10.33.79.1 : octets=32 temps<1ms TTL=128
Réponse de 10.33.79.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.79.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

- vers l'adresse IP 127.0.0.1

```
PS C:\Users\chiar> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
#
🌞 On continue avec ping. Envoie un ping vers...

- ta passerelle

```
PS C:\Users\chiar> ping 10.33.79.254

Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
```

- un(e) pote sur le réseau

```
PS C:\Users\chiar> ping 10.33.66.78

Envoi d’une requête 'Ping'  10.33.66.78 avec 32 octets de données :
Réponse de 10.33.66.78 : octets=32 temps=103 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=47 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=19 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=40 ms TTL=64

Statistiques Ping pour 10.33.66.78:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 19ms, Maximum = 103ms, Moyenne = 52ms
```

- un site internet

```
PS C:\Users\chiar> ping www.thinkerview.com

Envoi d’une requête 'ping' sur www.thinkerview.com [188.114.96.7] avec 32 octets de données :
Réponse de 188.114.96.7 : octets=32 temps=17 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=18 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=19 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=40 ms TTL=55

Statistiques Ping pour 188.114.96.7:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 17ms, Maximum = 40ms, Moyenne = 23ms
```
#
🌞 Faire une requête DNS à la main

- ça se fait en une seule commande, je te laisse la chercher sur internet

```
nslookup
```

- effectue une requête DNS à la main pour obtenir l'adresse IP qui correspond aux noms de domaine suivants:

```
PS C:\Users\chiar> nslookup www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3121::7
          2a06:98c1:3120::7
          172.67.189.166
          104.21.73.104
```

```
PS C:\Users\chiar> nslookup www.wikileaks.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  51.159.197.136
          80.81.248.21
Aliases:  www.wikileaks.org
```

```
PS C:\Users\chiar> nslookup www.torproject.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe7f:1826
          2a01:4f9:c010:19eb::1
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          116.202.120.166
          95.216.163.36
          116.202.120.165
          204.8.99.144
          204.8.99.146
``` 



#
# III. Sniffer le réseau
#


➜ Refais les commandes ping de la partie précédente

🌞 J'attends dans le dépôt git de rendu un fichier ping.pcap

🌞 Livrez un deuxième fichier : dns.pcap

#
# IV. Network scanning et adresses IP
#

🌞 Effectue un scan du réseau auquel tu es connecté

nmap.exe -sn -PR 10.33.64.0/20

🌞 Changer d'adresse IP

```
PS C:\Users\chiar> ipconfig
[...]
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::28cf:3eed:aab4:8bf7%11
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.76.43
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```