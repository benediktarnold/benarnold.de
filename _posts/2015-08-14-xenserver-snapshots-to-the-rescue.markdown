---
layout: post
title: "Xenserver Snapshots to the Rescue"
modified:
categories:
excerpt:
tags: [xenserver, xe, snapshots, vm, virtualization, devops]
image:
  feature:
date: 2015-08-14T10:18:51+02:00
---
... or how to start a new vm from snapshot with command line xe.
----------------------------------------------------------------

Recently I killed the VM that I use to control and monitor my smarthome. I made some mistakes while trying to repair some lvm metadata and in the end the VM didn't boot anymore.
Luckily I made a vm snapshot some days before.

1\. List your snapshots and copy uuid
{% highlight bash %}
[root@xenserver-home ~]# xe snapshot-list
  uuid ( RO)            : 5f09d92f-bc8c-4927-b984-7ef08b8b87c1
  name-label ( RW)      : smarthome_2015-07-24T20:14+0200
  name-description ( RW): Smarthome server with Kibana, elasticsearch, logstash
{% endhighlight %}

2\. Install the new vm
{% highlight bash %}
[root@xenserver-home ~]# xe vm-install new-name-label=smarthome2 template-uuid=<uuid of your snapshot>
3e41bc4f-fb71-849b-6b55-1fafed153c67
{% endhighlight %}

3\. Start the new vm
{% highlight bash %}
[root@xenserver-home ~]# xe vm-start uuid=<uuid of the new installed vm>
{% endhighlight %}
