---
tags:
  - aspire
---
#### Container resource lifetime

By default, container resources use the __session__ container lifetime. This means that every time the app host process is started, the container is created and started. When the app host stops, the container is stopped and removed. Container resources can opt-in to a _persistent_ lifetime to avoid unnecessary restarts and use persisted container state. To achieve this, chain a call the [ContainerResourceBuilderExtensions.WithLifetime](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.containerresourcebuilderextensions.withlifetime) API and pass [ContainerLifetime.Persistent](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.containerlifetime#aspire-hosting-applicationmodel-containerlifetime-persistent):

C#Copy

```
var builder = DistributedApplication.CreateBuilder(args);

var ollama = builder.AddContainer("ollama", "ollama/ollama")
    .WithLifetime(ContainerLifetime.Persistent);
```

The preceding code adds a container resource named "ollama" with the image "ollama/ollama" and a persistent lifetime.
