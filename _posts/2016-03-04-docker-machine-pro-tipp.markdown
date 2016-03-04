---
layout: post
title: "Docker-machine Pro Tipp"
modified:
categories: 
excerpt:
tags: [docker, docker-machine, bash, devops]
image:
  feature:
date: 2016-03-04T14:51:50+01:00
---
Tired of typing "eval $(docker-machine env default)" again and again?
-------------------------------------------------------------------
I use docker-machine day to day with multiple machines. To make my life easier, I put a litle shell function in my .zprofile/.bashrc

{% highlight bash %}
dme(){
	eval "$(docker-machine env $1)"
}
{% endhighlight %}

From now on I only type *dme machine1* to switch to machine1 or *dme default* to switch to my default machine. 
