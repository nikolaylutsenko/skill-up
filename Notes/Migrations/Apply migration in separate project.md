---
tags:
  - migrations
---
[source](https://learn.microsoft.com/en-us/dotnet/aspire/database/ef-core-migrations)

- create a separate service of type `worker`
- add reference to web api and database
- add aspire package
- add Service Defaults to builder in Program.cs
- modify worker to insure that db exists, applies migrations and seed data if needed
- add migration service to orchestator AppHost
- add script that will create migrations table
- add waiting to be sure that containers is up and running