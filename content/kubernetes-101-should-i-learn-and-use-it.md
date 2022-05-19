---
title: Kubernetes 101
subtitle: Should I Learn and Use It?
prerequisite: [container, container orchestration, microservice]
publish-date: false
---

When I started learning about DevOps, one term that keeps on appearing was "Kubernetes". Reading that it is the de-facto container orchestrator all the way to being "the way forward" I naturally gravitated toward it. It took a while but now I can safely say that I have some cursory knowledge about the topic and can help you answer two questions:

1. Should I learn Kubernetes, and
2. Should I use Kubernetes?

### The Good
Let’s start with what everyone seems to focus on, the advantages that it brings.

Ideally, you only have to set up a Kubernetes cluster once, set it to autoscale, and it will take care of itself no matter how many applications you want to run on it. Don’t have many visitors at night? Scale down to one node and spin up just one instance of your application. Your website went viral? Spin up new nodes, and scale up your application to handle the surge of visitors. Kubernetes can easily do that.

Another thing that Kubernetes enables developers and companies to do is to implement a proper microservice architecture. Imagine manually/semi-automatically maintaining a hundred small microservices each one doing a specific task. Even with the use of containers and maybe even Docker Swarm, a limited number of microservices can be effectively managed by a human. Kubernetes, on the other hand, can (almost) effortlessly handle thousands, even tens or hundreds of thousands, of containers at the same time.

With just these two capabilities, a wealth of options open up for developers:

- Want to test a new version of your application or a microservice but don’t want to risk an outage? Deploy both at the same time, send the request to both versions but only use the response of the current version (shadow deployment).

- Want to support multiple versions simultaneously but not sure which will receive more traffic? Deploy both and just autoscale.

- Want to (hopefully) save on infrastructure costs? Divide that monolith into autoscaling microservices instead of scaling a single monolith vertically.

### The Bad
All that convenience, power, and reliability comes at a cost: infrastructure and operational costs.

Kubernetes clusters are generally divided into two parts: a master node plus one or more worker nodes. A master node is the one that checks, controls, and schedules each container. It is responsible for monitoring each application and, if applicable and needed, spinning up a new instance to handle more load. A worker node, as the name implies, contains the applications themselves. This separation translates to infrastructure costs. Even without any running application, the smallest cluster will cost more than a virtual private server running idle.

The separation also means computational and technical overhead. Kubernetes doesn’t run on magic but is in itself another application. An application that requires CPU resources, RAM, disk space, and of course human setup and maintenance (no matter how little). The computational resources (CPU, RAM, disk, power, etc) can be offloaded to managed services like GKE and EKS but with a convenience fee. The human part would probably be the hardest part to find especially in the Philippines because of (a) relatively new technology, (b) initial cost to implement, and (c) lack of trained personnel.

### The Answers

> Should you learn Kubernetes? Absolutely!

Whether it becomes useful professionally or not, the things I’ve learned along the way have become valuable to me. Setting up my home lab, Ansible, and networking are just some of the topics I had to learn first before I was able to set up my own Kubernetes cluster. Even if I didn’t end up using Kubernetes for my personal projects, all the other things proved useful in some other ways.

> Should you use Kubernetes? It depends.

For me personally, the infrastructure costs were too much given my requirements. I don’t have any project that requires auto-scaling, I don’t need to deploy a ton of microservices, I don’t need to support multiple versions of any API, and the list goes on. Kubernetes solves a lot of problems but problems I don’t have right now.

Professionally though, it’s a different story. I can see a lot of advantages of moving to Kubernetes but, again, the technical and operational costs are too high for immediate (or maybe even long-term) adoption. Breaking apart monoliths, and turning them into microservices is not an easy (or even necessary) task at this point. Maybe in the future, I’ll revisit the idea and try to create a proof-of-concept again.
