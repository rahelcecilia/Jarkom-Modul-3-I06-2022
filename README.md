# Jarkom-Modul-3-I06-2022
<strong> Our Members :
1. Muhammad Naufal Alif - 05111942000008
2. Denta Bramasta Hidayat - 5025201116
3. Rahel Cecilia Purba - 5025201155 </strong>

## MODUL 3

![image](https://user-images.githubusercontent.com/112471006/200609868-cd195895-08a0-4a88-a5a5-27ec329c4940.png)


## Number 1
create the map above with criteria WISE as DNS Server, Westalis as DHCP Server, Berlint as Proxy Server.

```bash
# WISE - DNS Server
apt-get update
apt-get install bind9 -y
service bind9 restart

# Berlint - Proxy Server
apt-get update
apt-get install squid -y
service squid start

# Westalis - DHCP Server
apt-get update
apt-get install isc-dhcp-server -y
service isc-dhcp-server start

	# Westalis => /etc/default/isc-dhcp-server
```
Result:

![](https://i.ibb.co/80LKSn0/Screenshot-2022-11-12-at-11-27-03.png)

## Number 2
Create Ostania as DHCP Relay.

```bash
# Ostania - DHCP Relay
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
# Ostania => /etc/default/isc-dhcp-relay
```

Result:

![](https://i.ibb.co/Hgqt73p/Screenshot-2022-11-12-at-11-29-35.png)

All existing clients MUST use the IP configuration from the DHCP Server.

```bash
# SSS, Garden, Eden, NewtonCastle, KemonoPark => network configuration
	auto eth0
iface eth0 inet dhcp
```

## Number 3
Client that go through Switch1 have the IP range from 10.39.1.50 - 10.39.1.88 and 10.39.1.120 - 10.39.1.155

```bash
# Westalis => /etc/dhcp/dhcpd.conf
subnet 10.39.1.0 netmask 255.255.255.0 {
    range 10.39.1.50 10.39.1.88;
    range 10.39.1.120 10.39.1.155;
    ...
}
```

## Number 4
Client that go through Switch3 have the IP range from 10.39.3.10 - 10.39.3.30 dan 10.39.3.60 - 10.39.3.85

```bash
# Westalis => /etc/dhcp/dhcpd.conf
subnet 10.39.3.0 netmask 255.255.255.0 {
    range 10.39.3.10 10.39.3.30;
    range 10.39.3.60 10.39.3.85;
    ...
}
```

## Number 5
Client gets the DNS from WISE and client can connect to the internet through the DNS. 

```bash 
# Westalis => /etc/dhcp/dhcpd.conf
subnet 10.39.1.0 netmask 255.255.255.0 {
    ...
    option domain-name-servers 10.39.2.2;
    ...
}
subnet 10.39.3.0 netmask 255.255.255.0 {
    ...
    option domain-name-servers 10.39.2.2;
    ...
}
```

## Number 6
The length of time the DHCP server lends an IP address to client via Switch1 is 5 minutes, while the client via Switch3 is 10 minutes. With a maximum time allocated for borrowing an IP address is 115 minutes.

```bash
# Westalis => /etc/dhcp/dhcpd.conf
subnet 10.39.1.0 netmask 255.255.255.0 {
    ???
    default-lease-time 300;
    max-lease-time 6900;
}

subnet 10.39.3.0 netmask 255.255.255.0 {
    ...
    default-lease-time 600;
    max-lease-time 6900;

}
```

## IP Result from DHCP
![hasil SSS](https://user-images.githubusercontent.com/73649094/201453684-211a8419-0041-44a8-bbbd-41d356997bf8.jpg)
![hasil garden](https://user-images.githubusercontent.com/73649094/201453687-91d635ad-8a41-4a82-aecf-aa2296732367.jpg)
![hasil newstoncastle](https://user-images.githubusercontent.com/73649094/201453693-5a9e742b-44e9-489b-9c23-f8ad3c797c00.jpg)
![hasil kemonopark](https://user-images.githubusercontent.com/73649094/201453698-a059c7a2-e5f9-478a-b90f-98787f3dff04.jpg)


## Number 7
Eden as a server for exchanging information with a fixed IP address with IP 10.39.3.13

hwaddress on Eden :

![hwaddress](https://user-images.githubusercontent.com/73649094/201453640-9f5001b7-abde-46f7-8967-bcfb60408c9c.jpg)

```bash
# Westalis => /etc/dhcp/dhcpd.conf
host Eden {
    hardware ethernet 32:0d:7a:0d:8c:93;
    fixed-address 10.39.3.13;
}

# Eden => network configuration
auto eth0
iface eth0 inet dhcp
hwaddress ether 32:0d:7a:0d:8c:93
```

Result : 

![hasil fixed address](https://user-images.githubusercontent.com/73649094/201453600-46b66fa0-3954-49ef-81b9-f5f846e2a5bb.jpg)
