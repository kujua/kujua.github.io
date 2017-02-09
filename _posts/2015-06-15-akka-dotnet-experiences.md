---
layout: post
title: Akka.net Experiences
sortorder: 4077
date: 2015-07-31
ignoredate: 0
photo-front-url: /res/blog-akka-card.jpg
photo-front-class: grid-image-wrapper-square
disqus_comments: 1
disqus_identifier: 2015-07-31-akkadotnet-experiences
---

**The actor model is the new cool in the .Net world. The concept as such is more than 40 years old and widely used.** 

Programming with the actor model is not difficult, but we always have to keep in our minds that everything we do in this model is asynchronous. Usually, web applications in .Net were written in a pure synchronous way: a request comes in, the request is handled on the server, a response is sent back to the client. If the processing takes to long, the connection between the client and the server times out.

This is a simple and effective way to write web applications, although eventually the app will run into scalability problems with either too many concurrent users or backend bottlenecks like database access. Tasks, _async_- and _wait_- keywords now take care of asynchronous communication in .Net, but especially their contagious nature is putting many developers off.  

The actor model does not solve this problem without work having to be done by the developer, but it gives a conceptual framework for how to ease the problems. The concept is 40 years old and has been implemented in different languages, Erlang - itself 30 years old - is one of the prime examples. The Java and Scala community has Akka and this is implementation now ported to .Net as Akka.net, which has had its 1.0 release not long time ago: [Akka.net](https://getakka.net).

Documentation for Akka.net is somehow thin, but it is possible to read the very good Akka documentation either for Java or better Scala and get an idea what the framework is about. There are some examples on Github, but going deeper into development will soon let you run against walls.

I am doing a project with Akka for a company and - bound by an NDA - I can't say too much about it or show real code, but I can give some notes about my experiences so far.

**Notes on messaging**

It is very important to use immutable messages for communication with and between actors. I opt for a simple message structure with a hash or dictionary as the main transport for business domain values. The reason for this is to avoid serialization and deserialization problems and enhance performance. Also, updates can be done without breaking existing actor versions. An actor just takes out from the hash what it needs for processing the data and leaves the rest alone.

![Actor Messaging](/res/actormodel-generic.jpg)

A tricky part is actor-to-actor communication regarding response messages. There are two options:

+ Tell is the fire-and-forget option. It sends a message to an actor and processes the next message in its queue.
+ Ask is the synchronous option. It sends a message to an actor and waits for the answer, optionally with defining a timeout. _Synchronous_ is not 100% correct, because the Ask-call can be wrapped in a closure or anonymous function and if it is decorated with the _async_-keyword it can be awaited, making the call asynchronous for the system.

In any case, the second option is blocking the processing of more messages from the actor's queue, so it needs to be used with caution. In a project's code you will probably use more Tell- than Ask-communication to keep the system responsive.

**Notes on actor hierarchy**

Normally actors are grouped by the business process they support. In my designs for business apps there always exists a supervisor, which is a normal actor and distributes the work to other actors in the group. The supervisor is the only actor that knows the business process and handles errors and other responses from the other actors in the group.

![Supervisor Hierarchy](/res/actormodel-supervisor.jpg)

It is also possible to create supervisors for each user of an application and keep the state of this user in the actor. Microsoft's _Halo_ implementation used this approach for multiplayer games, although with their own actor model implementation _Orleans_.

**Notes on remote actors**

Actor groups can be deployed in containers, which exposes and listens to a TCP port that is unique in the system.

For calling actors in remote containers, it is necessary to know the address, which is similar to _"akka.tcp://server@localhost:8042/user/remotesupervisor"_.

It is possible to get the supervisor reference from the container, but this requires some global variable magic. The location lookup with a predefined address in the configuration is not as accurate as an actor reference. The reference tells us that there is an existent actor, the location lookup, called _ActorSelection_, just gives us an actor address which might have an existing actor behind it or not. Both cases allow valid calls and do not throw an exception if there is no actor to take a message sent to it. Messages without recipient end up in the _DeadLetter_ queue, by the way.

Talking of containers: who does not think of Docker containers? On Windows it is not possible at the moment, but I am sure it will come soon.

More coming later.
