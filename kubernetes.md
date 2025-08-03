# Kubernetes and Docker Overview

k8's was build by google.

it is an opensource project and is one of the best container orchestration technology.

## Containers

The most popular container technology out there that is Docker.

### Why docker and what will it do ?

Imagine you've developed an application on macOS using various technologies—such as a web server built with Node.js, a MongoDB database, a messaging system like Redis, and an orchestration tool like Ansible. Now, you want your team to test this application.

You hand it over to a teammate who's using Windows OS. For them to run the application, they would need to manually install and configure all the required environments and dependencies. This includes setting up Node.js, MongoDB, Redis, and ensuring Ansible (which may not be fully compatible with Windows) works correctly.

Here’s where the problems begin:

1. Some services or tools may not be fully compatible with Windows, requiring additional configuration or even replacement.

2. They must ensure that every service and library is correctly installed and performs as expected on their system.

3. If any part of the setup fails—due to OS differences, missing dependencies, or configuration errors—you’ll have to troubleshoot and fix the issues specifically for that environment.

On top of that, you’ll need to provide detailed setup instructions to each team member. And if you want others to test the application later, they’ll have to repeat this entire process on their own machines. All of this is time-consuming, error-prone, and inefficient.

Docker allows you to package your entire application—along with all its dependencies, services, and configurations—into lightweight, portable containers.

These containers run consistently across any environment, whether it's macOS, Windows, or Linux. With Docker, your teammates don't need to worry about setting up or configuring anything manually.

They simply run the container, and the application works exactly as it does on your machine.

In short, Docker eliminates the "it works on my machine" problem, streamlines development and testing, and ensures consistency across all environments.


OS kernel and OS  ?
kernel : The kernel is the core part of an operating system that talks directly to the hardware (CPU, memory, etc.).

All the systems share the same OS kernel , it the software on the top of the kernel that differentiate the operating system.

But docker share the same kernel what does this mean ?

Docker does not run a full operating system like a virtual machine does.

Instead, it shares the host system’s kernel and just adds the libraries and files needed for your app.

So if you're using Docker on Linux, all containers running on that Docker engine must also use the Linux kernel — even if they look like Ubuntu, Alpine, or Debian, they’re all based on Linux underneath.

Docker can run different types of Linux-based OS environments (like Ubuntu, Debian, Alpine), but not Windows-based containers unless the Docker host is running Windows.

What are Containers ?

K8's is built to orchestrate the containers.

**Containers are Portable**: Containers include everything needed to run an app: code, dependencies, runtime, config. Build once and run anywhere dont worry about os.

**Containers are Isolate**: Containers isolate our app and its environment. Prevents apps from interfering with each other.Multiple apps can run on same node without conflict , no need of worrying .

**Containers are lightweight and Fast**: Start up in milliseconds . use less memory and cpu as they share same kernel. K8's use this efficiency to scale up and down quickly.

**Containers are consistent**: K8s uses this consistency to automate deployments, rollbacks, and upgrades confidently.

## Containers and Virtual Machines

### Architecture Comparison

- **Containers Architecture**: containers <---- docker <----- operating system <------- hardware
- **VM Architecture**: Virtual machine <------ Hypervisor < ----- operating system <------ hardware

Each virtual machine has its own OS inside it, and then the dependencies and then the application.

So the overhead causes high utilization of underlying resources as they are multiple virtual OS and kernels as a result they consume much space and memory as each vm is in Gigabytes.

Where as docker containers are lightweight and are MB in size . This helps to boost them fast

Docker has less isolation when compared to Virtual Machines.

### Comparison Table

| Aspect | Containers | Virtual Machines (VMs) |
|--------|------------|------------------------|
| Isolation | Process-level | Full OS-level (hardware isolation) |
| Kernel | Shared with host | Own kernel per VM |
| Boot time | Seconds (very fast) | Minutes (slower) |
| Size | Lightweight (MBs) | Heavy (GBs) |
| Performance | as fast as host machine | Some overhead |
| Use case | Microservices, CI/CD, | Full OS, security-critical apps |
| Security | Weaker (shares kernel) | Stronger (isolated OS) |

## Images and Containers

Image is a package that has all the info and files about our application.

Containers are running instance of an image

## Container Orchestration

Process of automatically deploying and managing containers are called as container orchestration.

### Advantages of container orchestration

- High availability because we deploy many instances . Even if one hardware fail the other instances in other hardware will be up.
- User traffic is balanced across different containers

Different container orchestration docker has it tool swarn , kubernetes from google and Mesos for apache .

Top ranked projects in github is Kubernetes.

