---
tags:
  - open-api
---
In .NET 9 Swagger was removed from project defaults, probably it was because of no longer updates in repository but still there is no Swagger

but OpenAPI support stays and if you go on:
```url
https:localhost.port/openapi/v1.json
```

you'll receive json object with specification

```json
{
  "openapi": "3.0.1",
  "info": {
    "title": "CacheApp.Server | v1",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "https://localhost:53037"
    },
    {
      "url": "http://localhost:53038"
    }
  ],
  "paths": {
    "/WeatherForecast": {
      "get": {
        "tags": [
          "WeatherForecast"
        ],
        "operationId": "GetWeatherForecast",
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "text/plain": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/WeatherForecast"
                  }
                }
              },
              "application/json": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/WeatherForecast"
                  }
                }
              },
              "text/json": {
                "schema": {
                  "type": "array",
                  "items": {
                    "$ref": "#/components/schemas/WeatherForecast"
                  }
                }
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "WeatherForecast": {
        "type": "object",
        "properties": {
          "date": {
            "type": "string",
            "format": "date"
          },
          "temperatureC": {
            "type": "integer",
            "format": "int32"
          },
          "temperatureF": {
            "type": "integer",
            "format": "int32"
          },
          "summary": {
            "type": "string",
            "nullable": true
          }
        }
      }
    }
  },
  "tags": [
    {
      "name": "WeatherForecast"
    }
  ]
}
```

### Swagger alternative
Nick Chapsas suggest to use `Scalar` [source](https://youtu.be/8yI4gD1HruY)
- add package to project
````shell
dotnet add package Scalar.AspNetCore
````

- add app.MapScalarApiReference()
```c#
// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
    app.MapScalarApiReference(options =>
    {
        options
            .WithTitle("CacheApp API")
            .WithTheme(ScalarTheme.Mars)
            .WithDefaultHttpClient(ScalarTarget.CSharp, ScalarClient.HttpClient);
    });
}
```

there is a lot of customization, you can find api here [source](https://guides.scalar.com/scalar/scalar-api-references/net-integration)

#### Issue with Aspire
openapi has wrong ip addresses, it solves with overriding Servers = [] property
```c#
    app.MapScalarApiReference(o =>
    {
        o.Servers = []; // this workaround is a bug solving
        o.WithTitle("CacheApp API");
        o.WithTheme(ScalarTheme.Mars);
    });
```
