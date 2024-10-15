# TP5 : Un ptit LAN à nous

# 0. Prérequis

☀️ **Uniquement avec des commandes, prouvez-que :**
- vous avez bien configuré les adresses IP demandées 
    
    routeur :
    ```
    johann@client1:~$ ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host noprefixroute
        valid_lft forever preferred_lft forever
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:8e:eb:54 brd ff:ff:ff:ff:ff:ff
        inet ☀️10.5.1.11/24 brd 10.5.1.255 scope global noprefixroute enp0s3
        valid_lft forever preferred_lft forever
        inet6 fe80::e99c:3cea:b09e:696/64 scope link noprefixroute
        valid_lft forever preferred_lft forever    
    ```

    client 1 :
    ```
    johann@client2:~$ ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host noprefixroute
        valid_lft forever preferred_lft forever
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:6e:89:95 brd ff:ff:ff:ff:ff:ff
        inet ☀️10.5.1.12/24 brd 10.5.1.255 scope global noprefixroute enp0s3
        valid_lft forever preferred_lft forever
        inet6 fe80::7193:6c7a:5550:6580/64 scope link noprefixroute
        valid_lft forever preferred_lft forever    
    ```

    client 2 :
    ```
    [johann@routeur ~]$ ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:f7:15:54 brd ff:ff:ff:ff:ff:ff
        inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute enp0s3
        valid_lft 86217sec preferred_lft 86217sec
        inet6 fe80::a00:27ff:fef7:1554/64 scope link noprefixroute
        valid_lft forever preferred_lft forever
    3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:dc:59:bf brd ff:ff:ff:ff:ff:ff
        inet ☀️10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s8
        valid_lft forever preferred_lft forever
        inet6 fe80::a00:27ff:fedc:59bf/64 scope link
        valid_lft forever preferred_lft forever
    ```


- vous avez bien configuré les hostnames demandés

    routeur :

    ```
    [johann@routeur ~]$ hostnamectl
    Static hostname: routeur.tp5.b1 ☀️
        Icon name: computer-vm
            Chassis: vm 🖴
        Machine ID: e4c0ae4d4739401cbf8ec7b46517be53
            Boot ID: 1361a8e4e042420b9645806015950d1b
    Virtualization: oracle
    Operating System: Rocky Linux 9.4 (Blue Onyx)
        CPE OS Name: cpe:/o:rocky:rocky:9::baseos
            Kernel: Linux 5.14.0-427.13.1.el9_4.x86_64
        Architecture: x86-64
    Hardware Vendor: innotek GmbH
    Hardware Model: VirtualBox
    Firmware Version: VirtualBox
    ```

    client 1

    ```
    johann@client1:~$ hostnamectl
    Static hostname: client1.tp5.b1 ☀️
        Icon name: computer-vm
            Chassis: vm 🖴
        Machine ID: f5229d623472423c8886fb357b939b90
            Boot ID: efa3144268584b5caa3f7c68ca7dc921
    Virtualization: oracle
    Operating System: Ubuntu 24.04.1 LTS
            Kernel: Linux 6.8.0-45-generic
        Architecture: x86-64
    Hardware Vendor: innotek GmbH
    Hardware Model: VirtualBox
    Firmware Version: VirtualBox
    Firmware Date: Fri 2006-12-01
        Firmware Age: 17y 10month 2w    
    ```

    client 2
    ```
    johann@client2:~$ hostnamectl
    Static hostname: client2.tp5.b1 ☀️
        Icon name: computer-vm
            Chassis: vm 🖴
        Machine ID: f5229d623472423c8886fb357b939b90
            Boot ID: eed08cdfb8ac417ba14403642b7d40e9
    Virtualization: oracle
    Operating System: Ubuntu 24.04.1 LTS
            Kernel: Linux 6.8.0-45-generic
        Architecture: x86-64
    Hardware Vendor: innotek GmbH
    Hardware Model: VirtualBox
    Firmware Version: VirtualBox
    Firmware Date: Fri 2006-12-01
        Firmware Age: 17y 10month 2w
    ```




