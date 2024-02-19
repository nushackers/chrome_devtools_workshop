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
download: true
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

Hi I'm **Chun Yu**! My GitHub is: https://github.com/gunbux/

* I'm a Y3 CS undergraduate that enjoys hacking and building systems
* I play the violin (sometimes)

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
* Concept 3: Connecting Volumes and Networks
* Concept 4: Writing your own Dockerfile
* Concept 5: Connecting Containers with Docker Compose

::right::

## What we **won't** cover

* Advanced Docker Concepts
* Orchestration tools like Kubernetes or Ansible
* Docker as a secure development environment

---
layout: center
---

## What is Docker?

Docker is a piece of software that allows us to run **applications in isolated environments known as containers.**

---
layout: center
---

## Why do we need Docker?

Consider an application that requires a **certain version of Node, or Python** to run a certain application.

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
class: px-5 self-center
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

* Docker Images are **read-only templates or blueprints** for containers
* You can think of it like a published recipe for a cake.
    * You can't modify the recipe because it has been published
    * You don't actually make the cake

::right::

# Containers

* Containers are **runnable instances** of images
* With the same example, you can think of it as making a cake with the recipe.
    * You are executing the sequence of steps in the recipe to make this cake

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

This is because `docker run` is actually a **combination of actions**:

1. Check if we have the image
2. If we do not have the image locally, run `docker pull` to get the image (Think of it like installing an executable)
3. Run `docker run` on the installed image (Think of it like running the executable)

---
layout: two-cols
class: px-5 self-center
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
layout: center
---

We've already seen different *modes* to run a docker container. There are a few ways you can run a docker container:

- Default without flags: this will run the docker container with your terminal attached to the container.
- Interactive: Launch a program from the docker container
- Detached: Running `docker run` with a `-d` flag will **detach** the container from your terminal.
    - How do we check the logs for detached processes?

---
layout: center
---

# Let's try it out!

```bash
docker run prakhar1989/static-site // Default
docker run --rm -it prakhar1989/static-site // Interactive
docker run -d -P --name static-site prakhar1989/static-site // Detached
```

* `--rm`: remove the container when it exits
* `--name`: give the container a name
* `-P`: publish any open ports of the container to a random port on our host machine

---
layout: center
---

Now let’s check:

```jsx
docker port static-site // Notice we use the NAME of the container
```

Then, lets head to `localhost:<port>` to see our running website running in a docker container

---
layout: center
---

To stop a container:

```jsx
docker stop <container-name>
docker rm <container-name>
```

---
layout: quote
---

Why are there two commands? Shouldn’t they do the same thing?

> `docker stop` only stops the container (think of it like pausing the application), but the state is still saved (an exited program stored in memory still). You can verify this by doing `docker ps -a`. `docker rm` will then remove this from ‘memory’

---
layout: center
---

To remove an image:

```bash
docker rmi <image_name>
```

---
layout: two-cols
class: self-center px-2
---

## Summary

```bash
// Test out if docker is working
docker run hello-world

// Emulating an ubuntu environment
docker run -it ubuntu /bin/bash

// Running different versions of the same application
docker run -it python:3.8 python
docker run -it python:2.7 python

// View running containers
docker ps
docker ps -a

```

::right::

```bash
// Different ways to run a container
docker run prakhar1989/static-site
docker run --rm -it prakhar1989/static-site
docker run -d -P --name static-site prakhar1989/static-site

// Finding published ports
docker port static-site

// Stopping and removing a container
docker stop <container-name>
docker rm <container-name>

// Removing an image
docker rmi <image-name>
```

---
layout: cover
background: none
---

# Concept 2: Docker Hub

---
layout: two-cols
class: py-30 px-5
---

## Docker Hub

The **Docker Hub** is a central repository of images we can use.

To view the Docker Hub, go to [hub.docker.com](hub.docker.com)

::right::

<img src="/docker_hub.png" class="mx-30 h-50" />

---
layout: two-cols
class: py-20 px-10
---

Whenever we pull an ubuntu or python image, we’re getting the image from the docker hub. So when I do a command like:

```bash
docker pull/docker run <image-name>
```

Docker will search the docker registry for any images that matches that name.

::right::

There are two main naming conventions for images:

* Official Images
    * `python`, `ubuntu`, `nginx`
* Community Images (Not the actual name for these)
    * These are named `<username>/<image-tag>`

