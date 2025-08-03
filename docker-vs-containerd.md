# Docker, containerd & Kubernetes – Explained Simply

Docker made containers popular by offering an easy way to build, run, and manage them.

Kubernetes came later to orchestrate containers and was originally built to work only with Docker.

Over time, Kubernetes needed to support other container runtimes, not just Docker.

So Kubernetes introduced the Container Runtime Interface (CRI) — a standard way to talk to any container runtime.

The Open Container Initiative (OCI) defined how images and runtimes should behave (image spec + runtime spec).

Docker was not designed to support CRI, so Kubernetes used a temporary adapter called Dockershim to support it.

Maintaining Dockershim was hard, so in Kubernetes v1.24, it was removed, and Docker was no longer supported as a runtime in Kubernetes.

## Docker Components

Docker is more than a runtime — it includes:

- Docker CLI
- Docker API
- Build tools
- Security, volumes, networking features

## Docker Internal Components

Internally, Docker uses:

- **containerd** – manages container lifecycle
- **runc** – low-level tool to run containers

After Docker, containerd became its own project, now maintained independently and part of CNCF.

Kubernetes now directly supports containerd (and others like cri-o) through CRI.

## CLI Tools Overview

- **ctr**: Comes with containerd. Very limited. Debug-only.
- **nerdctl**: Docker-like CLI for containerd. Supports advanced features. Recommended for general use.
- **crictl**: From Kubernetes community. Talks to any CRI runtime. Best for debugging on Kubernetes nodes.

## Summary

Docker made containers popular, Kubernetes came after to orchestrate them.

Docker and Kubernetes were tightly coupled at first.

Now Kubernetes uses standard runtimes like containerd through CRI.

Docker still uses containerd under the hood.

## Usage Recommendations

Use:

- **nerdctl** instead of Docker for working with containerd
- **crictl** to debug containers in Kubernetes

## Docker Deprecation

Docker was the original and only supported container runtime for Kubernetes.

Kubernetes introduced the Container Runtime Interface (CRI) to support other runtimes.

Docker includes many components: CLI, API, build tools, volume management, security, runc, and containerd.

Kubernetes only needs the container runtime part, not the full Docker toolset.

containerd, which is part of Docker, can work directly with Kubernetes through CRI.

Kubernetes deprecated support for the full Docker runtime starting from version 1.24.

This deprecation means Kubernetes no longer uses Docker as its runtime, but Docker is not completely gone.

Docker is still widely used for building, testing, and running containers during development.

It remains the most popular container tool outside of Kubernetes.