- tout le monde peut se ping au sein du réseau 

    ☀️ Routeur vers client 1:

    ```
    [johann@routeur ~]$ ping 10.5.1.11
    PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
    64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=1.41 ms
    64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=1.91 ms
    64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=2.75 ms
    ^C
    --- 10.5.1.11 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2006ms
    rtt min/avg/max/mdev = 1.408/2.023/2.752/0.554 ms
    ```

    ☀️ Routeur vers client 2:

    ```
    [johann@routeur ~]$ ping 10.5.1.12
    PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
    64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=1.14 ms
    64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=2.71 ms
    64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=2.17 ms
    ^C
    --- 10.5.1.12 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2004ms
    rtt min/avg/max/mdev = 1.143/2.008/2.712/0.650 ms
    ```

    ☀️ Client 1 vers client 2:

    ```
    johann@client1:~$ ping 10.5.1.12
    PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
    64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=5.31 ms
    64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=1.31 ms
    64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=1.21 ms
    ^C
    --- 10.5.1.12 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2012ms
    rtt min/avg/max/mdev = 1.214/2.613/5.313/1.909 ms
    ```

    ☀️ Client 1 vers routeur:

    ```
    johann@client1:~$ ping 10.5.1.254
    PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
    64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=2.80 ms
    64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=2.16 ms
    64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=2.38 ms
    64 bytes from 10.5.1.254: icmp_seq=4 ttl=64 time=1.68 ms
    ^C
    --- 10.5.1.254 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3012ms
    rtt min/avg/max/mdev = 1.676/2.252/2.795/0.403 ms
    ```

    ☀️ Client 2 vers client 1:

    ```
    johann@client2:~$ ping 10.5.1.11
    PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
    64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=3.70 ms
    64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=0.864 ms
    64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=1.30 ms
    ^C
    --- 10.5.1.11 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2004ms
    rtt min/avg/max/mdev = 0.864/1.953/3.699/1.247 ms
    ```

    ☀️ Client 2 vers routeur:

    ```
    johann@client2:~$ ping 10.5.1.254
    PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
    64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=4.63 ms
    64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=3.53 ms
    64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=2.02 ms
    ^C
    --- 10.5.1.254 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2003ms
    rtt min/avg/max/mdev = 2.015/3.389/4.625/1.069 ms
    ```



# II. Accès internet pour tous

## 1. Accès internet routeur

☀️ **Déjà, prouvez que le routeur a un accès internet**

```
[johann@routeur ~]$ ping www.ynov.com
PING www.ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=47 time=87.2 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=2 ttl=47 time=121 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=3 ttl=47 time=66.6 ms
^C
--- www.ynov.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 66.624/91.653/121.142/22.479 ms
```





☀️ **Activez le routage**

```
[johann@routeur ~]$ sudo firewall-cmd --add-masquerade --permanent
success
[johann@routeur ~]$ sudo firewall-cmd --reload
success
```





## 2. Accès internet clients


☀️ **Prouvez que les clients ont un accès internet**

- Client 1 :
    ```
    johann@client1:~$ ping www.ynov.com
    PING www.ynov.com (104.26.11.233) 56(84) bytes of data.
    64 bytes from 104.26.11.233: icmp_seq=1 ttl=46 time=158 ms
    64 bytes from 104.26.11.233: icmp_seq=2 ttl=46 time=131 ms
    64 bytes from 104.26.11.233: icmp_seq=3 ttl=46 time=137 ms
    64 bytes from 104.26.11.233: icmp_seq=4 ttl=46 time=194 ms
    ^C
    --- www.ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3008ms
    rtt min/avg/max/mdev = 131.157/154.971/193.614/24.459 ms
    ```

- client 2 :

    ```
    johann@client2:~$ ping www.ynov.com
    PING www.ynov.com (104.26.11.233) 56(84) bytes of data.
    64 bytes from 104.26.11.233: icmp_seq=1 ttl=46 time=186 ms
    64 bytes from 104.26.11.233: icmp_seq=2 ttl=46 time=144 ms
    64 bytes from 104.26.11.233: icmp_seq=3 ttl=46 time=71.6 ms
    64 bytes from 104.26.11.233: icmp_seq=4 ttl=46 time=100 ms
    ^C
    --- www.ynov.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3001ms
    rtt min/avg/max/mdev = 71.580/125.374/185.780/43.313 ms
    ```


☀️ **Montrez-moi le contenu final du fichier de configuration de l'interface réseau**

```
johann@client1:/etc/netplan$ sudo cat ifcfg-enp0s8
network:
  version: 2
  ethernets:
    NM-c2d17356-c678-46ae-b2ec-1a8613e396c0:
      renderer: NetworkManager
      match:
        name: "enp0s3"
      addresses:
      - "10.5.1.11/24"
      nameservers:
        addresses:
        - 1.1.1.1
      dhcp6: true
      wakeonlan: true
      networkmanager:
        uuid: "c2d17356-c678-46ae-b2ec-1a8613e396c0"
        name: "Profile 1"
        passthrough:
          ethernet._: ""
          ipv4.address1: "10.5.1.11/24,10.5.1.254"
          ipv4.method: "manual"
          ipv6.addr-gen-mode: "default"
          ipv6.ip6-privacy: "-1"
          proxy._: ""
```



# III. Serveur SSH


