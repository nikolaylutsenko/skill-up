---
tags:
  - notes
  - clean
  - architecture
---
#### What it is
is a suggestion how to split the code into components

![[Pasted image 20241220125921.png]]
Presentation -> Application -> Domain
Infrastructure -> Application -> Domain
##### Presentation
is all about interacting with the user, handle how information is displayed to users

##### Application
is orchestrate use cases, is where use cases laid

##### Domain
is everything about business logic