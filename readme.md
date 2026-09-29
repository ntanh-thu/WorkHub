# WorkHub — C# / .NET Learning Project

> **Goal:** Build a small internal company portal while learning the C# / .NET ecosystem and preparing for an ASP.NET Core / Umbraco project.

---

## 🎯 Project Goal

**WorkHub** is an internal company portal for managing:

* Employees
* Departments
* Announcements
* Company events
* Leave requests
* Documents

The main goal is **not** to build a perfect product.

The goal is to understand how a real .NET web application works from:

```text
Browser
   ↓
HTTP Request
   ↓
ASP.NET Core
   ↓
Controller
   ↓
Service
   ↓
Database
   ↓
Response
   ↓
Browser
```

---

# 🗺️ Tech Stack

## Backend

* [ ] C#
* [ ] .NET 10
* [ ] ASP.NET Core
* [ ] ASP.NET Core MVC
* [ ] ASP.NET Core Web API
* [ ] Razor
* [ ] Dependency Injection
* [ ] Middleware
* [ ] Authentication / Authorization
* [ ] JWT
* [ ] Swagger / OpenAPI

## Database

* [ ] SQL Server
* [ ] Entity Framework Core
* [ ] DbContext
* [ ] DbSet
* [ ] LINQ
* [ ] Migrations

## Testing

* [ ] xUnit
* [ ] Moq
* [ ] Unit Testing
* [ ] Integration Testing

## Tools

* [ ] Visual Studio / VS Code
* [ ] .NET CLI
* [ ] Git
* [ ] Postman / Swagger

---

# Phase 0 — Environment Setup

### Goal

Get a basic ASP.NET Core project running.

### Learn

* .NET SDK
* `dotnet` CLI
* `.csproj`
* `Program.cs`
* Project structure

### Tasks

* [ ] Install .NET SDK
* [ ] Create ASP.NET Core project
* [ ] Run project locally
* [ ] Understand `Program.cs`
* [ ] Understand `.csproj`
* [ ] Understand `appsettings.json`

### Commands

```bash
dotnet --version

dotnet new mvc -o WorkHub

cd WorkHub

dotnet run
```

### Definition of Done

* [ ] Application runs locally
* [ ] Can explain what `Program.cs` does
* [ ] Can explain what `.csproj` is
* [ ] Can create/run a project without a tutorial

---

# Phase 1 — C# Fundamentals

### Goal

Learn enough C# to understand real ASP.NET Core code.

### Topics

* [ ] Variables
* [ ] Types
* [ ] Classes
* [ ] Objects
* [ ] Properties
* [ ] Methods
* [ ] Constructors
* [ ] Interfaces
* [ ] Enums
* [ ] `List<T>`
* [ ] `Dictionary<TKey, TValue>`
* [ ] Nullable types
* [ ] Exception handling
* [ ] Generics
* [ ] `async`
* [ ] `await`
* [ ] `Task<T>`
* [ ] LINQ

### Important mental model

```text
Class
  ↓
Object
  ↓
Properties + Methods
```

```text
Interface
  ↓
Implementation
```

```text
async
  ↓
Task<T>
  ↓
await
  ↓
Result
```

### Definition of Done

* [ ] Can create a class
* [ ] Can create an interface
* [ ] Can implement an interface
* [ ] Can use `List<T>`
* [ ] Can write basic LINQ
* [ ] Can explain `Task<T>`
* [ ] Can explain `async/await`

---

# Phase 2 — ASP.NET Core Fundamentals

### Goal

Understand how an HTTP request travels through ASP.NET Core.

### Topics

* [ ] HTTP request
* [ ] HTTP response
* [ ] Routing
* [ ] Controller
* [ ] Action
* [ ] Model
* [ ] View
* [ ] Razor
* [ ] `IActionResult`
* [ ] `Program.cs`
* [ ] Middleware

### Request flow

```text
GET /employees
      ↓
ASP.NET Core
      ↓
Routing
      ↓
EmployeeController
      ↓
Action
      ↓
View / JSON
      ↓
Browser
```

### Build

Create:

```text
/employees
/employees/1
```

### Definition of Done

* [ ] Can create a Controller
* [ ] Can create an Action
* [ ] Can create a Razor View
* [ ] Understand routing
* [ ] Understand request → controller → response
* [ ] Can explain middleware at a high level

---

# Phase 3 — WorkHub Landing / Dashboard

### Goal

Build the first real UI.

### Pages

```text
/
├── Dashboard
├── Employees
├── Announcements
├── Events
└── Leave Requests
```

### Dashboard

