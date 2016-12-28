---
layout: post
title: The Future of Web Applications
sortorder: 4078
date: 2015-06-17
ignoredate: 0
disqus_comments: 1
disqus_identifier: 2015-06-17-future-web-applications
---

**Have pure web applications a future in view of mobile apps or will they slowly disppear? Let's investigate.**

When I talk to fellow developers and mention the possibility that web applications as we see them now will disappear they look at me with big eyes, shake their head, turn around and walk away.

Note the term *web applications*. We are not talking of web sites like a blog that delivers content, but applications with forms, charts, dynamic content from several web services and a user interface that is close to traditional desktop applications. And we are also not talking primarily about native vs web apps on mobile devices, we are talking more about the devices.

I am spending most of the time of the year in Africa in Kenya and there people - who actually can afford it - are using smart phones as main device, especially Android based. Of course, some have laptops, but for various reasons the majority does not want to carry them around. Also, internet access speed is flaky at times, depending on the location.

When we as an industry developed web applications in the last decade, the emphasis was on features. Often backend developers were forced to *design* a user interface for the web which was more practical than usable if usable at all for non-technical users. My own *creations* from this time are no exception.

Nowadays the emphasis is on the UI with designers and sometimes barely Javascript-speaking novices creating single page applications with the help of more or less powerful frameworks like Angular, Ember and others. Content or data is pulled in from REST services or CMS databases.

This approach is fine for desktop applications with good internet access, but is less viable for mobile devices with high-latency internet connections. The frameworks are doing a better job now to support the fragmentation in the mobile device market regarding screen sizes and screen resolutions, but features like offline usage of apps is not always implementation standard yet.

The performance and feature discussion about native vs web applications will be resolved eventually, although just now - depending on features demands on the device - native developments are better for many applications. Systems that let developers write their mobile applications in one language and transpile to native code before deployment like Xamarin are helping bridging the gap at the moment.

Can we transfer web applications written for the desktop one-to-one to a mobile device? Some will say 'Yes', others will say 'No'. I am in the camp of the latter, thinking for example of different approaches to navigation. It is quite possible that in a few years all major mobile platforms may have the same apporach and controls that are not distinguishable from each other. At the moment this is not the case.

I also do not think that JavaScript is the future of everything. ES6 is moving closer to the object oriented programming paradigm, while many developers are embracing the functional paradigm or at least a hybrid Object Oriented-Functional concept. Not to talk about the *isomorphic* approach - a phrase that lets anyone who dug a bit deeper into mathematics shout out in pain. There is a reason why there were many languages invented for server side programming and JavaScript was not one of them.

**Where are we going?**

I guess we will develop for mobile devices first and only; the desktop browser application will be a side project, but not an afterthought of course. The language used may be any suitable language and the application will be deployed as a native app, where *native* can certainly include web view apps once the gaps in performance, looks and native feature access are closed.

The applications will have strong offline capabilities and will save data to and retrieve data from services on cloud servers, restful or not. Security will be paramount and services will have to be optimized to minimize access time and deal with the latency and changing speeds of on-the-go internet access.
