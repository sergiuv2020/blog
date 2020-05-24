---
layout: post
title:  "Sharing Chef Awesomeness to the DevOps community in Iasi"
date:   2016-10-29 13:53:00
categories: [OpenSource]
tags: [chef, vagrant, inspec]
share: facebook twitter linkedin
---

#### The DevOps Meetup
Last Thursday I had the opportunity to share my experiences with [Chef](https://www.chef.io/) to the DevOps practitioners in Iasi. I met a lot of people using docker, puppet and even Ansible in Iasi, sadly not so many using chef. 

I've went trough chef with them sharing the good and the bad I've experienced working with it, chef architecture, a live demo and felt that I should also write it down, well at least a few important parts from the presentation.
So bare with me if you want but keep in mind that some ideas are based on my own view of the system at the time i'm writing this.

#### Diving into a world of endless possibilities

Chef is an infrastructure automation tool aiming to continuously define, build and manage infrastructure. You can use it with your dev/test/production environments or if you want you can also use it for workstation or PC setup.

Why workstation?
Well think about all the time it takes a new colleague to setup his workspace for the new project, ide's, repos, libraries, specific tools. You can save that time by having a simple chef project.

It is a great tool to work with, easy to dive into it, however actually getting to be proficient with it and build reliable and reusable code will take a bit of practice,    learning and a few inevitable headaches.

Don't be scared that you need to learn ruby to be able to use it, Chef uses a simple DSL which helps you a lot in starting your journey. You might feel overwhelmed by all the cooking related primitives used in chef but actually there aren't to many.

- *Cookbook* = Your chef project, it contains recipes, one ore more
- *Recipe* = Similar to a class, defines what should be done to a certain infrastructure
- *Attributes* = Chef Global Variables
- *Resource* = Similar to a function with inputs and outputs for your infrastructure
- *test-kitchen* = a tool that helps you test your cookbook in isolation
- *templates* = Ruby Erb templates that you can use to dynamically defines file contents, like conf files for example
- *foodcritic* = A chef lint tool
- *Inspec* = post deployment test tool
- *chef spec* = unit test tool
- *Knife* = a tool that helps you control chef and your infrastructure from one workstation
- *chef server* = a server where you can store your cookbooks and manage your environments

That's all you need to know at first.

#### How, what, where?

You can start your journey easy with their tutorials as for your initial setup, just get one app to rule them all: chefdk, which comes with a fully equipped kitchen on the side and a few food critics :)

Yes, not joking, test-kitchen and foodcritic are two apps that come along with the chef development kit. And to sweeten the deal even more, you also get ruby, nicely packed so you won't have to shoot yourself in the foot trying to install it.

You can use docker, vagrant or any other machine provider out there to get yourself started, cloud providers also, of course.

GO PLAY WITH IT!

#### Pros and Cons

This is a list based on my experience with the toolset.

Pros:

- Erb Templates
- Using ruby code for custom functionality
- Defining your own resources
- Brilliant Testing Capabilities out of the box
- Awesome community
- Good documentation
- Idempotency
- A lot of flexibility and control when using Chef Server
- Business logic integration by using roles, environment
- Solr indexing server within chef server that helps you get and change server attributes very fast

Cons: 

- If not built right, quite slow, mainly because of all the downloads (dependency download) and the pure fact that it uses an agent

You can check-out the presentation [here](http://slides.com/sergiuvidrascu/cooking-with-chef), but be careful, it's part Romanian, part English.
