---
tags:
  - aspire
---
## AddProject

## AddContaineer
o express a [ContainerResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.containerresource) you add it to an [IDistributedApplicationBuilder](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.idistributedapplicationbuilder) instance by calling the [AddContainer](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.containerresourcebuilderextensions.addcontainer) method:
```C#
var builder = DistributedApplication.CreateBuilder(args);

var ollama = builder.AddContainer("ollama", "ollama/ollama")
    .WithBindMount("ollama", "/root/.ollama")
    .WithBindMount("./ollamaconfig", "/usr/config")
    .WithHttpEndpoint(port: 11434, targetPort: 11434, name: "ollama")
    .WithEntrypoint("/usr/config/entrypoint.sh")
    .WithContainerRuntimeArgs("--gpus=all");
```
## AddExecutable

## AddParameter

## WithReference
A reference represents a dependency between resources is used to express dependencies between resources.
When one resource depends on another resource, the app host injects environment variables into the dependent resource. These environment variables configure the dependent resource to connect to the resource it depends on. The format of the environment variables is specific to .NET Aspire and expresses service endpoints in a way that is compatible with [Service Discovery](https://learn.microsoft.com/en-us/dotnet/aspire/service-discovery/overview).
Service endpoint environment variable names are prefixed with `services__` (double underscore), then the service name, the endpoint name, and finally the index. The index supports multiple endpoints for a single service, starting with `0` for the first endpoint and incrementing for each endpoint.

Consider the following environment variable examples:

EnvironmentCopy

```
services__apiservice__http__0
```

The preceding environment variable expresses the first HTTP endpoint for the `apiservice` service. The value of the environment variable is the URL of the service endpoint. A named endpoint might be expressed as follows:

EnvironmentCopy

```
services__apiservice__myendpoint__0
```

In the preceding example, the `apiservice` service has a named endpoint called `myendpoint`. The value of the environment variable is the URL of the service endpoint.
## WaitFor
waiting for another resource to start
## WithImageTag
clarify the image version, example "latest" or "7.4"

