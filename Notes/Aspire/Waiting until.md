---
tags:
  - aspire
---
[source](https://systenics.ai/blog/2024-11-12-using-waitfor-and-waitforcompletion-in-dotnet-aspire-9/)

if your code is dependent on another resource we can add 
```
.WaitFor(resouce_name)
```
and it will wait until that resource will up and run

also if you need wait until another resource will finish it's work you can use
```
.WaitForConpletion(resource_name)
```

![[Pasted image 20241222181348.png]]