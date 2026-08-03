---
layout: Post
permalink: /projects
content-type: static
title: Projects
description: Platform engineering projects I've built or led at Adobe and Rakuten.
---

<p class="about-lead">A few of the platform engineering projects I've built or led — mostly developer platforms and the service infrastructure underneath them.</p>

## Adobe Service Runtime {#adobe-service-runtime}
<div class="post-meta"><span class="tag">adobe</span> <span class="tag">java</span></div>

Adobe Service Runtime (ASR) is an implementation of the [Microservice chassis](https://microservices.io/patterns/microservice-chassis.html) pattern. It provides mechanisms to handle cross-cutting concerns like logging, health checks, metrics, and easy access to foundational Adobe services via connectors.

ASR primarily supports Java and Spring, with a few libraries available for Python.

### Why is ASR required?

1. Provide a collection of components, tools, and best practices ([12 factor](https://12factor.net/)) which enable rapid development of four-9s-capable, innovative, and secure services at Adobe by product and research teams.
2. Enable a container-first deployment system.

### My role in this project

- I'm the hands-on lead engineer/architect/product manager for this suite of libraries.

### Impact of ASR at Adobe

- Using ASR has saved 4–6 weeks of setup time for new Java projects at Adobe.
- Secure BOM for every Adobe service that uses ASR.

## Service Registry Wrapper APIs {#service-registry-wrapper-apis}

At Adobe we use ServiceNow as the service catalog store. This store has all the metadata for a given service — GitHub repo, owner info, cost centers, endpoints, API docs, and more.

Every microservice onboarded onto Adobe's Developer Platform has an entry in ServiceNow. During onboarding of a new service to Adobe's IDP, the platform can create a Service ID if it doesn't have one. For services that already have an ID, we need to validate whether the user is using the right Service ID.

To cater to these needs, we created a wrapper around ServiceNow — a Golang-based gin-gonic service.

## Other projects

A few more I've worked on, briefly:

- **VeraLIS: Laboratory Information Systems** <span class="post-meta" style="display:inline"><span class="tag">java</span> <span class="tag">vaadin</span> <span class="tag">veracyte</span></span>
- **SPRODA: Slice Product Data for Advertising** <span class="post-meta" style="display:inline"><span class="tag">aws</span> <span class="tag">dynamodb</span> <span class="tag">faas</span> <span class="tag">lambda</span> <span class="tag">rakuten</span></span>
- **Grandcentral**
- **Provisioner**
- **Glider**

More on my [About](/about) page, or on [GitHub](https://github.com/animathad).
