---
layout: post
title:  "Understanding Microservices, Part I: An Overview."
date:   2015-11-05 22:00:00
tags: microservices, soa, architecture
categories: microservicesseries
---

Microservices are the hottest trend right now. The first article I read about the subject was authored by Martin Fowler, [in his blog][microservices]. Despite its hotness, the principles of Microservices are based in best practices learned about the development of web applications in the last decade. Many of the principles preached by Microservices evangelists also apply to SOA (Software Oriented Architecture) and there's a never ending discussion about whether Microservices and SOA are the same thing, or Microservices is an evolution, or a whole different thing which shares many common principles. I don't intend to engage in this discussion, because for a developer like me, it doesn't matter.

An application that follows the Microservices model is composed obviously of one or more services. Each service represents a single, well-defined component, which is deployed independently. Components may be written by different teams, with different languages and technologies. All interaction of components happens through remote protocols, usually using RESTful web services and messaging technologies, and consequently there's an inherent concern with fault tolerance, scalability and performance.

At this point, the main technical differences between classical SOA and Microservices become more apparent. In Microservices, it's always preferable use a decentralized model, preferring asynchronous communication via AtomPub or messaging; Choreography guided by the use of HATEOAS and dumb message routing, instead of complex orchestration standards and sofisticated middleware; There's also more emphasis in infrastructure automation and continuous delivery, based on the learnings of Agile and DevOps practices in the last 15 years.

There are a number of techniques and paradigms that fit well to the Microservice world. Since applications based in this model are inherently asynchronous, modeling data as a series of immutable events helps the application to achieve the desired level of scalability. This techinique is known as Event Sourcing, as Greg Young mentioned in his many talks. [Event Sourcing][eventsourcing] also helps to follow the "Tell, don't ask" principle, since a data change event may be used to propagate information between two or more services, usually using an asynchronous channel.

[Domain Driven Development][ddd], or simply DDD, helps one to understand the boundaries of a service, its main entities, its business rules and interactions. Alistair Cockburn's [Hexagonal Architecture][hexagonalarch] is also a good fit since, it's centered on the idea of having a central domain model and adapters to the service's many interfaces, such as data access interfaces and other external and internal endpoints.

Since all components of an application may be developed by different teams and accessed by numerous other components, every component must be throughly tested, and continuously integrated in order to meet the product's time to market and overcome its inherent technical complexites. So, more than ever, the knowledge of different types of testing and how they fit together must be in the mind of every developer. There's a [great presentation][microservicetesting] on the different kinds of testing that can be done in a Microservice application, although many of the techniques shown also apply to other types of applications and architectures.

Infrastructure automation plays a significant role in the Microservices architecture. Every component must be automatically deployed in each environment (dev, test, qa and production), execute all tests, and proceed to the next environment, composing a Continuous Delivery Pipeline. There will be a lot of components, with different infrastructure sizes and configuration, therefore it's not feasible do this by hand. Configuration Management tools are essential to this task, such as Puppet, Chef, Salt Stack and Ansible, but hard and soft virtualization and related tools are also welcome, such as hypervisors, IaaS stacks, LXC and cgroups and, of course, Docker.

That's a lot of information for one to learn in order to reach enlightenment. Most articles about these subjects help understand what and why they're important, but give little insight on how to build this complex systems from scratch and what problems will arise once we start deviating from the traditional three-tier model to a Microservices one. Most of this information is scattered on the net, but I intend to write a series of articles that will describe the building a microservice application from alpha to omega, while reviewing each of this principles. As I am more a learner than a teacher, feel free to comment and advice whenever you, dear reader, want.

[microservices]: http://martinfowler.com/articles/microservices.html
[eventsourcing]: http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/
[ddd]: http://www.amazon.com.br/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215
[hexagonalarch]: http://alistair.cockburn.us/Hexagonal+architecture
[microservicetesting]: http://martinfowler.com/articles/microservice-testing/
