# Scalability

When it comes to scalability, there are a couple options available to us .

## Vertical Scaling
Make the individual servers bigger. Make the CPU's beefier, upgrade the storage, etc.
Usually the only option in the past, but now we have access to horizontal scaling.
The only place I can think we use this is Minecraft servers. Cause Minecraft can't do multi-threading lol.
## Horizontal Scaling
When you make more copies of the server to increase max load. You can usually have each server copy handle certain aspects (load management, request management), leading to increased efficiency.
When it comes to web servers, horizontal scaling can be done pretty easily since it's mostly just requesting data.
Databases are also pretty good at handling data queries across servers, especially since

## Hybrid Scaling
Not everything scales super good horizontally, and not everything should be scaled vertically.
In the real world, we tend to keep the servers horizontally scaled, while we let the database scale vertically.

## Elasticity in the Cloud
While having your physical servers can be nice, the cloud provides a lot of flexibility that physical servers are unable to provide. Physical servers also cost a fuck ton in time, electricity, and maintenance costs. 
With the cloud you pay for what you use. So while the monthly subscription can suck, you can scale up and down super easily without having to pay for that extra unused server space.

# Docker and Deployment
Scalability like this is ONLY possible if you have a quick way of deploying your solution.
People can't do this, you gotta *containerize* your code.

Docker is a containerization tool, you can instead make **images** of your applications and run them anywhere.
This is super useful for deployment and scalability, as you can transfer images without having to transfer code. It's also useful for sending indev builds to QA without fiddling with dependencies and code.

## Docker vs. VM
Virtual Machines are similar to Docker, but verrrryyy different.
Virtual machines load an entire operating system at a time, requiring a *hypervisor* program between that and the host OS. 
*Hypervisor* is a program that tricks the VM OS into thinking that it's running on bare metal. It started out as a separate program, but now we typically build it into the hardware to get more performance.
The apps are still specific to the OS though, and we're basically emulating and entire computer just for one program. Docker however replaces the hypervisor with a *container engine* instead. That *container engine* sandboxes the individual apps, giving them their own environment to fuck around. With this approach, we just need to make the container engine multi-platform.