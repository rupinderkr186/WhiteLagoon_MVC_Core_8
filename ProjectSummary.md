# Briefing Document: Clean Architecture Fundamentals in .NET Core MVC (.NET 8) - Excerpts Review

**Date:** 2023-10-27  
**Source:** Excerpts from *Clean Architecture Fundamentals in .NET Core MVC (.NET 8)*  
**Subject:** Core concepts, project structure, error handling, routing, data management, dependency injection, and UI patterns in a .NET Core MVC (.NET 8) application with Clean Architecture principles.

---

## Executive Summary

These excerpts provide a foundational understanding of building a .NET Core MVC (.NET 8) application incorporating Clean Architecture principles. Key areas include:

- Debugging techniques
- Application configuration via `Program.cs`
- MVC structure and routing
- Entity Framework Core for data management
- Dependency injection and Unit of Work
- UI patterns including partial views and validation

---

## Key Themes and Important Ideas/Facts

### Effective Debugging and Problem Solving

- Primary approach: **Google the error message**.
- If unresolved, check Q&A platforms like **Udemy**.
- When asking for help, include:
  - Clear issue description
  - Steps to reproduce
  - **GitHub link** to the project (most critical)

---

### Application Configuration (`Program.cs`)

- Central role in app configuration.
- Uses environment variables for conditional behavior.
- Middleware pipeline includes:
  - `UseHttpsRedirection()`
  - `UseStaticFiles()`
  - `UseRouting()`
  - `UseAuthorization()` (covered later)
  - `MapControllerRoute()` with default pattern to `/Home/Index`
- `app.Run()` starts the application.

---

### MVC Architecture Fundamentals

#### Routing Pattern

- Pattern: `/Controller/Action/ID`
- Segments:
  - Controller name
  - Action name
  - Optional ID (`{id?}`)
- Defaults to `/Home/Index` if nothing is specified.

#### Controllers

- Located in **Controllers** folder.
- Must end with `Controller`.
- Return type typically `IActionResult`.

#### Views

- Located in **Views** folder, subfolders match controller names.
- Defaults to view matching action name.
- **Partial Views**:
  - Start with `_`
  - Included using `<partial>` tag helper
  - Not rendered standalone

#### Layouts and Shared Files

- `_Layout.cshtml`: Master page
- `_ViewStart.cshtml`: Defines default layout
- `_ViewImports.cshtml`: Global imports for views

#### Razor Syntax

- C# embedded in `.cshtml` via `@`
- Looping: `@foreach`
- Model access via `Model`

---

### Data Management with Entity Framework Core

- **Layers**: Domain, Application, Infrastructure
- Entities/models live in the **Domain layer**
- Required NuGet packages: `Microsoft.EntityFrameworkCore.*`

#### `ApplicationDbContext`

- Inherits from `DbContext`
- Located in Infrastructure layer
- Uses `DbSet<T>` for each entity/table

#### Configuration

- Connection strings in `appsettings.json`
- Use `HasData()` in `OnModelCreating` for seeding

#### Migrations

- Use `Add-Migration` and `Update-Database`
- **Don't modify migration files** directly

#### Relationships

- Supports foreign keys and navigation properties
- Supports primary key conventions and customization

---

### Dependency Injection

- Services registered in `Program.cs` using `AddScoped()`, etc.
- Injected into controllers via constructors
- Prefer injecting interfaces for loose coupling

---

### Repository and Unit of Work Patterns

- Generic repository (`IRepository<T>`) for CRUD operations
- Implementations reside in Infrastructure
- `UnitOfWork` wraps multiple repositories
  - Central `Save()` method
  - Promotes clean controller code

---

### CRUD Operations Implementation

- Sample entity: `Villa`, `VillaNumber`
- Repository usage:
  - Read: `_unitOfWork.Villa.GetAll()`
  - Create: `_unitOfWork.Villa.Add(obj)`
  - Update: `_unitOfWork.Villa.Update(obj)`
  - Delete: `_unitOfWork.Villa.Remove(obj)`
  - Save: `_unitOfWork.Save()`

---

### Validation

#### Server-Side

- Use `[Required]` and `ModelState.IsValid`
- Tag helpers:
  - `asp-validation-for`
  - `asp-validation-summary`
- Add custom errors: `ModelState.AddModelError()`

#### Client-Side

- Include `_ValidationScriptsPartial.cshtml`
- Uses jQuery Validation libraries

---

### Image Uploading

- Inject `IWebHostEnvironment` to access `wwwroot`
- Save files using `FileStream`
- Use `Guid` for file name uniqueness
- Save path (URL) in database
- Support default images

---

### UI Elements and Tag Helpers

- **Bootstrap** for styling
- Tag Helpers:
  - `asp-controller`, `asp-action`, `asp-for`
  - `asp-validation-for`, `asp-validation-summary`
  - `partial`, `asp-items`
- **Dropdowns**: `<select asp-items="...">`
- **ViewData vs. ViewBag**: Temporary data
- **View Models**: Strongly typed and cleaner
- `[ValidateNever]` to skip validation on specific properties
- **TempData**: One-time messages (success/error)
- **Toaster Notifications**: For user alerts

---

### Code Organization and Best Practices

- Use `nameof()` instead of magic strings
- CSS Isolation: Scoped CSS using `.cshtml.css` files
  - Example: `_Layout.cshtml.css`

---

## Conclusion

These excerpts offer a practical and structured guide to developing .NET Core MVC applications using Clean Architecture. They cover debugging, MVC fundamentals, Entity Framework integration, and advanced patterns like Unit of Work and Repository. Developers are provided with hands-on strategies to apply best practices and maintain scalable, testable, and cleanly organized codebases.
