---
layout: post
title: Personal Supercomputing in the Cloud
---
So the title of the post may contain a bit of hyperbole, but I think we are clearly and rapidly headed
in that direction. For about a year now, I have been playing around with the various abilities
of <a href= "http://aws.amazon.com/">Amazon's Web Services</a>, spending most of my time on ec2.
I have been particularly interested in the HPC offerings, "Cluster Compute" and "Cluster GPU" instances.
These instances have 8 cores coming from two quad core Intel Xeon X5570's, 23 GB memory (22 for GPU instance)
and 10 Gigabit Ethernet.  The GPU instances, as the name suggests also include two NVIDIA Tesla M2050 GPUs.
Each instance alone packs decent computational firepower, but the real value is seen as soon as these instances
are launched in parallel and clustered, leveraging the elastic nature of ec2.  I decided run some simple benchmarks
on ec2 using <a href="http://www.ks.uiuc.edu/Research/namd/">NAMD</a>, a molecular dynamics software which I help develop.

I ran basic MD simulations on two different systems: Thioredoxin reductase (4,371 atom protein, 45,750 atoms solvated) and
a nitrilase (87,084 atom protein, 468,429 atoms solvated). I ran the simulations on single CPU only and GPU instances to
illustrate the benefits of GPU acceleration, and also across small clusters of CPU only instances to demonstrate the
scaling across nodes (testing the 10Gb interconnect as well).  
<img src="/thionitr.png" height=95% width=95%/>

It is obvious from these graphs how software can benefit from GPU acceleration, especially with two NVIDIA Teslas
at its disposal.  As shown in the thioredoxin results, the speed advantage from a single GPU instance cannot
even be matched by a three CPU only instance cluster.  Considering a GPU instance is $2.10/hour and a CPU instance is
$1.60/hour, you are certainly getting your money's worth from the GPU's if your software can utilize them.

Also interesting is simply the speed that can be achieved on these instances. One GPU instance nets you roughly .08 days/ns
of performance.  For those unfamiliar with molecular dynamics, this metric describes how many real world days are required
to calculate 1 ns of simulation time.  Most simulations range from the 10's and 100's of ns to 10's and 100's of &mu;s depending
on the process being studied. Squeezing about 12.5 ns a day out of a single GPU instance when simulating 45,750 atoms might
not seem exciting to researchers accustomed to running on top 500 supercomputers, but it is encouraging regardless. Not every
researcher receives millions of dollars in grants and access to the speediest supercomputers. As a huge proponent of the 
"democratization" of science, I certainly enjoy seeing ec2 delivering such good performance to anyone with a few dollars at the
click of a button.

Granted, once you start calculating the costs of running even a single GPU instance for a full day (about $50), the money
seemingly adds up quickly. What needs to be considered, however, is not just the upfront per hour cost, but also all of the
savings resulting from having amazon do all of the hardware work. Using ec2, you can literally launch an 8-node cluster
with the click of a single button.  You do not need to worry about privisioning hardware, setting up your own cluster,
paying for the electricity and maintaining every hardware component that will undoubtedly fail at some point. Setting
up a basic HPC cluster can be accomplished by almost anyone within just a few minutes, start to finish. Below you can
see a video from Amazon doing just this, even running NAMD!
<iframe width="420" height="315" src="http://www.youtube.com/embed/5zBxl6HUFA4" frameborder="0" allowfullscreen></iframe>

I find this exciting, as even the smallest research group or curious individual can have access to their own personal HPC
cluster. There are even companies such as <a href="http://www.cyclecomputing.com/cyclecloud/overview">Cycle Computing</a> that
offer solutions built on AWS to make it even more convenient to launch and manage HPC cloud clusters (such as queueing systems).
There will always be a place for ultra-high performing supercomputers, but now there are viable solutions for the rest of the world.
