---
tags:
  - aspire
---
when the app host is run, the [ContainerResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.containerresource) is used to determine what container image to create and start. Under the hood, .NET Aspire runs the container using the defined container image by delegating calls to the appropriate OCI-compliant container runtime, either Docker or Podman.

First, the container is created using the `docker container create` command. Then, the container is started using the `docker container start` command.

- [docker container create](https://docs.docker.com/reference/cli/docker/container/create/): Creates a new container from the specified image, without starting it.
- [docker container start](https://docs.docker.com/reference/cli/docker/container/start/): Start one or more stopped containers.

These commands are used instead of `docker run` to manage attached container networks, volumes, and ports. Calling these commands in this order allows any IP (network configuration) to already be present at initial startup.