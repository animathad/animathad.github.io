---
title: "Service to Service Communication between containers on your localhost"
tags: [containers, docker, docker compose, microservices, service to service]
description: "tldr; Inside the containers other containers can be called by their service names described in docker-compose.yaml Outside the containers (your laptop)…"
original_date: 2022-02-13T06:24:18-08:00
---

tldr;

- *Inside the containers other containers can be called by their service names described in docker-compose.yaml*
- *Outside the containers (your laptop) they need to be called by localhost:<port>*

```
version: '3.8'
services:
  serviceA:
    build:
      context: .
    ports:
      - "8080:8080"
  serviceB:
    image: serviceB-image
    ports:
      - "9090:8080"
```

- *In serviceA use* `http://serviceB:8080/hello` *to call Service B, instead of* `localhost:9090/hello`
- *localhost -> serviceB*
- *NOT 9090! -> 8080*

I have a ☕️ Java Tomcat Service A that talks to 🐍 Python Flask Service B.

![](/assets/img/posts/service-to-service-communication-between-containers-on-your-localhost/1-dvf9BfKui6h863EWcFvFow.png)

Service A runs on 8080 & Service B on 9090. See I am smart💡 because I chose different ports to avoid port conflicts.

Everything works great in the non-container world. From my Java Service A, service discovery is easy peasy. You call <http://localhost:9090/serviceB> and we are good.

### When ServiceB get “pip”ed

As I add Python libs in the Service B it becomes nasty. *I hate your GCC compiler* (Mac vs Linux) or some dependency of dependency, gives you an error, which doesn’t tell exactly what is wrong and holds your weekend ransom 🔫 . Shit Happens! 💩

So my in my infinite wisdom I containerize 🐳 them. It’s a little slow but better than managing the chaos of dependencies. If you have a million Python projects on your laptop this is appreciated even more.

Alright I containerized them. Because I containerized, I don’t have to worry about port conflicts.

> I will use 8080 because Java has institutionalized me to use 8080.

Cool Kids at React use 3000! The lazy just me wants to ping [http://localhost:8080/serviceB](http://localhost:9090/serviceB) and voila nothing happens! Aaargh! Why? Meanwhile, I have switched between Reddit, Social Media, Twitter and WSJ by now. Because I hate being stuck and my ADHD starts distracting me.

I gather myself, let’s google it. *Can’t access containerized App from localhost.* Within 2 secs I learn about the port mapping. The restless me has already updated by the port mapping to `-p 8080:9090` Doesn’t work. Dang! Why does this happen to me? I should have been an MBA, wouldn’t have to deal with this shit. Another ADHD trip and Googling reveals, now I learnt the port mapping must be reversed. `-p 9090:8080` Phew! I ping the endpoint <http://localhost:9090> and feel like Mark Zuckerberg. Billion dollar Unicorn here I come.

### Time for Service to Docker Communication

![](/assets/img/posts/service-to-service-communication-between-containers-on-your-localhost/1-qFzp-E0XVhgiLYH_O4A1rA.png)

I haven’t containerized Service A. I mean it’s a Java Bulldozer who wants to containerize and make it painfully slower? I update my configs to call Containerized Service B <http://localhost:9090/serviceB> and of course I feel like a million dollars.

I have solved the notorious Python dependency problem with a container and that’s as much I am willing to go with containers. I mean I have a life, I can’t get sucked into the containers. I think outside the Box, I am a visionary!

### When Contributors burst your bubble! 💥

After I feel like I have conquered the world, I write a detailed doc on how to contribute to this awesomeness. Add pictures, gotchas, snippets and the whole shebang! (are we still allowed to use this?, I wish there was a linter that could check those, may be there is, too lazy to research)

An enthusiast forks my service and asks me what is JDK, JRE, what is maven?🤦🏽‍♂️ but he is supposed to be a Python Guru.

I forgot there is a world beyond Java, where people have fun with programming! They don’t want to learn the whole Java stack (or anything remotely close), they just want to contribute to Python stuff.

Back to the box again! I containerized Java. Yay!

### localhost:9090/serviceB doesn’t work from my Java container!

![](/assets/img/posts/service-to-service-communication-between-containers-on-your-localhost/1-Ubv0zhrupOrwwWalZrCViA.png)

ok, I get it! localhost for Java container means its own container and there is nothing on 9090 there. You gotta use the “hostname” and may be use docker-compose.yml to make it elegant.

```
version: '3.8'
services:
  serviceA:
    build:
      context: .
    ports:
      - "8080:8080"
  serviceB:
    image: serviceB-image
    hostname: hostB
    ports:
      - "9090:8080"
```

Alright, look at me, how fluent and disciplined. Before, I update my Java calls to [http://hostB:9090/serviceB](http://localhost:9090/serviceB) I want to test it! Because I am a smart Engineer and I can tell you Battle stories 🏰 of how I went in without testing and got bruised etc.

So I ping [http://hostB:9090/serviceB](http://localhost:9090/serviceB) from my laptop. Unknown Host! Wow! I have been taken for a ride. This whole docker compose is a scam right? I mean you say something but you won’t mention how to validate it and get away with it. Just like Politicians!

Googling as always gives more wisdom than I can digest. I just want to finish this and doom scroll my Reddit feed man!

One dude or dudette says you gotta update `/etc/hosts`the other use `docker network` Someone wrote a Python script to update `/etc/hosts` I mean people have a lot of time No? Don’t people have to take ADHD trips or doom scroll their Twitter feed? Seriously people get a life!

All the solutions were too nerdy for me. I just want to do it with a few lines of change. I am the first mouse of *Who Moved My Cheese?* 🧀 I refuse to goto another Cheese station and will wait here for the Cheese to comeback.

### Occam’s Razor

An entire weekend passes, turns out `hostB` is accessible from inside Java Container and not my local machine. You don’t even need to add the `hostname` field. FML!

And if I had not decided to validate, it would have worked and I would saved my weekend and be much younger when I write this! So much for learning from your mistakes.

The good news is we get to do all over again next Friday!
