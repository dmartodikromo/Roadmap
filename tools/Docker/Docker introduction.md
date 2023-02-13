What are containers

-   A group of processes run in isolation(isolation is provided by a kernel feature called linux namespaces
	-   All processes must be able to run on the shared kernel
-    each container has its own set of namespaces(isolated view)
	-   PID - process ids
	-   USER - user and group ids
	-   UTS - hostname and domain name
	-   NS - mount points
	-   NET - network devices, stacks, ports
	-   IPC - inter-process communications, message queues
-   Cgroups
	-   Controls limits and monitoring of resources

Vms vs containers
![[Pasted image 20230210144655.png]]

What is docker

-   At its core, docker is tooling to manage containers
	-   Simplified existing technology to enable it for the masses
-   Enabled developers to use containers for their applications
	-   Package dependencies with containers "build once, run anywhere"

Why containers are appealing to users

-   No more "works on my machine"
-   Lightweight and fast
-   Better resource utilization
	-   Can fit more containers than vms
-   Standard developer to operations interface
-   Ecosystem and tooling
- 
Namespaces are a feature of the Linux kernel. However, Docker allows you to run containers on Windows and Mac. The secret is that embedded in the Docker product is a Linux subsystem. Docker open-sourced this Linux subsystem to a new project: LinuxKit. Being able to run containers on many different platforms is one advantage of using the Docker tooling with containers.

In addition to running Linux containers on Windows by using a Linux subsystem, native Windows containers are now possible because of the creation of container primitives on the Windows operating system. Native Windows containers can be run on Windows 10 or Windows Server 2016 or later.

get the ID of the running container that you just created:

docker container ls

Use that container ID to run bash inside that container by using the docker container exec command. Because you are using bash and want to interact with this container from your terminal, use the -it flag to run using interactive mode while allocating a psuedo-terminal:

```docker
$ docker container exec -it <containerid> bash
```

root@[containeri]d:/#

You just used the docker container exec command to enter the container's namespaces with the bash process. Using docker container exec with bash is a common way to inspect a Docker container.

The --detach flag will run this container in the background. The publish flag publishes port 80 in the container (the default port for NGINX) by using port 8080 on your host. Remember that the NET namespace gives processes of the container their own network stack. The --publish flag is a feature that can expose networking through the container onto the host.

You are also specifying the --name flag, which names the container. Every container has a name. If you don't specify one, Docker will randomly assign one for you. Specifying your own name makes it easier to run subsequent commands on your container because you can reference the name instead of the id of the container. For example, you can specify docker container inspect nginx instead of docker container inspect 5e1.

For more information on these running containers, use the docker container inspect [container id] command.

Containers are self-contained and isolated, which means you can avoid potential conflicts between containers with different system or runtime dependencies. For example, you  can deploy an app that uses Java 7 and another app that uses Java 8 on the same host. Or you can run multiple NGINX containers that all have port 80 as their default listening ports. (If you're exposing on the host by using the --publish flag, the ports selected for the host must be unique.) Isolation benefits are possible because of Linux namespaces.

Removing containers

Stop the containers by running this command for each container in the list:
```cmd
$ docker container stop [container id]
```

You can also use the names of the containers that you specified before:
```cmd
$ docker container stop d67 ead af5
d67
ead
af5
```

Remove the stopped containers. The following command removes any stopped containers, unused volumes and networks, and dangling images:

```cmd
$ docker system prune
```

-   Containers are composed of Linux namespaces and control groups that provide isolation from other containers and the host.
-   Because of the isolation properties of containers, you can schedule many containers on a single host without worrying about conflicting dependencies. This makes it easier to run multiple containers on a single host: using all resources allocated to that host and ultimately saving server costs.
-   That you should avoid using unverified content from the Docker Store when developing your own images because these images might contain security vulnerabilities or possibly even malicious software.
-   Containers include everything they need to run the processes within them, so you don't need to install additional dependencies on the host.

LAB 2: Add CI/CD value with docker images

Docker images
![[Pasted image 20230210150007.png]]

-   Tar file containing a container's filesystem and metadata
-   For sharing and distribution

Docker registry
![[Pasted image 20230210150050.png]]

-   Push and pull images from registry
-   Default registry: docker hub
	-   Public and free for public images
	-   Many pre-packaged images available
-   Private registry
	-   Self host or cloud provider options

Creating a dcoker image with docker build
-   Create a dockerfile
	-   List of instructions for how to construct the container
-   Run  `docker build -f Dockerfile

Common docker cli commands:

-   build
	-   Creates container images
	-   Requires Dockerfile
	-   Tags, or names, images
-   tag
	-   Names images
	-   Doesn’t overwrite existing images
	-   creates new tag that points to that image
-   images
	-   Lists all images, their repos and tags and their size
-   run
	-   Run containers
	-   Suited for testing an image that has been built
-   push and pull
	-   Stores images and retrieces images from a remote location

Dockerfile instruction

Any valid dockerfile must first begin with a FROM instruction, which initializes a new build stage and specifies the base image that subsequent instructions will build upon

-   FROM
	-   Define base image
	-   Base image often from a public repo like an OS or language
-   RUN
	-   Executes arbitrary commands
-   ENV
	-   Set environment variables
-   ADD and COPY
	-   Copy files and directories
	-   COPY -> can only copy local files or directories
	-   ADD -> can also add files from local repos
-   CMD
	-   Define default command for container executions
	-   Only one CMD instruction in a Dockerfile
	-   Main purpose is to provide default for executing your container. Defined the executable that should run in your container

example
```Dockerfile
FROM ubuntu
ADD myapp/
EXPOSE 80
ENTRYPOINT /myapp
```

Docker image layers
![[Pasted image 20230210150541.png]]
![[Pasted image 20230210150550.png]]

-   Union file system
	-   Merge image layers into single file system for each container
-   Copy-on-write
	-   Copies files that are edited up to top writable layer
		-   Keeps underlying images. Allows to reuse layers which saves a lot of space

Advantages

-   More containers per host
-   Faster startup and download time -  base layers are cached