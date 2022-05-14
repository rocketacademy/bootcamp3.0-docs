# 2.1: Internet 101

## Learning Objectives

1. The internet is wires that connect computers
2. The internet uses protocols such as HTTP to transmit data reliably
3. DNS translates human-readable URLs to IP addresses that identify computers on the network

## Introduction

![Global map of submarine internet cables. Source: Ars Technica](<../../.gitbook/assets/2.1 - World Submarine Cable Map.png>)

The internet consists of computers, wires and software that sends data between computers through wires.

Internet pioneers developed software protocols that allow us to transmit data across the internet reliably. [Internet governing bodies](https://www.ietf.org/) are continuously upgrading these protocols.

As app developers we do not need to understand these protocols in depth. This page runs through the most important aspects of internet protocols we need to build apps effectively.

## HTTP

[HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) (Hypertext Transfer Protocol) is the most common internet data-transfer protocol. We will use it to send data between our app frontends and backends, as well as between our apps and any 3rd-party [API](https://www.mulesoft.com/resources/api/what-is-an-api) (Application Programming Interface) services to store or retrieve data.

HTTP consists of "requests" and "responses". Frontends (e.g. browsers, mobile apps, aka "clients") typically send "requests" to backends (aka "servers") to create, retrieve, update or delete data from a database. Backends send back "responses" with confirmations and relevant data.

## Internet Addressing

### URLs

URLs (Uniform Resource Locators) are internet addresses. We will send HTTP requests with URLs to retrieve our frontends and communicate with our backends and 3rd-party APIs.

![A URL consists of these key components. Source: Rocket Academy](<../../.gitbook/assets/2.1 - URL.jpg>)

We use ports to identify requests and responses to different applications on the same computer. We can omit ports in URLs when our applications use default ports (e.g. 443 for HTTPS requests, 80 for HTTP).

### IP Addresses

URLs map to IP (Internet Protocol) addresses that identify individual or networks of computers on the internet. IP addresses are network-based, not computer-based, so if we connect our computer to a different network it will have a different IP address.

IP addresses typically consist of 4 numbers from 0-255 separated by `.`, for example `192.158.1.38`. These are known as "[IPv4](https://en.wikipedia.org/wiki/IPv4)" addresses and route most internet traffic today. The world is running out of IPv4 addresses and plans to transition to "[IPv6](https://en.wikipedia.org/wiki/IPv6\_address)" in the coming decades.

### DNS

[DNS](https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/) (Domain Name System) translates domain names in URLs to IP addresses so our requests can reach the right servers. It's helpful to have domain names decoupled from IP addresses so we can change servers without changing domain names.&#x20;

When we rent or buy a domain name and want to host our website or server there, we will need to add 1 or more "DNS records" to our domain to let DNS know where to find our server.
