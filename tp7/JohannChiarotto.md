# TP7 : On dit chiffrer pas crypter


#
# II. Serveur Web



🌞 **Lister les ports en écoute sur la machine**

```
[johann@web ~]$ sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=11281,fd=6),("nginx",pid=11280,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=11281,fd=7),("nginx",pid=11280,fd=7))
```

🌞 **Ouvrir le port dans le firewall de la machine**

```
[johann@web ~]$ sudo firewall-cmd --permanent --remove-port=80/tcp
Warning: NOT_ENABLED: 80:tcp
success
```
#
### A. Install
### B. Configuration
### C. Tests client


🌞 **Vérifier que ça a pris effet**

- faites un ping vers sitedefou.tp7.b1
    ```
    [johann@client1 ~]$ sudo nano /etc/hosts
    [sudo] password for johann:
    [johann@client1 ~]$ ping sitedefou.tp7.b1
    PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=3.53 ms
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=1.13 ms
    64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=1.89 ms
    ^C
    --- sitedefou.tp7.b1 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2005ms
    rtt min/avg/max/mdev = 1.128/2.181/3.525/0.999 ms
    ```

- visitez http://sitedefou.tp7.b1
    ```
    [johann@client1 ~]$ curl http://sitedefou.tp7.b1
    meow !
    ```

### D. Analyze


🌞 **Capture `tcp_http.pcap`**

[HTTP](tcp_http.pcap)




## 2. On rajoute un S

### A. Config


🌞 **Lister les ports en écoute sur la machine**

```
[johann@web ~]$ sudo ss -lnpt | grep 443
LISTEN 0      511        10.7.1.11:443       0.0.0.0:*    users:(("nginx",pid=1299,fd=6),("nginx",pid=1298,fd=6))
```

🌞 **Gérer le firewall**

```
[johann@web ~]$ sudo firewall-cmd --permanent --add-port=443/tcp
Warning: ALREADY_ENABLED: 443:tcp
success
```


### B. Test test test analyyyze


🌞 **Capture `tcp_https.pcap`**

[HTTPS](tcp_https.pcap)





#
# III. Serveur VPN



🌞 **Prouvez que vous avez bien une nouvelle carte réseau `wg0`**

```
[johann@vpn ~]$ ip a
[...]
4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```


🌞 **Déterminer sur quel port écoute Wireguard**

```
[johann@vpn ~]$ sudo ss -lnpu | grep 51820
UNCONN 0      0            0.0.0.0:51820      0.0.0.0:*
UNCONN 0      0               [::]:51820         [::]:*
```


🌞 **Ouvrez ce port dans le firewall**

```
[johann@vpn ~]$ sudo firewall-cmd --permanent --add-port=51820/udp
Warning: ALREADY_ENABLED: 51820:udp
success
```


## 2. Ajout d'un client VPN


## 3. Proofs

🌞 **Ping ping ping !**


```
[johann@client1 ~]$ ping 10.7.200.1
PING 10.7.200.1 (10.7.200.1) 56(84) bytes of data.
64 bytes from 10.7.200.1: icmp_seq=1 ttl=64 time=2.39 ms
64 bytes from 10.7.200.1: icmp_seq=2 ttl=64 time=27.2 ms
64 bytes from 10.7.200.1: icmp_seq=3 ttl=64 time=1.48 ms
^C
--- 10.7.200.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 1.475/10.354/27.203/11.919 ms
```


🌞 **Capture `ping1_vpn.pcap`**

[ping1](ping1_vpn.pcap)



🌞 **Capture `ping2_vpn.pcap`**

[ping2](ping2_vpn.pcap)


🌞 **Prouvez que vous avez toujours un accès internet**

```
[johann@client1 ~]$ traceroute 1.1.1.1
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  _gateway (10.7.200.1)  3.235 ms  8.024 ms  6.952 ms
 2  * * *
 3  10.0.2.2 (10.0.2.2)  19.050 ms  20.754 ms  20.743 ms
 4  * * *
 ```


## 4. Private service


🌞 **Visitez le service Web à travers le VPN**


```
[johann@client1 ~]$ curl -k https://sitedefou.tp7.b1
meow !
```
