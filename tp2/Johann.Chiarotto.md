# TP2 : Hey yo tell a neighbor tell a friend

Dans ce TP, on va commencer à construire sur ce qu'on a fait au premier TP.

> ~~On va monter une interco IPsec entre tous les edge routers qui sont pas dans les mêmes zones BGP.~~ Pas du tout, on va encore envoyer des `ping` :d

C'est un TP qui se fait à 2, avec un câble que je vous fournis en cours. Le but : connectez vos deux PCs avec le câble, et faire mumuse.

![LAN](./img/fw.png)

# Sommaire

- [TP2 : Hey yo tell a neighbor tell a friend](#tp2--hey-yo-tell-a-neighbor-tell-a-friend)
- [Sommaire](#sommaire)
- [0. Prérequis](#0-prérequis)
- [I. Simplest LAN](#i-simplest-lan)
  - [0. Setup](#0-setup)
  - [1. Quelques pings](#1-quelques-pings)
- [II. Utilisation des ports](#ii-utilisation-des-ports)
  - [0. Intro blabla](#0-intro-blabla)
  - [1. Animal numérique](#1-animal-numérique)
- [III. Analyse de vos applications usuelles](#iii-analyse-de-vos-applications-usuelles)
  - [1. Serveur web](#1-serveur-web)
  - [2. Autres services](#2-autres-services)

# 0. Prérequis

🌞 Je n'ai pas de port éthernet donc je me suis connecté a ma VM en ssh.

# I. Simplest LAN

## 0. Setup

🌞 J'avais pas besoin de tous changer car je suis directement avec lma VM.

## 1. Quelques pings

🌞 **Prouvez que votre configuration est effective**🌞

🌞 Sur ma VM :

```
johann@johann-ubuntu:~$ ip addr show enp0s8
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:2b:90:80 brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.104/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 329sec preferred_lft 329sec
    inet6 fe80::4507:515e:2743:6807/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```

🌞 Sur mon ordinateur :

```
PS C:\Windows\system32> Get-NetIPAddress -InterfaceAlias "Ethernet 2"


IPAddress         : fe80::dc0b:6d00:87b5:149d%19
InterfaceIndex    : 19
InterfaceAlias    : Ethernet 2
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 192.168.56.1
InterfaceIndex    : 19
InterfaceAlias    : Ethernet 2
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore
```


🌞 **Tester que votre LAN + votre adressage IP est fonctionnel** 🌞

🌞 Sur ma VM vers mon Ordinateur :


```
johann@johann-ubuntu:~$ ping 10.33.76.43
PING 10.33.76.43 (10.33.76.43) 56(84) bytes of data.
64 bytes from 10.33.76.43: icmp_seq=1 ttl=127 time=53.3 ms
64 bytes from 10.33.76.43: icmp_seq=2 ttl=127 time=1.29 ms
64 bytes from 10.33.76.43: icmp_seq=3 ttl=127 time=2.29 ms
64 bytes from 10.33.76.43: icmp_seq=4 ttl=127 time=4.17 ms
64 bytes from 10.33.76.43: icmp_seq=5 ttl=127 time=3.31 ms
64 bytes from 10.33.76.43: icmp_seq=6 ttl=127 time=1.18 ms
64 bytes from 10.33.76.43: icmp_seq=7 ttl=127 time=3.03 ms
^C
--- 10.33.76.43 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6019ms
rtt min/avg/max/mdev = 1.178/9.797/53.325/17.798 ms
```

🌞 Sur mon Ordinateur vers ma VM :

🌞
```
PS C:\Windows\system32> ping 192.168.56.104

Envoi d’une requête 'Ping'  192.168.56.104 avec 32 octets de données :
Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps=1 ms TTL=64
Réponse de 192.168.56.104 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.56.104:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0
```



🌞**Capture de `ping`** 🌞

🌞 A trouver en PJ.

# II. Utilisation des ports

## 0. Intro blabla


## 1. Animal numérique

🌞 **Sur le PC serveur** 🌞

🌞
Ma commande en tans que VM comme PC serveur.

```
johann@johann-ubuntu:~$ nc -l 2525
```

🌞 **Sur le PC serveur toujours** 🌞

🌞
```
johann@johann-ubuntu:~$ nc -l 2525
sudo ss -lnpt
```

🌞 **Sur le PC client** 🌞

````
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> .\nc.exe  192.168.56.104 2525
````

🌞 **Echangez-vous des messages** 🌞

🌞
De mon post client :

```
dfghjk
sudo ss -lnpt
yo
bonjour toi de la où tu es
```

🌞
De mon post Serveur :

```
sudo ss -lnpt
dfghjk
yo
bonjour toi de la o� tu es

```

🌞 **Utilisez une commande qui permet de voir la connexion en cours** 🌞

🌞
Sur le serveur :

```
johann@johann-ubuntu:~$ sudo ss -lnpt
State     Recv-Q    Send-Q       Local Address:Port        Peer Address:Port    Process                                                                         
LISTEN    0         1                  0.0.0.0:2525             0.0.0.0:* 
```

🌞
Sur le client :

```
PS C:\Windows\system32> netstat -a -b -n
[...]
 [nc.exe]
  TCP    [::]:135               [::]:0                 LISTENING
  RpcSs

```


🌞 **Faites une capture Wireshark complète d'un échange** 🌞

Voir en PJ.


# III. Analyse de vos applications usuelles

## 1. Serveur web

➜ **Connectez-vous à un site en HTTP**

🌞
J'ai trouver ce site :
```
http://w3.uqo.ca/iglewski/ens/inf1493/src/html2/html2_http.php
```


🌞 **Utilisez Wireshark pour capturer du trafic HTTP** 🌞

🌞
Voir PJ.



## 2. Autres services

🌞 **Pour les 5 applications** 🌞

Première application, Spotify :
🌞
```
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> netstat -a -b -n | Select-String Spoti -Context 1,0

    TCP    10.33.76.43:56012      34.120.195.249:443     SYN_SENT
>  [Spotify.exe]
```

Deuxième application, Skype :
🌞
```
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> netstat -a -b -n | Select-String Skype -Context 1,0

    TCP    10.33.76.43:56066      13.107.42.16:443       SYN_SENT
>  [Skype.exe]
```

Troisième application, Google Chrome :
🌞
```
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> netstat -a -b -n | Select-String Chr -Context 1,0

    TCP    10.33.76.43:47473      54.170.12.237:443      SYN_SENT
>  [chrome.exe]
```


Quatrième application, Discord :
🌞
```
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> netstat -a -b -n | Select-String Disco -Context 1,0

    TCP    10.33.76.43:56248      162.159.138.232:443    SYN_SENT
>  [Discord.exe]
```

Cinquième application, Edge :
🌞
```
PS C:\Users\chiar\Downloads\netcat-win32-1.11\netcat-1.11> netstat -a -b -n | Select-String Edge -Context 1,0

    TCP    10.33.76.43:32577      20.56.187.20:443       SYN_SENT
>  [msedge.exe]
```