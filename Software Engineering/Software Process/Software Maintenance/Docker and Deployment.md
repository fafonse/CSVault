[[Scalability]] like this is ONLY possible if you have a quick way of deploying your solution.
People can't do this, you gotta *containerize* your code.

Docker is a containerization tool, you can instead make **images** of your applications and run them anywhere.
This is super useful for deployment and scalability, as you can transfer images without having to transfer code. It's also useful for sending indev builds to QA without fiddling with dependencies and code.

## Docker vs. VM
Virtual Machines are similar to Docker, but verrrryyy different.
Virtual machines load an entire operating system at a time, requiring a *hypervisor* program between that and the host OS. 
*Hypervisor* is a program that tricks the VM OS into thinking that it's running on bare metal. It started out as a separate program, but now we typically build it into the hardware to get more performance.
The apps are still specific to the OS though, and we're basically emulating and entire computer just for one program. Docker however replaces the hypervisor with a *container engine* instead. That *container engine* sandboxes the individual apps, giving them their own environment to fuck around. With this approach, we just need to make the container engine multi-platform.