```text
Welcome
    ↓
Announcements
    ↓
Upcoming Events
    ↓
Leave Balance
    ↓
Quick Actions
```

### Tasks

* [ ] Create layout
* [ ] Create navbar
* [ ] Create dashboard
* [ ] Create reusable Razor components/partials
* [ ] Add responsive CSS
* [ ] Add mock data

### Definition of Done

* [ ] Dashboard works
* [ ] Navigation works
* [ ] Data is rendered from C# models
* [ ] UI is responsive

---

# Phase 4 — Models & Data Flow

### Goal

Understand how C# models move through the application.

### Models

```text
Employee
Department
Announcement
Event
LeaveRequest
```

Example:

```csharp
public class Employee
{
    public int Id { get; set; }

    public string Name { get; set; }

    public string Email { get; set; }

    public int DepartmentId { get; set; }
}
```

### Data flow

```text
Model
  ↓
Controller
  ↓
ViewModel
  ↓
Razor
  ↓
HTML
```

### Learn

* [ ] Entity vs ViewModel
* [ ] Model binding
* [ ] DTO
* [ ] Validation
* [ ] Form submission

### Definition of Done

* [ ] Can create models
* [ ] Can pass models to views
* [ ] Can create forms
* [ ] Understand DTO vs Entity

---

# Phase 5 — REST API

### Goal

Build APIs with ASP.NET Core.

### Endpoints

```text
GET    /api/employees
GET    /api/employees/{id}

POST   /api/employees

PUT    /api/employees/{id}

DELETE /api/employees/{id}
```

### Learn

* [ ] REST
* [ ] HTTP methods
* [ ] Status codes
* [ ] JSON
* [ ] Controller API
* [ ] DTO
* [ ] Swagger

### Example

```http
GET /api/employees
```

```json
[
  {
    "id": 1,
    "name": "John",
    "email": "john@example.com"
  }
]
```

### Definition of Done

* [ ] CRUD API works
* [ ] Can test API with Swagger
* [ ] Understand HTTP status codes
* [ ] Understand JSON serialization

---

# Phase 6 — Service Layer & Dependency Injection

### Goal

Stop putting business logic inside Controllers.

### Architecture

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Database
```

### Example

```csharp
public interface IEmployeeService
{
    Task<List<Employee>> GetEmployees();
}
```

```csharp
public class EmployeeService : IEmployeeService
{
    public async Task<List<Employee>> GetEmployees()
    {
        // business logic
    }
}
```

### Learn

* [ ] Dependency Injection
* [ ] Interface
* [ ] Service
* [ ] Repository
* [ ] Lifetime

  * [ ] Singleton
  * [ ] Scoped
  * [ ] Transient

### Definition of Done

* [ ] Controller doesn't contain business logic
* [ ] Understand DI
* [ ] Can register a service in `Program.cs`
* [ ] Understand why interfaces are used

---

# Phase 7 — SQL Server + Entity Framework Core

### Goal

Replace mock data with a real database.

### Stack

```text
ASP.NET Core
      ↓
EF Core
      ↓
SQL Server
```

### Learn

* [ ] Database
* [ ] Table
* [ ] Primary key
* [ ] Foreign key
* [ ] Relationship
* [ ] DbContext
* [ ] DbSet
* [ ] LINQ
* [ ] Migration
* [ ] `ToListAsync`
* [ ] `FirstOrDefaultAsync`
* [ ] `Include`

### Example

```csharp
var employees = await _context.Employees
    .Include(x => x.Department)
    .Where(x => x.IsActive)
    .OrderBy(x => x.Name)
    .ToListAsync();
```

### Definition of Done

* [ ] SQL Server connected
* [ ] EF Core configured
* [ ] Database created
* [ ] Migration works
* [ ] CRUD works with real data
* [ ] Understand LINQ → SQL conceptually

---

# Phase 8 — Authentication & Authorization

### Goal

Understand how real applications protect resources.

### Flow

```text
Login
  ↓
Authentication
  ↓
JWT
  ↓
Request
  ↓
Authorization
  ↓
Controller
```

### Learn

* [ ] Authentication
* [ ] Authorization
* [ ] JWT
* [ ] Claims
* [ ] Roles
* [ ] `[Authorize]`
* [ ] Password hashing

### Roles

```text
Admin
Manager
Employee
```

Example:

```csharp
[Authorize(Roles = "Admin")]
public IActionResult DeleteEmployee(int id)
{
}
```

### Definition of Done

* [ ] User can login
* [ ] JWT works
* [ ] Protected endpoint works
* [ ] Roles work

---

# Phase 9 — Middleware

### Goal

Understand what happens between HTTP request and Controller.

### Request pipeline

```text
Request
   ↓