---
layout: two-cols
class: py-30 px-10
---

Let's take a look at the python image on the dockerhub:

https://hub.docker.com/_/python

::right::

What is the difference between different versions?

```bash
docker run -it python:3.8 python
docker run -it python:3.8-slim python
docker run -it python:3.8-alpine python

docker images // Use this command to check!
```

---
layout: two-cols
class: py-30
---

Look at the tabs page of the docker hub:

https://hub.docker.com/_/python/tags

Notice how there are different architectures being built for the docker image?

::right::

> By default, Docker will always try to find and use the architecture native to your machine.
>
> This might not be the best since there might be slight differences between your native architecture (M1 Mac) vs where you want to run your program (x86).
>
> To manually configure this, use `--platform`

```bash
docker run --platform linux/amd64 python:3.13
docker run --platform linux/arm64 python:3.13
```

---
layout: center
---

Let's explore some fun docker images we can find on docker hub!

```bash
docker run xer0x/spaceinvaders // Space Invaders on your terminal!
docker run -it spkane/starwars:latest // Watch Star Wars on your terminal
```

---
layout: center
---

## Summary

```bash
// Pull a docker image
docker pull/docker run <image-name>

// Different image tags
docker run -it python:3.8 python
docker run -it python:3.8-slim python
docker run -it python:3.8-alpine python

// See instaalled images
docker images

// Specifying specific architecture
docker run --platform linux/amd64 python:3.13

// Fun Docker Images
docker run xer0x/spaceinvaders
docker run -it spkane/starwars:latest
```

---
layout: cover
background: none
---

# Concept 3: Volumes and Networks
What if we have more complex docker images, that download a file, or needs to be exposed to a network?

---
layout: center
---

# Volumes

Volumes are basically how you share storage between the host and the container. There are two ways we can do this, either when building the image or when running the image.

We can map volumes with the following flag in our `docker run`:

```bash
-v <host directory location>:<docker directory location>
```

---
layout: center
---

# Exercise

Here's a really cool docker container that allows us to download youtube videos with a UI.

```bash
docker run -d -p 8081:8081 -v <fill in the blanks here> ghcr.io/alexta69/metube
```

