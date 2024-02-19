---
theme: seriph
class: text-center
background: none
highlighter: shikiji
lineNumbers: false
favicon: /quackers.png
info: |
  Hacker School 23/24 - Docker
drawings:
  persist: false
transition: fade
title: "Hackerschool: Docker"
mdc: true
fonts:
  sans: "Inter Tight"
  serif: "Inter Tight"
  mono: "Jetbrains Mono"
layout: center
---

# Hackerschool:

<img src="/docker-logo.png" class="m-20 h-60" />

---
layout: center
---

# Slides

[https://nushackers.github.io/docker_slides](https://nushackers.github.io/docker_slides)

![slides_qr](/slides_link.png)

---
layout: center
---

# Prerequisites

* Pre-installed docker (if you haven't installed, sound out now!)
    * Mac: https://docs.docker.com/desktop/install/mac-install/
    * Windows: https://docs.docker.com/desktop/install/windows-install/
    * Linux: https://docs.docker.com/desktop/install/linux-install/
* **Some** basic knowledge of the command line

---
layout: two-cols
class: mt-25
---

## What we **will** cover

* Motivations behind docker
* Concept 1: Docker basics and terminology
* Concept 2: The Docker Hub
* Concept 3: Writing your own Dockerfile
* Concept 4: Connecting Volumes and Networks
* Concept 5: Connecting **Containers** with Docker Compose

::right::

## What we **won't** cover

* Advanced Docker Concepts
* Orchestration tools like Kubernetes or Ansible
* Docker as a **secure** development environment

---
layout: center
---

## What is Docker?

Docker is a piece of software that allows us to run **applications in isolated environments known as containers.**

---
layout: center
---

## Why do we need Docker?

Consider an application that requires a certain version of **Node, or Python** to run a certain application.

- Well, what if you want to get a team to work on that project? That would mean that you would need a large amount of setup time to get them ready for development.
- What if you want to deploy your application to multiple servers in production?

---
layout: center
---

## Why do we need Docker?

You can think of Docker as a **box or package** which encapsulates everything your application needs to run.

In other words, we want to be able to write some configuration files to determine our environment/infrastructure we run our programs in.

---
layout: two-cols
class: px-5
---

## Why not use virtual machines?

Don't virtual machines kind of solve the problem docker aims to solve as well?

**Answer:** We can think of docker containers as computationally cheaper virtual machines.

::right::

See more here:

[https://www.cloudbees.com/blog/why-docker#docker-enables-consistent-environments](https://www.cloudbees.com/blog/why-docker#docker-enables-consistent-environments)

![why_docker_link](/why_docker_link.png)

---
layout: cover
background: none
---

# Concept 1: Images and Containers

---
layout: two-cols
class: px-5 py-20
---

# Images

* Docker Images are **read-only templates or blueprints** for *containers*
* You can think of it like a *published recipe for a cake*.
    * You can't *modify* the recipe because it has been published
    * You don't actually *make* the cake

::right::

# Containers

* Containers are **runnable instances** of *images*
* With the same example, you can think of it as *making a cake with the recipe*.
    * You are *executing* the sequence of steps in the recipe to make this cake

---
layout: image
image: /application.png
---

# An executable file vs a running program

---
layout: center
---

Now, lets check that docker is working on our machines:

```bash
docker run hello-world
```

---
layout: center
---

Let's very quickly dissect this command:
```bash
docker run hello-world
```

* `docker`: the main command line program we are running
* `run`: a subcommand that tells docker to run a program
* `hello-world`: the name of a special image we want to run

---
layout: center
---

## More examples

We can use this command to "emulate" an Ubuntu environment

```bash
docker run -it ubuntu /bin/bash
```

* `i`: interactive mode
* `t`: tty (you don't need to know too much, just run this every time you want to run interactively!)
* `/bin/bash`: the path to the **terminal command** you want to run

---
layout: center
---

We can use it to run different versions of python
```bash
docker run -it python:3.8 python
docker run -it python:2.7 python
```

---
layout: center
---

Notice how when we first call `docker run` on an image, we get this message:
```
Unable to find image <image-name> locally
```

---
layout: center
---

This is because `docker run` is actually a **combination** of actions:

1. Check if we have the image
2. If we do not have the image locally, run `docker pull` to get the image (Think of it like installing an executable)
3. Run `docker run` on the installed image (Think of it like running the executable)

---
layout: two-cols
class: px-5
---

# View running docker containers

To view the docker containers running at any point of time:
```bash
docker ps
```
We can use some flags to make the output more verbose:
```bash
docker ps -a
```

::right::

You can find out more about the different flags [here](https://docs.docker.com/engine/reference/commandline/container_ls/)!

![docker_ps](/docker_ps.png)

---
layout: cover
background: none
---

# Concept 2: Docker Hub

---
layout: cover
background: none
---

# Concept 3: Writing Dockerfiles

---
layout: cover
background: none
---

# Concept 4: Volumes and Networks

---
layout: cover
background: none
---

# Concept 5: Docker Compose

---
layout: cover
background: none
---

# What's next?

---
