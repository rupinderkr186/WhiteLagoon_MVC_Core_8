# .NET Core MVC Clean Architecture Application

Based on the sources, a .NET Core MVC Clean Architecture application is structured in layers to promote **separation of concerns**. The course described aims to teach how to build such an application starting from the fundamentals of a .NET Core MVC project and then applying the **Clean Architecture** design pattern.

---

## 1. Core Concepts: MVC and Clean Architecture

### MVC (Model-View-Controller)

This architectural pattern is the foundation of the application.

- **Model**: Represents the shape of the data, including classes that correspond to database tables (also known as domain entities).
- **View**: Represents the user interface, controlling the HTML elements displayed on the screen.
- **Controller**: Handles user requests and acts as the intermediary between the Model and View.
- **Action Methods**: Endpoints within a controller that handle specific requests.
- **Routing**: Defines how URLs map to specific controller action methods. The typical pattern is `/ControllerName/ActionName/OptionalId`.
- **Views Folder Structure**: Views related to a specific controller are placed in a subfolder within the `Views` folder matching the controller's name (excluding "Controller").
- **_Layout.cshtml**: The master page containing global HTML structure, header, footer, CSS/JavaScript. Content from views is rendered using `@RenderBody()`.
- **_ViewStart.cshtml**: Defines the default layout page for views.
- **_ViewImports.cshtml**: Used for global using statements and tag helpers.
- **Razor Syntax (@)**: Embeds C# code in `.cshtml` files.
- **Tag Helpers**: e.g., `asp-for` to bind model properties to input fields.
- **IActionResult**: Base return type for action methods (e.g., `ViewResult`, `RedirectToActionResult`).
- **Partial Views**: Render reusable content parts; stored in `Views/Shared/` and prefixed with an underscore (e.g., `_VillaDetail.cshtml`).

### Clean Architecture

This design pattern divides the application into layers with specific responsibilities.

#### Layers:

- **Domain Layer**: Core entities and business rules (e.g., `Villa`, `VillaNumber`).
- **Application Layer**: Contains business logic and repository interfaces.
- **Infrastructure Layer**: Handles external concerns like database access, emails, etc.
- **Presentation Layer (Web Project)**: ASP.NET Core MVC web application (Controllers + Views).

#### Dependency Rule:

Dependencies **flow inward**:
- Presentation → Infrastructure → Application → Domain

---

## 2. Key .NET Core Features and Patterns in Clean Architecture

### Dependency Injection (DI)

- Built-in to .NET Core
- Services are registered in `Program.cs` and injected via constructors

### Entity Framework Core (EF Core)

- **DbContext**: Defined in Infrastructure layer
- **Entities**: Placed in Domain layer
- **Connection String**: Stored in `appsettings.json` or environment-specific files
- **Migrations**: Use `Add-Migration` and `Update-Database`
- **CRUD Operations**: `.Add()`, `.Update()`, `.Remove()`, `.ToList()`, `.FirstOrDefault()`, `.Include()`

### Repository Pattern

- **Interfaces** (e.g., `IVillaRepository`) in Application layer
- **Implementations** in Infrastructure layer using EF Core

### Generic Repository

- A base interface and class for CRUD operations across entity types (`<T>`)

### Unit of Work Pattern

- **Interface (`IUnitOfWork`)** in Application layer
- **Implementation (`UnitOfWork`)** in Infrastructure layer
- Coordinates saving changes using `DbContext.SaveChanges()`

### Program.cs

- Configures services and middleware:
  - `AddControllersWithViews()`
  - `AddDbContext()`
  - Register repositories and UnitOfWork
  - `UseExceptionHandler`, `UseStaticFiles`, `UseRouting`, `UseAuthorization`

### Configuration (appsettings.json)

- Stores config such as connection strings and secrets
- Supports environment-specific settings via `ASPNETCORE_ENVIRONMENT`

### Model State Validation

- Uses data annotations for validation
- `[ValidateNever]` and `ModelState.Remove()` can skip validation for specific fields

### TempData

- Pass data between requests (e.g., post-redirect notifications)

---

## 3. Application Structure and Setup

- Create a new **ASP.NET Core Web App (Model-View-Controller)** project
- Start with **No Authentication**, add it later
- Solution Structure:
  - `.Domain` (Class Library)
  - `.Application` (Class Library)
  - `.Infrastructure` (Class Library)
  - `.Web` (ASP.NET Core MVC Web Project)

- Set project references for inward dependency
- Add necessary **NuGet Packages**:
  - EF Core → Infrastructure
  - MVC/web packages → Web project
- Static assets (CSS/JS/images) → `wwwroot`

---

## 4. Development Practices

- Use **GitHub** for source control
- Set **debug points** for step-by-step inspection
- Reference **course content** (code, images)
- Use `nameof()` for strong typing in action/controller references
- Troubleshoot common issues (e.g., malformed connection strings)
- Manage **learning overwhelm** with pacing and practice

---

## Summary

This guide outlines building a .NET Core MVC application following the Clean Architecture pattern, emphasizing:

- Separation of concerns via distinct layers
- Core .NET features like DI and EF Core
- Structured project setup and configuration
- Best practices like repository/unit of work patterns
