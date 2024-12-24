---
tags:
  - aspire
---
# Prerequisites
- .NET 8/ .NET 9
- Docker/Podman
- VS 2022/ VS Code + C# Dev Kit extension

# Understand the .NET Aspire solution structure

The solution consists of the following projects:

- **AspireSample.ApiService**: An ASP.NET Core Minimal API project is used to provide data to the front end. This project depends on the shared **AspireSample.ServiceDefaults** project.
- **AspireSample.AppHost**: An orchestrator project designed to connect and configure the different projects and services of your app. The orchestrator should be set as the _Startup project_, and it depends on the **AspireSample.ApiService** and **AspireSample.Web** projects.
- **AspireSample.ServiceDefaults**: A .NET Aspire shared project to manage configurations that are reused across the projects in your solution related to [resilience](https://learn.microsoft.com/en-us/dotnet/core/resilience/http-resilience), [service discovery](https://learn.microsoft.com/en-us/dotnet/aspire/service-discovery/overview), and [telemetry](https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/telemetry).
- **AspireSample.Web**: An ASP.NET Core Blazor App project with default .NET Aspire service configurations, this project depends on the **AspireSample.ServiceDefaults** project. For more information, see [.NET Aspire service defaults](https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/service-defaults).

Your _AspireSample_ directory should resemble the following structure:

DirectoryCopy

```
└───📂 AspireSample
     ├───📂 AspireSample.ApiService
     │    ├───📂 Properties
     │    │    └─── launchSettings.json
     │    ├─── appsettings.Development.json
     │    ├─── appsettings.json
     │    ├─── AspireSample.ApiService.csproj
     │    └─── Program.cs
     ├───📂 AspireSample.AppHost
     │    ├───📂 Properties
     │    │    └─── launchSettings.json
     │    ├─── appsettings.Development.json
     │    ├─── appsettings.json
     │    ├─── AspireSample.AppHost.csproj
     │    └─── Program.cs
     ├───📂 AspireSample.ServiceDefaults
     │    ├─── AspireSample.ServiceDefaults.csproj
     │    └─── Extensions.cs
     ├───📂 AspireSample.Web
     │    ├───📂 Components
     │    │    ├───📂 Layout
     │    │    │    ├─── MainLayout.razor
     │    │    │    ├─── MainLayout.razor.css
     │    │    │    ├─── NavMenu.razor
     │    │    │    └─── NavMenu.razor.css
     │    │    ├───📂 Pages
     │    │    │    ├─── Counter.razor
     │    │    │    ├─── Error.razor
     │    │    │    ├─── Home.razor
     │    │    │    └─── Weather.razor
     │    │    ├─── _Imports.razor
     │    │    ├─── App.razor
     │    │    └─── Routes.razor
     │    ├───📂 Properties
     │    │    └─── launchSettings.json
     │    ├───📂 wwwroot
     │    │    ├───📂 bootstrap
     │    │    │    ├─── bootstrap.min.css
     │    │    │    └─── bootstrap.min.css.map
     │    │    ├─── app.css
     │    │    └─── favicon.png
     │    ├─── appsettings.Development.json
     │    ├─── appsettings.json
     │    ├─── AspireSample.Web.csproj
     │    ├─── Program.cs
     │    └─── WeatherApiClient.cs
     └─── AspireSample.sln
```

[](https://learn.microsoft.com/en-us/dotnet/aspire/get-started/build-your-first-aspire-app?pivots=vscode#explore-the-starter-projects)

# AppHost project
The _*.AppHost_ project is responsible for acting as the orchestrator

# ServiceDefaults project
The _*.ServiceDefaults_ project is a shared project that's used to manage configurations that are reused across the projects in your solution. This project ensures that all dependent services share the same resilience, service discovery, and OpenTelemetry configuration.

To help visualize the relationship between the app host project and the resources it describes, consider the following diagram:
![[Pasted image 20241224135855.png]]

## Built-in resource types

.NET Aspire projects are made up of a set of resources. The primary base resource types in the [📦 Aspire.Hosting.AppHost](https://www.nuget.org/packages/Aspire.Hosting.AppHost) NuGet package are described in the following table:

Expand table

|Method|Resource type|Description|
|---|---|---|
|[AddProject](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.projectresourcebuilderextensions.addproject)|[ProjectResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.projectresource)|A .NET project, for example, an ASP.NET Core web app.|
|[AddContainer](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.containerresourcebuilderextensions.addcontainer)|[ContainerResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.containerresource)|A container image, such as a Docker image.|
|[AddExecutable](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.executableresourcebuilderextensions.addexecutable)|[ExecutableResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.executableresource)|An executable file, such as a [Node.js app](https://learn.microsoft.com/en-us/dotnet/aspire/get-started/build-aspire-apps-with-nodejs).|
|[AddParameter](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.parameterresourcebuilderextensions.addparameter)|[ParameterResource](https://learn.microsoft.com/en-us/dotnet/api/aspire.hosting.applicationmodel.parameterresource)|A parameter resource that can be used to [express external parameters](https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/external-parameters).|

Project resources represent .NET projects that are part of the app model. When you add a project reference to the app