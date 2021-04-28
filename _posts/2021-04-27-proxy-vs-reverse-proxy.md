---
layout: post
current: post
cover:  assets/images/proxy-vs-reverse-proxy.jpg
navigation: True
title: Proxy vs Reverse Proxy
date: 2021-04-27 10:00:00
tags: [System Design]
class: post-template
subclass: 'post'
author: heyvp7
---

Lets learn about the basics of Proxy server vs Reverse Proxy server. 

## Proxy Server 

Proxy is helpful for the client-side connection. It mainly helps the client to hide their identity. 

We can consider a scenario where we connect to the internet via our college network. Think of 3 friends connecting to various servers

- Friend 1: Connecting to the internet via Android phone to google.com 
- Friend 2: Connecting to the internet via iPhone to youtube.com 
- Friend 3: Connecting to the internet via Dell Laptop to wikipedia.com 

We all 3 connect via our college internet. And our college has a proxy server named CollegeProxy Server.

First of all, all our requests will be going to this CollegeProxy Server, and this server will be making connections to google.com or facebook.com, or twitter.com for us. 

### Hide Client Identity

For google.com or youtube.com or wikipedia.com, all the details from the client are got by this CollegeProxy Server and this CollegeProxy Server requests us. All these  google.com, youtube.com, and wikipedia.com  will only know CollegeProxy Server has requested.  

### Blocking website

To make students productive, colleges will be blocking sites like facebook.com or twitter.com if we are connecting via college internet. 
A proxy server will be very much helpful for blocking unwanted websites.

### GeoFencing

Some of the sites can be restricted to access when connected via proxy server alone. For example, when we are connected to our College internet connection (which in turn connects to our CollegeProxy Server)  we will be allowed to access our digital mark sheet website, assignments website, and timetable website which we will not be allowed when are outside of our college internet


## Reverse Proxy

Reverse Proxy is helpful for Servers. 

As the Proxy server helps the client-side connection (like making anonymity of 3 Friends mentioned above), Reverse Proxy helps Server from unwanted clients. 

Let's assume there are few internal websites in our College. And now let's assume we have a reverse proxy server named CollegeReverseProxy.

Let's name the domain of the internal website as  collegeinternalwebsite.com

### Hide Server Identity

Our college internal website (collegeinternalwebsite.com) will be running on 5 or 6 machines. If the IP address of those machines is known to hackers then it can be corrupted. CollegeReverseProxy server can help in **hiding the internal IP address of the servers**.

### Blocking bots and unwanted users access

Consider there are some notorious students who try to access college internal resources without giving the password and username, these types of **unauthorized access** can be stopped at CollegeReverseProxy before sending the request to the resource website.

Think of 1000 requests coming within 10 seconds to the same internal resources from the same machine. Requests like these are mostly **targeted attacks** and these types of requests **are blocked at CollegeReverseProxy** level itself before coming to the resources server

### Can Cache Resources

ReverseProxy server can **cache the most static resources** which won't be changed for a long time. With this, load coming to the servers can be reduced.

### Act as Load Balancer

Load Balancer is the special type of use case of Reverse Proxy and its most common example. Simple we can use a Reverse Proxy server to **distribute the request to different servers** based on some logic. We can check the later detailed post about Load balancer.
