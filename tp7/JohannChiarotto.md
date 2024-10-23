# TP7 : On dit chiffrer pas crypter



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

[ici](tcp_http.pcap)


🌞 **Voir la connexion établie**




## 2. On rajoute un S

### A. Config


🌞 **Lister les ports en écoute sur la machine**

````
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









# III. Serveur VPN



🌞 **Prouvez que vous avez bien une nouvelle carte réseau `wg0`**




🌞 **Déterminer sur quel port écoute Wireguard**



🌞 **Ouvrez ce port dans le firewall**




## 2. Ajout d'un client VPN


## 3. Proofs

🌞 **Ping ping ping !**



🌞 **Capture `ping1_vpn.pcap`**




🌞 **Prouvez que vous avez toujours un accès internet**



## 4. Private service



🌞 **Visitez le service Web à travers le VPN**



