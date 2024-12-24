---
tags:
  - aspire
---
### Connection string and endpoint references

It's common to express dependencies between project resources. Consider the following example code:

C#Copy

```
var builder = DistributedApplication.CreateBuilder(args);

var cache = builder.AddRedis("cache");

var apiservice = builder.AddProject<Projects.AspireApp_ApiService>("apiservice");

builder.AddProject<Projects.AspireApp_Web>("webfrontend")
       .WithReference(cache)
       .WithReference(apiservice);
```

Project-to-project references are handled differently than resources that have well-defined connection strings. Instead of connection string being injected into the "webfrontend" resource, environment variables to support service discovery are injected.

Expand table

|Method|Environment variable|
|---|---|
|`WithReference(cache)`|`ConnectionStrings__cache="localhost:62354"`|
|`WithReference(apiservice)`|`services__apiservice__http__0="http://localhost:5455"`  <br>`services__apiservice__https__0="https://localhost:7356"`|

Adding a reference to the "apiservice" project results in service discovery environment variables being added to the frontend. This is because typically, project-to-project communication occurs over HTTP/gRPC. For more information, see [.NET Aspire service discovery](https://learn.microsoft.com/en-us/dotnet/aspire/service-discovery/overview).

To get specific endpoints from a [ContainerResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.containerresource) or an [ExecutableResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.executableresource), use one of the following endpoint APIs:

- [WithEndpoint](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.resourcebuilderextensions.withendpoint)
- [WithHttpEndpoint](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.resourcebuilderextensions.withhttpendpoint)
- [WithHttpsEndpoint](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.resourcebuilderextensions.withhttpsendpoint)

Then call the [GetEndpoint](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.resourcebuilderextensions.getendpoint) API to get the endpoint which can be used to reference the endpoint in the `WithReference` method:

C#Copy

```
var builder = DistributedApplication.CreateBuilder(args);

var customContainer = builder.AddContainer("myapp", "mycustomcontainer")
                             .WithHttpEndpoint(port: 9043, name: "endpoint");

var endpoint = customContainer.GetEndpoint("endpoint");

var apiservice = builder.AddProject<Projects.AspireApp_ApiService>("apiservice")
                        .WithReference(endpoint);
```

Expand table

|Method|Environment variable|
|---|---|
|`WithReference(endpoint)`|`services__myapp__endpoint__0=https://localhost:9043`|

The `port` parameter is the port that the container is listening on. For more information on container ports, see [Container ports](https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/networking-overview#container-ports). For more information on service discovery, see [.NET Aspire service discovery](https://learn.microsoft.com/en-us/dotnet/aspire/service-discovery/overview).