☀️ **Sur `routeur.tp5.b1`, déterminer sur quel port écoute le serveur SSH**

```
[johann@routeur ~]$ sudo ss -lnpt | grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=701,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=701,fd=4))
```




☀️ **Sur `routeur.tp5.b1`, vérifier que ce port est bien ouvert**

```
[johann@routeur ~]$ sudo ss -npt
State                Recv-Q                Send-Q                                Local Address:Port                                 Peer Address:Port                 Process
ESTAB                0                     52                                       10.5.1.254:22                                       10.5.1.1:10221                 users:(("sshd",pid=1331,fd=4),("sshd",pid=1327,fd=4))
```







# IV. Serveur DHCP

## 1. Le but

## 2. Comment le faire

## 3. Rendu attendu

### A. Installation et configuration du serveur DHCP

☀️ **Installez et configurez un serveur DHCP sur la machine `routeur.tp5.b1`**


Pour installer :

```
sudo dnf install dhcp-server -y
````
- `sudo cd /etc/dhcp`
- `sudo nano dhcp.conf`
- 
    ```
    GNU nano 5.6.1                                                                             dhcp.conf                                                                                       default-lease-time 2592000;

    max-lease-time 3888000;

    authoritative;

    subnet 10.5.1.0 netmask 255.255.255.0 {

        range dynamic-bootp 10.5.1.137 10.5.1.237;

        option routers 10.5.1.254;

        option subnet-mask 255.255.255.0;

        option domain-name-servers 1.1.1.1;

    }
    ```
- `sudo firewall-cmd --reload`
- `sudo systemctl enable --now dhcpd`



### B. Test avec un nouveau client

☀️ **Créez une nouvelle machine client `client3.tp5.b1`**

Verification de la bonne plage pour l'adresse IP :
```
johann@client3:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:01:3f:1b brd ff:ff:ff:ff:ff:ff
    inet ☀️10.5.1.137/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 309sec preferred_lft 309sec
```


Verification de l'accèa  internet avec un ping sur un site internet.

```
johann@client3:~$ ping www.ynov.com
PING www.ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233: icmp_seq=1 ttl=46 time=125 ms
64 bytes from 104.26.10.233: icmp_seq=2 ttl=46 time=334 ms
64 bytes from 104.26.10.233: icmp_seq=3 ttl=46 time=169 ms
64 bytes from 104.26.10.233: icmp_seq=4 ttl=46 time=187 ms
64 bytes from 104.26.10.233: icmp_seq=5 ttl=46 time=208 ms
^C
--- www.ynov.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4010ms
rtt min/avg/max/mdev = 124.777/204.377/334.277/70.444 ms
```





### C. Consulter le bail DHCP


☀️ **Consultez le *bail DHCP* qui a été créé pour notre client**

```
[johann@routeur dhcpd]$ cat dhcpd.leases~
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.4.2b1

# authoring-byte-order entry is generated, DO NOT DELETE
authoring-byte-order little-endian;

server-duid "\000\001\000\001.\241?\250\010\000'\334Y\277";

lease 10.5.1.137 {
  starts 2 2024/10/15 15:30:25;
  ends 2 2024/10/15 15:40:25;
  cltt 2 2024/10/15 15:30:25;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
  client-hostname "client1";
}
lease 10.5.1.137 {
  starts 2 2024/10/15 15:35:24;
  ends 2 2024/10/15 15:45:24;
  cltt 2 2024/10/15 15:35:24;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
  client-hostname "client1";
}
lease 10.5.1.137 {
  starts 2 2024/10/15 15:40:44;
  ends 2 2024/10/15 15:50:44;
  cltt 2 2024/10/15 15:40:44;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
  client-hostname "client1";
}
lease 10.5.1.137 {
  starts 2 2024/10/15 15:45:44;
  ends 2 2024/10/15 15:55:44;
  cltt 2 2024/10/15 15:45:44;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
  client-hostname "client1";
}
lease 10.5.1.137 {
  starts 2 2024/10/15 15:50:44;
  ends 2 2024/10/15 16:00:44;
  cltt 2 2024/10/15 15:50:44;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
  client-hostname "client1";
}
lease 10.5.1.137 {
  starts 2 2024/10/15 15:50:44;
  ends 2 2024/10/15 16:00:44;
  tstp 2 2024/10/15 16:00:44;
  cltt 2 2024/10/15 15:50:44;
  binding state free;
  hardware ethernet 08:00:27:01:3f:1b;
  uid "\001\010\000'\001?\033";
}
```

☀️ **Confirmez qu'il s'agit bien de la bonne adresse MAC**


```
johann@client3:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ☀️08:00:27:01:3f:1b brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.137/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 487sec preferred_lft 487sec
```