- `-v`: `<host location to map>:<location inside the container>`
- `-p`: we'll find out soon!
- [ghcr.io](http://ghcr.io) : github’s version of the docker hub

---
layout: center
---

## Networking Ports

Now you may notice that we like to pass in a `-p` or a `-P` argument in a lot of the examples, and we have kind of glossed through what it does.

When you think about how your computer connects to a website, it is establishing a connection to another computer somewhere in the world. But what you may not know is that it is also connected to a certain **port** of a computer in the world.

---
layout: center
---

This concept carries over in docker, where our containers have their own ports, and docker allows us to connect one of our host ports to one of the containers ports.

```bash
-p <host port of our machine>:<container's port>
```

`-P` is a special command where docker automatically tries to find ports used by the docker container and maps it to a random available port of your host machine

---
layout: center
---

If we look at our previous command:

```bash
docker run -d -p 8080:8081 -v ... ghcr.io/alexta69/metube
```

- `-p 8080:8081`: map the host port 8080 to our container port 8081

---
layout: center
---

# Exercise

Can you figure out how to map this Docker container such that we can use it?

```bash
// Sterling PDF:
docker run -d \
  -p <fill in the blanks here> \
  -e DOCKER_ENABLE_SECURITY=false \
  --name stirling-pdf \
  frooodle/s-pdf:latest
```

> This docker container uses the port `8080`

---
layout: center
---

# Break Time!

In the meantime, try out some of these cool docker containers!

- `themythologist/monkeytype`

```bash
docker run -p 5000:5000 -d themythologist/monkeytype:frontend-latest
```

- `code-server`

```bash
docker run -d \
  --name=code-server \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
	-P \
	lscr.io/linuxserver/code-server:latest
```

---
layout: cover
background: none
---

# Concept 4: Writing Dockerfiles

---
layout: center
---

# Dockerfiles

What if we want to create our own images? A Dockerfile is a simple text file that contains a list of commands that the Docker client calls while creating an image. It's a simple way to automate the image creation process.

---
layout: two-cols
class: self-center px-2
---

```bash {all|1|2|3|4|all}
FROM python:3
RUN pip3 install pycryptodome requests
COPY wasg-register.py /
ENTRYPOINT ["python3", "wasg-register.py"]
```

- `FROM` : Takes a base image
- `RUN` : Run a command
- `COPY` : Copy a file from our host to the container
- `ENTRYPOINT` : Command to start the ‘application’, this is equivalent to running `python3 wasg-register.py`

::right::

Here's a really cool python script that automates getting credentials for Wireless@SG without download the app.

https://github.com/zerotypic/wasg-register/blob/master/wasg-register.py

Unfortunately, it required us to install some dependencies for it to run, which makes it difficult to share the program without others.

We instead share a Dockerfile to build an image that can be used anywhere!

---
layout: center
---

### Building the Dockerfile into an image

```docker
docker build -t <name> .
docker run <name>
```

---
layout: two-cols
class: self-center px-2
---

```bash {all|4|6|10|all}
FROM golang
MAINTAINER Drew Miller <drew@joyent.com>

ENV GOPATH=/go

RUN go get -u github.com/asib/spaceinvaders && \
    cd $GOPATH/src/github.com/asib/spaceinvaders && \
    go build

CMD /go/bin/spaceinvaders
```

::right::

Here's another Dockerfile, this time it's the Dockerfile of the spaceinvader docker we played!


- `ENV` : Set environment variables
- `&& \` : Run multiple commands + continue to the next line
- `CMD` : A lot of people how to use this with entrypoint - officially you should “start” the application with `ENTRYPOINT` and pass commands to the program with `CMD`, but a lot of people also just start the docker application with `CMD`

---
layout: two-cols
class: self-center px-10
---

# Writing our own Dockerfile

Now let's try practicing writing our own Dockerfile!

We have a simple flask app ready to be deployed, get it here:

https://hckr.cc/docker-zip

> You might want to take a look at metube's Dockerfile and try and find out
> how they made things work: https://github.com/alexta69/metube/blob/master/Dockerfile
> Also look at the docs! https://docs.docker.com/engine/reference/builder/

::right::

Here's what we want to do:

1. Require python to run
2. Install the required python packages with `pip3 install --no-cache-dir -r requirements.txt`
3. Expose the port 5000 so that we can use it (Hint: use `EXPOSE <port>` to expose a port)
4. Run the command `python3 app.py` to start the application

---
layout: two-cols
class: self-center px-10
---

1. Require python to run
2. Install the required python packages with `pip3 install --no-cache-dir -r requirements.txt`
3. Expose the port 5000 so that we can use it (Hint: use `EXPOSE <port>` to expose a port)
4. Run the command `python3 app.py` to start the application

::right::

```bash {all|1|4|7|10,11|15|18}
FROM python:3.8

# copy all the files to the container
COPY . /app

# Set a working directory to /app
WORKDIR /app

# install dependencies
RUN pip install --no-cache-dir \
    -r requirements.txt

# define the port number
# the container should expose
EXPOSE 5000

# run the command
CMD ["python", "./app.py"]
```

---
layout: cover
background: none
---

# Concept 5: Docker Compose

---
layout: two-cols
class: self-center px-10
---

## The problem

We saw a really cool docker image just now:

https://github.com/linuxserver/docker-code-server

The problem? I don't want to type out or remember this command every time I want to start this container!

::right::

```bash
docker run -d \
  --name=code-server \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
	-p 8443:8443 \
	lscr.io/linuxserver/code-server:latest
```

---
layout: center
---

This is what Docker Compose aims to address, as well as a bunch of other different issues we have with plain docker.

- What if we want to run multiple containers together? I don’t want to copy and paste 10 different commands!
- What if I want the docker containers to communicate with each other? (We won’t cover this in too much detail, but it’s possible for this to work!)

---
layout: center
---

## docker-compose.yml

On top of our Dockerfile/images, docker compose aims to let us write in a `docker-compose.yml` how we want to run the docker containers,
and also allows us to spin up multiple containers at once!

---
layout: two-cols
class: self-center px-10
---

## Three main sections

There are three main sections to a docker-compose.yml:

1. Version - Use v3 latest kind of docker compose file
2. Services - Define your Docker containers
3. Define your docker volumes

::right::

```bash {all|1|2-20|21-23}
version: "3"
services:
  es:
    image: docker.elastic.co/elasticsearch/elasticsearch:6.3.2
    container_name: es
    environment:
      - discovery.type=single-node
    ports:
      - 9200:9200
    volumes:
      - esdata1:/usr/share/elasticsearch/data
  web:
    image: yourusername/foodtrucks-web
    command: python3 app.py
    depends_on:
      - es
    ports:
      - 5000:5000
    volumes:
      - ./flask-app:/opt/flask-app
volumes:
  esdata1:
    driver: local
```

---
layout: two-cols
class: self-center px-10
---

The services section contains:

- `image`: indicates the image to start the service with
- `command`: overrides the CMD in dockerfile
- `environment`: setting environment variables
- `ports`: carries out port forwarding
- `volumes`: can be bind mount or dedicated volume
- `depends_on`: tells docker the sequence to start the services

::right::

```bash {2-20|4|14|6,7|8-9,17-18|10-11,19-20|15-16}
version: "3"
services:
  es:
    image: docker.elastic.co/elasticsearch/elasticsearch:6.3.2
    container_name: es
    environment:
      - discovery.type=single-node
    ports:
      - 9200:9200
    volumes:
      - esdata1:/usr/share/elasticsearch/data
  web:
    image: yourusername/foodtrucks-web
    command: python3 app.py
    depends_on:
      - es
    ports:
      - 5000:5000
    volumes:
      - ./flask-app:/opt/flask-app
volumes:
  esdata1:
    driver: local
```

---
layout: two-cols
class: self-center px-10
---

## Exercise

Let's try rewriting this code-server docker command into a docker-compose.yml!

::right::

```bash
docker run -d \
  --name=code-server \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
	-P \
	lscr.io/linuxserver/code-server:latest
```

---
layout: center
---

```
version: 3.0
services:
  code-server:
    image: lscr.io/linuxserver/code-server:latest
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    ports:
      - 8443:8443
    restart: unless-stopped
```

---
layout: center
---

## Starting and stopping a docker compose

```docker
docker compose up
docker compose down
docker compose up -d --force-recreate
```

---
layout: two-cols
class: self-center px-3
---

Here's a partial docker-compose.yml:


```yml
services:
  website:
    build:
      context: .
      dockerfile: website/Dockerfile.dev
      args:
        - GIT_COMMIT_HASH
        - DATA_API_BASE_URL
    volumes:
      - ~/.cache/yarn:/home/node/.cache/yarn
      - ./website:/home/node/app/website
      - ./packages:/home/node/app/packages
      - ./.prettierrc.js:/home/node/app/.prettierrc.js
    expose:
      - 8080
      - 8081
    environment:
      - NODE_ENV=development
    user: ${CURRENT_UID:-1000:1000}
    restart: on-failure
```

::right::

- `build`: Instead of pulling an image from docker hub, build using a directory with a Dockerfile

---
layout: center
---

This is actually a portion of the `docker-compose.yml` used by **NUSMods**:

https://github.com/nusmodifications/nusmods/blob/master/docker-compose.yml

With this knowledge, you can probably deploy the entire NUSMods website locally using Docker Compose!

---
layout: center
---

## Looking at NUSMods
- Notice how we have three different services. This means that there are three docker containers required to run NUSMods locally
- `restart: on-failure` is another special feature of docker compose that allows us to automatically restart the container if something fails abruptly

---
layout: center
---

Let's try running it!

```bash
docker compose -f docker-compose.yml build
docker compose -f docker-compose.yml up
```

---
layout: center
---

## Pruning Images

Remember that docker images are similar to applications. In otherwords, these images take up space in your computer if you don't
clear them up. If you no longer need the docker images, besides doing `docker rmi`, you can clean your entire system of images by doing:

```
docker systems prune -a
```

---
layout: center
---

# And that's it!

---
layout: center
---

## Summary of key ideas

- **Docker** is a containerization platform for developing, shipping, and running applications.
- **Dockerfiles** are scripts containing commands to build Docker images.
- **Docker Compose** allows for defining and managing multi-container Docker applications via a simple YAML file.

---
layout: center
---

## Resources to explore:

- Docker Curriculum: https://docker-curriculum.com/
- Really cool docker compose files: https://github.com/Haxxnet/Compose-Examples
- Official Docker Cheatsheet: https://docs.docker.com/get-started/docker_cheatsheet.pdf

---
layout: center
---

## Feedback Form

Let us know your thoughts on this workshop!

<img src="/feedback.jpeg" class="m-10 h-60" />

---
layout: cover
background: none
---

# What's next?

