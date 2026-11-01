What is a container ?
A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.


<img width="1662" height="718" alt="217262726-7cabcb5b-074d-45cc-950e-84f7119e7162" src="https://github.com/user-attachments/assets/521779fd-85c3-472c-83ad-4e49abf5e6ae" />


Why are containers light weight ?

Containers are lightweight because they use a technology called containerization, which allows them to share the host operating system's kernel and libraries, while still providing isolation for the application and its dependencies. This results in a smaller footprint compared to traditional virtual machines, as the containers do not need to include a full operating system. Additionally, Docker containers are designed to be minimal, only including what is necessary for the application to run, further reducing their size.

Let's try to understand this with an example:

Below is the screenshot of official ubuntu base image which you can use for your container. It's just ~ 22 MB, isn't it very small ? on a contrary if you look at official ubuntu VM image it will be close to ~ 2.3 GB. So the container base image is almost 100 times less than VM image.

It's important to note that while a container uses resources from the host operating system, it is still isolated from the host and other containers, so changes to the container do not affect the host or other containers.

Note: There are multiple ways to reduce your VM image size as well, but I am just talking about the default for easy comparision and understanding.

so, in a nutshell, container base images are typically smaller compared to VM images because they are designed to be minimalist and only contain the necessary components for running a specific application or service. VMs, on the other hand, emulate an entire operating system, including all its libraries, utilities, and system files, resulting in a much larger size.

What is Docker ?

Docker is a containerization platform that provides easy way to containerize your applications, which means, using Docker you can build container images, run the images to create containers and also push these containers to container regestries such as DockerHub, Quay.io and so on.

In simple words, you can understand as containerization is a concept or technology and Docker Implements Containerization.

Docker Architecture ?

<img width="1009" height="527" alt="217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622" src="https://github.com/user-attachments/assets/317b37ab-bfa5-4810-9688-0c538976c1e6" />

The above picture, clearly indicates that Docker Deamon is brain of Docker. If Docker Deamon is killed, stops working for some reasons, Docker is brain dead :p (sarcasm intended).

Docker LifeCycle
We can use the above Image as reference to understand the lifecycle of Docker.

There are three important things,

docker build -> builds docker images from Dockerfile
docker run -> runs container from docker images
docker push -> push the container image to public/private regestries to share the docker images.

<img width="1402" height="372" alt="217511949-81f897b2-70ee-41d1-b229-38d0572c54c7" src="https://github.com/user-attachments/assets/568a4812-bf34-4959-ba71-90712a114c20" />

Understanding the terminology (Inspired from Docker Docs)


Docker daemon
The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

Docker client
The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

Docker Desktop
Docker Desktop is an easy-to-install application for your Mac, Windows or Linux environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. For more information, see Docker Desktop.

Docker registries
A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry. Docker objects

When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.

Dockerfile
Dockerfile is a file where you provide the steps to build your Docker Image.

Images
An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

INSTALL DOCKER
A very detailed instructions to install Docker are provide in the below link

https://docs.docker.com/get-docker/

For Demo,

You can create an Ubuntu EC2 Instance on AWS and run the below commands to install docker.

sudo apt update
sudo apt install docker.io -y

Start Docker and Grant Access
A very common mistake that many beginners do is, After they install docker using the sudo access, they miss the step to Start the Docker daemon and grant acess to the user they want to use to interact with docker and run docker commands.

Always ensure the docker daemon is up and running.

A easy way to verify your Docker installation is by running the below command.

Start Docker daemon
sudo systemctl status docker
sudo systemctl start docker
Grant Access to your user to run docker commands
sudo usermod -aG docker ubuntu


https://docs.docker.com/get-started/docker_cheatsheet.pdf



