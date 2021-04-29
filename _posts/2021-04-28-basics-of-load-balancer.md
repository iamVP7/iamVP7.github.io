---
layout: post
current: post
cover:  assets/images/proxy-vs-reverse-proxy.jpg
navigation: True
title: Basics of Load Balancer
date: 2021-04-28 10:00:00
tags: [System Design]
class: post-template
subclass: 'post'
author: heyvp7
---
Load Balancer 

In our previous post Proxy Vs Reverse Proxy, we have seen reverse proxy is widely used as Load Balancer. In this post, we will be checking what is a load balancer, what are various advantages of using a load balancer, what are the commonly used algorithms.

In this post, we can consider the website https://www.flipkart.com one of the famous E-commerce shopping website.  From May 2nd - 7th they are having a massive event named Big Savings Days. During this time the requests from the users like us will be tremendous. Flipkart will be having  100's of servers for scaling this many users.

### What is Load Balancer

A Load balancer is a Reverse proxy. It is mainly used to distribute the huge income of requests from clients to various hosted servers. The Flipkart load balancer will be first accepting the request and then forward it to one of the 100's servers which is free to serve the request.

### Features of Load Balancer

- Effectively distribute the traffic coming from clients to various servers (if all request lands on to same server users will be affected so it has to be distributed)
- Maintain the flipkart.com with great stability, by distributing the requests to the servers which are only available.
- Can help in authenticating the client.
- Can distribute the request to different Flipkart app servers based on the type of device used.

### Load Balancer Algorithms

To distribute the load effectively, the reverse proxy uses certain algorithms to forward the request. They are mainly classified as Static algorithms and dynamic algorithms.

#### Static Algorithms

Assumptions are made beforehand and the state of machines is not considered. 
Static Algorithms are easy to configure but sometimes some machines get overloaded.

#### Dynamic Algorithms

They will be considering the state (load) of the machine and distribute traffic accordingly. 
They are difficult to design but are effective and can maintain the reliability of the sites.

### Algorithms

Below are some of the most widely used algorithms. There are a lot of other techniques also.

#### RoundRobin Algorithm
Assign the first request to the first server, second to second, and moves on in a circular fashion.

#### Randomize Static
Distribute the requests in a random way among all the servers.

#### IP Hash-based
Find the hash of the client IP (user IP address from which request is sent) and use the hash function to distribute it to different app servers.

#### Sticky Session
In this type of algorithm, the load balancer will be persisting the information of the server which handled the request.

Say the first request comes from User1, it lands to the server10; then when the request comes again from the same user, the load balancer will be forwarding the request to the same server10. This is sometimes achieved using sessionid or cookie.

#### Master-worker Schema

In this, there will be a Master who will be distributing the tasks to other servers (sometimes referred to as slaves). Here all the slaves have to report whether they are idle. This algorithm will distribute the load decently to all the app servers based on the load. The main problem is it's very difficult to design and also the communication overhead is too high.

There are more things to learn in this direction like Consistent Hashing, Rate Limiting(one of my friends wrote an article on this, checkout in  [hashnode](https://buildwithsammie.hashnode.dev/how-to-design-a-scalable-api-rate-limiter)), API Gateway, and so on.
