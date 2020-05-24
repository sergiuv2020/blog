---
layout: post
title:  "Making Nginx easy to work with in docker-compose"
date:   2016-10-15 15:59:39
categories: [OpenSource]
tags: [docker-compose, nginx, bash]
share: facebook twitter linkedin
---

Two days ago I encountered a big problem. I needed to build multiple nginx images for different application stacks, that’s not cool at all.
Yes I could use Consul and registrator to actually have proper service discovery within each stack cluster but I didn’t wanted to have this overhead.

Wouldn’t it be great if could just give Nginx some env variables in docker-compose so that he knows what to balance from the start? Well I though that was worth investigating.

First I tried search for something already built, At some point I found a great implementation of haproxy done by tumtum but it wouldn’t really satisfy my need, I have multiple paths/ports in some of my services and I couldn’t just serve everything from port 80.

So then I gave it a go and written my own container, that just does what I needed. Nothing to fancy just a bash script that interprets specific env variables and creates locations and upstreams in nginx.

So now I can just have a few variables in compose like so:

```ruby
SERVICE_1: "location1:server upstream:9999"
SERVICE_2: "location2:server upstream:9122/server upstream2:9122"
```

and this creates the fallowing in nginx.conf:

```ruby
location /location1 {
  proxy_pass http://upstreamlocation1/location1;
}

location /location2 {
  proxy_pass http://upstreamlocation2/location2;
}

}

upstream upstreamlocation1 {
  server upstream:9999;
}

upstream upstreamlocation2 {
  server upstream:9122;
  server upstream2:9122;
}
```

If you want to try it out checkout the image on dockerhub:

[DockerHub Image](https://hub.docker.com/r/svidrascu/dynginx/)

If you want to add functionality to this, feel free to fork  [svidrascu/dynginx](https://github.com/svidrascu/dynginx)

Now I know that this is not really fully configurable, I could have even more power on the location directive but for now, it’s what I need :)