Logging
   ↓
Exception Handling
   ↓
Authentication
   ↓
Authorization
   ↓
Routing
   ↓
Controller
   ↓
Response
```

### Learn

* [ ] Middleware
* [ ] Request pipeline
* [ ] Custom middleware
* [ ] Global exception handling
* [ ] Logging

### Build

Create a simple request logging middleware.

### Definition of Done

* [ ] Can explain middleware
* [ ] Can create custom middleware
* [ ] Understand request pipeline

---

# Phase 10 — Validation & Error Handling

### Goal

Make the application behave like a real production application.

### Learn

* [ ] Model validation
* [ ] Data annotations
* [ ] Validation errors
* [ ] Global exception handling
* [ ] Problem Details
* [ ] HTTP error codes

Example:

```csharp
[Required]
[StringLength(100)]
public string Name { get; set; }
```

### Definition of Done

* [ ] Invalid requests are rejected
* [ ] Errors return meaningful responses
* [ ] Frontend can display validation errors

---

# Phase 11 — Testing

### Goal

Learn how .NET applications are tested.

### Learn

* [ ] xUnit
* [ ] Unit tests
* [ ] Mocking
* [ ] Moq
* [ ] Integration tests

Example:

```text
EmployeeService
      ↓
Unit Test
      ↓
Mock Repository
      ↓
Assert result
```

### Definition of Done

* [ ] Service has unit tests
* [ ] Important business logic is tested
* [ ] At least one integration test exists

---

# Phase 12 — Umbraco Preparation

### Goal

Connect everything you've learned to Umbraco.

### Review

* [ ] ASP.NET Core
* [ ] C#
* [ ] Razor
* [ ] Routing
* [ ] Dependency Injection
* [ ] Middleware
* [ ] Models
* [ ] HTTP
* [ ] APIs
* [ ] Database
* [ ] Authentication

### Then learn

```text
Umbraco
│
├── Content
├── Document Types
├── Properties
├── Templates
├── Razor
├── Controllers
├── Services
├── Backoffice
└── APIs
```

### Goal

Be able to understand:

```text
ASP.NET Core
      ↓
Umbraco
      ↓
CMS Content
      ↓
Razor / Templates
      ↓
HTML
```

---

# 🏁 Final Project Architecture

By the end:

```text
                        WorkHub
                           │
              ┌────────────┴────────────┐
              │                         │
           Frontend                  Backend
              │                         │
           Razor                   ASP.NET Core
                                        │
                              ┌─────────┴─────────┐
                              │                   │
                         Controllers           API
                              │                   │
                              └─────────┬─────────┘
                                        │
                                     Services
                                        │
                                   Repository
                                        │
                                     EF Core
                                        │
                                   SQL Server
```

---

# 🧠 Core Mental Models

These are more important than memorizing syntax.

### HTTP

```text
Request
   ↓
Server
   ↓
Response
```

### ASP.NET Core

```text
Request
   ↓
Middleware
   ↓
Routing
   ↓
Controller
   ↓
Service
   ↓
Database
   ↓
Response
```

### Async

```text
async
  ↓
Task<T>
  ↓
await
  ↓
result
```

### Database

```text
C# Object
   ↓
EF Core
   ↓
LINQ
   ↓
SQL
   ↓
Database
```

### Dependency Injection

```text
Program.cs
   ↓
DI Container
   ↓
Controller
   ↓
Interface
   ↓
Implementation
```

---

# 📌 Progress Tracker

```text
[ ] Phase 0 — Environment Setup
[ ] Phase 1 — C# Fundamentals
[ ] Phase 2 — ASP.NET Core Fundamentals
[ ] Phase 3 — WorkHub Dashboard
[ ] Phase 4 — Models & Data Flow
[ ] Phase 5 — REST API
[ ] Phase 6 — Service Layer & DI
[ ] Phase 7 — SQL Server + EF Core
[ ] Phase 8 — Authentication & Authorization
[ ] Phase 9 — Middleware
[ ] Phase 10 — Validation & Error Handling
[ ] Phase 11 — Testing
[ ] Phase 12 — Umbraco Preparation
```

## 🎯 Main rule

> **Don't move to the next phase just because you finished the tutorial. Move when you can explain the data/request flow without looking at the tutorial.**

For example, before leaving Phase 7, you should be able to explain:

```text
GET /employees
      ↓
Controller
      ↓
Service
      ↓
EF Core
      ↓
LINQ
      ↓
SQL Server
      ↓
List<Employee>
      ↓
Controller
      ↓
JSON / Razor
```

That's the real learning target.
