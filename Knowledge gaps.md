---
tags:
  - gaps
---

# DDD
#### 1. Basics
# Advanced 'C#'
#### 1. LINQ
- Methods: `Select`, `Where`, `GroupBy`, `Join`, `Aggregate`, `Any`, `All`.  
- Projection: `SelectMany`.  
- Delegates and Expressions: Usage of `Func<T>` and `Expression<Func<T>>`.
#### 2. Async/Await and Task-Based Asynchronous Programming
- Features:  
  - Asynchronous programming with `async`/`await`.  
  - Use `ValueTask` for optimization.  
  - Work with `CancellationToken` to cancel operations.  
- Key Methods: `Task.WhenAll`, `Task.WhenAny`.
#### 3. `Span<T> and Memory<T>`
- What it is: Efficient memory operations without additional allocations.  
- Related Features: `ReadOnlySpan<T>, ReadOnlyMemory<T>` for immutable data operations.
#### 4. Records and Immutable Types
- Features:  
  - `record`: Automatic creation of immutable types with support for `with`-expressions.  
  - `init`: Initialization-only properties.
#### 5. Nullable Reference Types
- What it is: Nullability analysis to prevent `NullReferenceException`.  
- Keywords: `?`, `!` (null-forgiving operator).  
- Practice: Enable nullable analysis in projects (`<Nullable>enable</Nullable>` in `csproj`).
#### 6. Pattern Matching
- Features:  
  - `switch` expressions:
  - Property Patterns (`{ ... }`).  
  - Positional Patterns.
#### 7. Expression-Bodied Members
- What it is: Syntax sugar for methods, properties, constructors.  
#### 8. Local Functions
- What it is: Nested functions accessible only within another function.  
#### 9. Tuples
- What it is: Convenient grouping of values without creating separate classes.  
#### 10. Records vs Classes
- What it is: `record` for declarative data models.  
- Key Difference: Records have value semantics (value equality), while classes have reference semantics (reference equality).
#### 11. Reflection
- What it is: Dynamic interaction with types, methods, properties.  
#### 12. Attributes and Source Generators
- What it is: Metadata creation via attributes.  
- Source Generators: Code generation based on attributes or conditions.
#### 13. Unsafe Code and Pointers
- What it is: Work with unmanaged memory using `unsafe` and `fixed`.  
#### 14. Delegates, Events, and Func/Action/Predicate
- What it is:  
  - Delegates: Method references.  
  - Func/Action/Predicate: Standard delegates.  
  - Events: Mechanism for subscription and event handling.
#### 15. Dynamic and DLR (Dynamic Language Runtime)
- What it is: `dynamic` type for runtime method or property invocation.
#### 16. Multithreading
- What to Learn:  
  - `Parallel.For`, `Parallel.ForEach`.  
  - `lock`, `Monitor`, `Semaphore`.  
  - Thread Pool (`ThreadPool`).  
  - `AsyncLocal<T>` for context preservation.
#### 17. Source Generators
- What it is: Tool for automatic code generation during compilation.

# Advanced ASP.NET
# Beginner Angular
able to create CRUD operations
# Core patterns

#### Factory Method
Дозволяє створювати об'єкти з логікою, яка залежить від умов, що спрощує підтримку коду.

#### Builder
Дуже корисний для створення об'єктів з багатьма параметрами або складною логікою ініціалізації. Часто використовується при роботі з DTO.
#### Dependency Injection
Полегшує тестування (mocking), знижує зв'язність компонентів, забезпечує підтримку Inversion of Control (IoC). Більшість .NET-проєктів активно використовують DI-контейнери, такі як Microsoft.Extensions.DependencyInjection.
#### Strategy
Полегшує розширення та заміну логіки поведінки у програмах (наприклад, різні способи обробки даних).
#### Adapter
Полегшує інтеграцію сторонніх бібліотек або модулів у проєкти.
#### Observer
Корисний для реалізації систем з багатьма залежностями, наприклад, в UI або системах реального часу.
#### Command
Корисний для реалізації операцій, які можна відкласти, скасувати або журналювати.
#### Decorator
Дуже корисний для побудови розширюваних систем, наприклад, для створення гнучких логів чи кешування.
#### Mediator
Дозволяє зменшити зв'язність між компонентами системи, особливо корисний у системах, які мають складні зв'язки між об'єктами.
#### CQRS (Command Query Responsibility Segregation)
Забезпечує масштабованість та спрощує підтримку складних доменних моделей у .NET-проєктах.
#### Event Sourcing
Дозволяє відстежувати всі зміни в системі та легко відновлювати попередній стан. Корисний для складних бізнес-логік.

# HTTP protocol
http theory
# Networking
networking theory
# Database
#### Profiling, optimizing