---
title: "High Concurrency/Availability/Reliability System Write Up"
layout: post
date: 2019-04-01 19:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
- system and backend
star: true
category: blog
author: jsyqrt
description: High Concurrency/Availability/Reliability System Write Up
---

## What is high concurrency system

Any resource is limited, so we need to scale up/out. When there are lots of requests in the system, it is impossible to support those requests with a simple architecture(i.e. ui/webserver/database).
We need a more complicated system to support client's requests.

There are some key concepts to be considered.

Functional requirements:

* High concurrency, a value to show how many requests are processed per second, often in tps.
* Low latency, a value to show how fast a request is processed, often in ms.
* Availability, a value to show the probability of the system to be available in a total time range, often in /. It is calculated by `A = Up Time / Total Time`.
* Reliability, a value to show the probability of the system perform to perform correctly, often in /. It is calculated by `R(t) = 1 - Probability of Failure`.

Non-Functional requirements:

* Scalability, to show the cost to scale the system, i.e. scale horizontally(deploy more machines), scale vertically(upgrade the hardware, virtualization involved).
* Extensibility, to show the cost to extend the system, i.e. add more functions/services.
* Maintainability, to show the cost the maintain the system, i.e. bug fixes or code updates.
* Controllability, to show the cost to control the system, i.e. avoid library attacks, invalid action attacks.

Basic implementation requirements:

* Component/Micro Services, is a requirement to split the system to many pieces to be easier to achieve requirements above.
* Security, is a requirement to keep things in control.

  * Confidentiality, who has no correct authorized toke cannot know the data/service.
  * Integrity, who has no correct authorized toke cannot change the data/service.
  * Availability, who has correct authorized toke can access/change the data/service.

Also, there is a concept called RAS from IBM, which means Reliability, Available and Serviceability.

* Reliability
* Availability
* Serviceability is used to show the ability of the technical support of the system.

## How to build a high concurrency system

There are some key tools to be used to help to reach requirements above.

* Service Split, to split the system to multiple micro systems, easy to update, maintain, control, debug, deploy...often with dubbo by Alibaba, an rpc framework with service registry/discovery, load balance.
* Cache Mechanism, to support lots of read requests. If write, write to db and delete in the cache.
* Message Queue, to do decoupling, asynchronous, peak flatten.
* Scheme Split and Table Split, to restrict the size of schemes and tables to avoid massive requests to a single node.
* Read Write Split, lots of Read and relatively rare Write, so Read from backup and Write to primary.
