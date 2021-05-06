---
layout: post
current: post
cover:  assets/images/api-gatway.png
navigation: True
title: What is API Gateway Server
date: 2021-05-06 00:00:00
tags: [System Design]
class: post-template
subclass: 'post'
author: heyvp7
---

In our previous post, we have seen about Load Balancer. In this post, we will be seeing about API Gateway and the little difference between Load Balancer and API Gateway.

The main job of the LoadBalancer is to forward the request which comes from the clients to the server, while the API gateway forwards the requests based on various conditions.  Both LoadBalancer and API gateway can cache the static resources.

### SSL Updates

In general Load Balancer will be accepting both HTTP and HTTPS requests while API gateway is restricted to accept HTTPS API request only.

Its general practice to update the Encryption keys of the SSL certificates for HTTPS requests each month or on a certain frequency. These things are maintained in the API gateway mostly.

### Authentication and Authorization

Both Loadbalancer and API gateway can help in the authentication part. Some of the complex services will be having complex authorization logic like some API for a specific set of users or organizations. This complex logic can be handled well at API gateway than in LoadBalancer.

### Splitting into Microservice

API Gateway helps the service to split into multiple Microservice.  For example, consider https://www.flipkart.com the famous e-commerce website in India.

In Flipkart there are a lot of actions, adding products to the cart, adding and fetching credit card details, displaying the products.

Each and everything is accessed from the client via API requests. So when the user adds a product into their Cart, first the request will land to API gateway and the Gateway based on the API pattern will redirect to a specific set of servers.

![API Gateway Diagram]({{site.url}}/assets/images/api-gatway.png)

**In the Above diagram consider**

- Servers with Number 1,2,3 for Adding products to Displaying Product
- Servers with Number 4,5,6 for Adding products to cart
- Servers with Number 7,8 for Fetching Credit and Debit card details


### Routing of Request

Previously we saw the request landing to specific servers based on the user action. In the same way, based on the devices, we can forward the requests to various servers.  These are done when mobile-based API is developed. In mobile-based scenarios generally, the amount of data transferred is very minimal so developers try to remove unwanted keys as much as possible and also try to accept fewer inputs from Android or iOS mobile devices.

### Logging and Monitoring

An API gateway that can be helpful is Logging the API requests came servers. Logging can help products in a various way like allocating more resources based on the studying API patterns/device request patterns

### Rate Limiting

In the API gateway based on the client devices or authentication/authorization rate limiting can be done.  Say we can add 35 products in our cart in one min, beyond 35 products sometimes it can be done by spammers also. So such types of rate limiting can be done at API gateway itself instead of hitting to Servers.

### Can Act as Central Adaptor

API Gateway can act as a central Adaptor that can communicate with various microservices.  It can act as a coordinator between microservices.

