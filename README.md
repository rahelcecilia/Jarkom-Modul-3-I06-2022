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

## Number 3
Client that go through Switch1 have the IP range from [prefix IP].1.50 - [prefix IP].1.88 and [prefix IP].1.120 - [prefix IP].1.155

## Number 4
Client that go through Switch3 have the IP range from [prefix IP].3.10 - [prefix IP].3.30 dan [prefix IP].3.60 - [prefix IP].3.85

## Number 5
Client gets the DNS from WISE and client can connect to the internet through the DNS. 

## Number 6
The length of time the DHCP server lends an IP address to client via Switch1 is 5 minutes, while the client via Switch3 is 10 minutes. With a maximum time allocated for borrowing an IP address is 115 minutes.

## IP Result from DHCP
![hasil SSS](https://user-images.githubusercontent.com/73649094/201453684-211a8419-0041-44a8-bbbd-41d356997bf8.jpg)
![hasil garden](https://user-images.githubusercontent.com/73649094/201453687-91d635ad-8a41-4a82-aecf-aa2296732367.jpg)
![hasil newstoncastle](https://user-images.githubusercontent.com/73649094/201453693-5a9e742b-44e9-489b-9c23-f8ad3c797c00.jpg)
![hasil kemonopark](https://user-images.githubusercontent.com/73649094/201453698-a059c7a2-e5f9-478a-b90f-98787f3dff04.jpg)


## Number 7
Eden as a server for exchanging information with a fixed IP address with IP [prefix IP].3.13

hwaddress on Eden :

![hwaddress](https://user-images.githubusercontent.com/73649094/201453640-9f5001b7-abde-46f7-8967-bcfb60408c9c.jpg)


Result : 

![hasil fixed address](https://user-images.githubusercontent.com/73649094/201453600-46b66fa0-3954-49ef-81b9-f5f846e2a5bb.jpg)


## Number 8


