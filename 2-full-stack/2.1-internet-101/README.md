# 2.1: Internet 101

## Learning Objectives

1. The internet is wires that connect computers
2. The internet uses protocols such as HTTP to transmit data reliably
3. DNS translates human-readable URLs to IP addresses that identify computers on the network

## Introduction

![Global map of submarine internet cables. Source: Ars Technica](<../../.gitbook/assets/2.1 - World Submarine Cable Map.png>)

The internet consists of computers, wires and software that sends data between computers through wires.

Internet pioneers developed software protocols that allow us to transmit arbitrary data across the internet reliably. [Internet governing bodies](https://www.ietf.org) are continuously upgrading these protocols.

As app developers we do not need to understand these protocols in depth; this page runs through the most important aspects of internet protocols we need to know to build apps effectively.

## HTTP

[HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) (Hypertext Transfer Protocol) is the most common internet data-transfer protocol. We will use it to send data between our app frontends and backends, as well as between our apps and any 3rd-party [API](https://www.mulesoft.com/resources/api/what-is-an-api#:\~:text=API%20is%20the%20acronym%20for,you're%20using%20an%20API.) (Application Programming Interface) services to store or retrieve data.

HTTP consists of "requests" and "responses". Frontends (e.g. browsers, mobile apps, aka "clients") typically send "requests" to backends (aka "servers") to create, retrieve, update or delete data from a database. Backends send back "responses" with confirmations and relevant data.

## Internet Addressing

### URLs

URLs (Uniform Resource Locators) are internet addresses. We will send HTTP requests with URLs to retrieve our frontends and communicate with our backends and 3rd-party APIs.

![A URL consists of these key components. Source: Rocket Academy](<../../.gitbook/assets/2.1 - URL.jpg>)

TODO: Ports

On a given computer, many programs can be sending and receiving data across the Internet simultaneously, such as WhatsApp, Spotify, Windows Updates, Mac Updates, etc. When each computer only has 1 IP address, how does the operating system determine which data is for which application?

TCP/IP uses **ports** to determine which application receives which data. [Here](https://en.wikipedia.org/wiki/List\_of\_TCP\_and\_UDP\_port\_numbers) is a comprehensive list. Occasionally multiple applications will use the same port, in which case we may need to close the others for any to work. This is rare for popular applications.

Ports are typically displayed as a number after IP addresses followed by a colon (`:`). We can use the following command to see all processes listening on specific ports on our computers.

```
lsof -i -P -n | grep LISTEN
```

When building apps, the servers that we host on the Internet to manage data will use ports to "listen" for requests from clients (e.g. browsers or apps). These requests will be like "commands" that tell our servers how to handle data. The port number in a destination address helps the server computer decide which server application to send the request to. For example, in the diagram above where there are 2 Node.js server applications running on the computer, the port numbers 3004 and 80 help the server computer decide which Node app to send the request to.

### IP Addresses

URLs map to IP (Internet Protocol) addresses that identify individual or networks of computers on the internet. IP addresses are network-based, not computer-based, so if we connect our computer to a different network it will have a different IP address.

IP addresses typically consist of 4 numbers from 0-255 separated by `.`, for example `192.158.1.38`. These are known as "[IPv4](https://en.wikipedia.org/wiki/IPv4)" addresses and route most internet traffic today. The world is running out of IPv4 addresses and plans to transition to "[IPv6](https://en.wikipedia.org/wiki/IPv6\_address)" in the coming decades.

### DNS

[DNS](https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/) (Domain Name System) translates domain names in URLs to IP addresses so our requests can reach the right servers. It's helpful to have domain names decoupled from IP addresses so we can change servers without changing domain names.&#x20;

When we rent or buy a domain name and want to host our website or server there, we will need to add 1 or more "DNS records" to our domain to let DNS know where to find the server for our domain.

## LAN vs. WAN

Our computers typically connect to the Internet via a router provided by our ISP (Internet Service Provider). All computers connected to the same router are typically connected via LAN (Local Area Network). The router forwards traffic from the LAN to the WAN (Wide Area Network), i.e. the broader Internet. This helps prevents unwanted traffic from accessing our computers, and aggregate Internet connections for simplicity of the Internet.

![Our routers forward requests to the ISP, which is directly connected to the internet.](../.gitbook/assets/wan-lan.jpg)

### LAN and WAN IP Addresses

Computers typically have a LAN IP address, and routers typically have a WAN IP address. The LAN IP address is used by routers to send responses from the Internet to the correct computers in the LAN. The WAN IP address is shared by computers connected to our router, and is how computers on the Internet identify us.

`ifconfig` (interface configuration) is a command line program that reveals the LAN IP address of our computer. If on Windows and running Ubuntu, we will need to [install `ifconfig`](http://geekstuff.org/2018/06/09/ifconfig-missing-in-ubuntu-18-04/#:\~:text=You%20may%20install%20ifconfig%20utility,information%20about%20your%20network%20configuration.) with `sudo apt install net-tools` before running it. `en0` is typically the interface with our current LAN IP address.

![Akira's computer has LAN IP address 192.168.0.195. Not accessible on Internet because LAN.](../.gitbook/assets/screen-shot-2020-11-02-at-9.13.00-pm.png)

We can visit [https://whatismyipaddress.com/](https://whatismyipaddress.com) to verify what our current WAN IP address is. When we visit websites, those sites have access to the source of our requests, i.e. our WAN address, but not our LAN address.

Notice LAN and WAN IP addresses are different. This is to protect our privacy and to streamline the Internet.

## Other Common Networking Tools

### Ping

[Ping](https://linux.die.net/man/8/ping) is a networking utility used to test if a computer is reachable on the network. It does not use a port because it is not trying to reach an application inside the computer, only that computer's networking software. Different domains may take a different amounts of time to respond, depending on how far away the servers are.

```
ping google.com
```

### Traceroute

[Traceroute](https://en.wikipedia.org/wiki/Traceroute) reveals the servers our TCP/IP packets travel through on the way to their destination.

```
traceroute google.com
```

There are several [Visual Traceroute](https://gsuite.tools/traceroute) utilities online to see these paths on a map. They may originate in Europe because the visual traceroute servers are in Europe.

## Exercise

Try `ping` and `traceroute` on the following domains. How long do each of the requests take and where do they travel through?

1. ntu.edu.sg
2. genting.com
3. tigerbeer.com.sg
4. stanford.edu
5. nus.edu.sg
6. in-n-out.com
7. musee-orsay.fr
8. rwandatel.rw

## Further Reading

### Other Protocols

1. [DHCP](https://en.wikipedia.org/wiki/Dynamic\_Host\_Configuration\_Protocol) configures our computers when they connect to routers.
2. [SMTP](https://en.wikipedia.org/wiki/Simple\_Mail\_Transfer\_Protocol#:\~:text=The%20Simple%20Mail%20Transfer%20Protocol,send%20and%20receive%20mail%20messages.) is a default protocol for email.

There have been many protocols that are now obsolete. [QOTD](https://en.wikipedia.org/wiki/QOTD) was a protocol to get a quote of the day.

## Additional Resources

1. See Stanford's [Intro to Networking course CS144](http://cs144.stanford.edu) for further reading on these topics. [Here](https://www.youtube.com/playlist?list=PLEAYkSg4uSQ2dr0XO\_Nwa5OcdEcaaELSG) is a playlist of past CS144 videos that past Coding Bootcamp students have found helpful.
2. Past students have found [this video](https://www.youtube.com/watch?v=RDotMcs0Erg) helpful in introducing ports and how they are used.
3. Past students have found [this video](https://youtu.be/AEaKrq3SpW8) helpful as a crash course to the Internet.
