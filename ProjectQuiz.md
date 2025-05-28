
# MVC Architecture and .NET Core Fundamentals Study Guide

This study guide covers key concepts and practices in .NET Core MVC development based on the provided source material.

---

## Quiz

Answer the following questions in 2–3 sentences each:

1. What is the recommended first step when encountering an error message while programming?  
2. What are the three critical pieces of information to include when raising a new question for help?  
3. In a .NET Core MVC application, which file is primarily used for configuring services and the request middleware pipeline?  
4. What is the default routing pattern in a .NET Core MVC application, considering the parts after the domain name and port?  
5. Based on the URL `/category/index/3`, identify the controller, action, and ID according to the default MVC routing.  
6. What is a "partial view" and what is its typical naming convention?  
7. What is the primary purpose of the `_ViewStart.cshtml` file?  
8. What is the purpose of the `_ViewImports.cshtml` file and where do its effects apply?  
9. Explain the concept of an `IActionResult` and how it relates to different return types in action methods.  
10. What is the main reason for using `TempData` in an MVC application?

---

## Quiz Answer Key

1. The first step is to Google the error message. Copy and paste the exact error into a Google search.
2. When raising a new question, you must clearly define the issue, include steps to reproduce it, and provide a GitHub link to your project.
3. The `Program.cs` file is primarily used for configuring services and defining the request middleware pipeline in a .NET Core MVC application.
4. The default routing pattern is `Controller/Action/Id`, where the ID is optional.
5. In the URL `/category/index/3`, the controller is `category`, the action is `index`, and the ID is `3`.
6. A partial view is a reusable view component that cannot be displayed on its own. It is typically named with an underscore prefix (e.g., `_PartialViewName.cshtml`).
7. The `_ViewStart.cshtml` file is used to define the default layout or master page for other views in the application.
8. The `_ViewImports.cshtml` file is used for defining global using statements and tag helpers that will be automatically available in all views within the same folder and its subfolders. Its effects are limited to views.
9. `IActionResult` is an interface that serves as a base abstraction for different types of action results that an action method can return, such as `ViewResult`, `RedirectToActionResult`, etc.
10. `TempData` is primarily used for displaying temporary notifications to the user after a redirect, as its data only persists for one subsequent request.

---

## Essay Questions

Consider the following questions and formulate a detailed response for each. *Do not provide answers in this section.*

- Discuss the importance of separating concerns in a large .NET Core MVC application using Clean Architecture, specifically focusing on the roles and dependencies of the Domain, Application, and Infrastructure layers.
- Explain the relationship between Controllers, Views, and Models in the MVC architecture. Describe how data flows between these components during a typical user request that involves displaying data from the database.
- Compare and contrast Model State Validation and Client-Side Validation in .NET Core MVC. Explain how they work together to provide a robust validation strategy and the benefits of implementing both.
- Describe the purpose and advantages of using a Generic Repository and the Unit of Work pattern in a .NET Core MVC application for database interactions with Entity Framework Core. How do these patterns improve code maintainability and testability?
- Explain the process of handling file uploads in a .NET Core MVC application, including how to access the uploaded file, generate a unique name, save it to the file system, and store the file path or URL in the database.

---

## Glossary of Key Terms

| Term | Definition |
|------|------------|
| **Action Method** | A public method within a Controller that handles incoming requests and returns an `ActionResult` or a derived type. |
| **App Settings** | Configuration files (typically `appsettings.json`) used to store application settings, such as database connection strings and environment variables. |
| **Application Layer** | In Clean Architecture, this layer contains the business logic and use cases of the application. |
| **ASP.NET Core** | An open-source, cross-platform framework for building modern, cloud-based, internet-connected applications. |
| **Tag Helpers (ASP Controller/Action/For/Route/Items/Validation)** | Tag Helpers used to bind HTML elements in Razor views to model properties, controllers, or validation messages. |
| **Controller** | A class in the MVC architecture responsible for handling user input, interacting with the model, and selecting the appropriate view to render. |
| **Connection String** | A string containing information needed to connect to a data source, such as a database server, name, and credentials. |
| **CRUD Operations** | Acronym for Create, Read, Update, and Delete – the basic operations for data manipulation. |
| **CSS Isolation** | A feature that scopes CSS styles to specific Razor components or views. |
| **DbContext** | Represents a session with the database and is used to query and save instances of entities. |
| **DbSet** | A collection of entities that can be queried from the database. |
| **Dependency Injection (DI)** | A pattern in which dependencies are supplied externally rather than hardcoded, promoting loose coupling. |
| **Domain Layer** | The core business logic layer in Clean Architecture, independent of any framework or external service. |
| **Eager Loading** | Loading related data as part of the initial query in EF Core. |
| **Entity Framework Core (EF Core)** | A modern ORM for .NET enabling developers to work with databases using .NET objects. |
| **Environment Variables** | Values set outside the application to define behavior based on the environment (Development, Production, etc.). |
| **Expression** | A tree-like data structure used in LINQ to represent code for filtering or sorting. |
| **Foreign Key Relation** | A database-level link between two tables using key fields. |
| **Generic Repository** | A pattern for abstracting common database operations into a generic class or interface. |
| **GitHub Co-pilot** | An AI-powered code assistant providing real-time code suggestions. |
| **Include Properties** | Used in EF Core queries to eagerly load navigation properties. |
| **Infrastructure Layer** | Implements the interfaces defined in the application layer and handles persistence, external APIs, and other system interactions. |
| **IntelliSense** | An IDE feature offering auto-completion and code suggestions. |
| **IQueryable** | Represents a query that can be executed against a data source. |
| **LINQ** | A feature in .NET that enables querying data using C# syntax. |
| **Middleware Pipeline** | A sequence of components that process HTTP requests in ASP.NET Core. |
| **Migrations** | EF Core feature for evolving the database schema alongside your application code. |
| **Model** | Represents the application’s data and business rules in the MVC architecture. |
| **Model State** | Represents the state of model binding and validation in a controller. |
| **MVC Architecture** | A design pattern that separates concerns into Model, View, and Controller layers. |
| **Navigation Property** | An EF Core property that defines a relationship to another entity. |
| **NuGet Packages** | Packages containing reusable .NET libraries, tools, and dependencies. |
| **Partial View** | A reusable view component, usually named with a leading underscore (e.g., `_MyPartial.cshtml`). |
| **Program.cs** | The main file for configuring services and request handling in .NET Core applications. |
| **Razor Syntax** | A templating syntax for embedding server-side logic into HTML. |
| **RedirectToActionResult** | Represents a result that redirects to a specified action method. |
| **Repository Pattern** | A pattern to abstract the data access layer and decouple it from business logic. |
| **Request Pipeline** | See "Middleware Pipeline". |
| **Routing** | Maps incoming requests to the appropriate controller and action. |
| **Scoped Dependency** | A service lifetime that exists for the duration of a single request. |
| **Seeding Data** | Pre-populating a database with initial data. |
| **Service Container** | Stores and resolves services using DI. |
| **Solution Explorer** | Visual Studio panel displaying project structure. |
| **Static Files** | Files like images, CSS, and JavaScript that are served directly. |
| **Tag Helpers** | Extend HTML elements with server-side logic in Razor. |
| **TempData** | Holds data for one request and the subsequent one, typically used with redirects. |
| **Toaster Notification** | A brief, non-blocking message shown to users. |
| **Trusted Connection** | Database authentication method using Windows credentials. |
| **Unit of Work Pattern** | Groups related operations into a single transaction to maintain consistency. |
| **ValidateNever Attribute** | Prevents validation for a specific model property. |
| **View** | Defines the UI in MVC; renders HTML from server-side code. |
| **ViewBag / ViewData** | Containers for passing dynamic data from controller to view. |
| **View Engine** | Software that parses and renders views. |
| **ViewModel** | A model specifically designed for views. |
| **ViewResult** | An ActionResult that renders a view. |
| **wwwroot** | Folder for serving static assets in ASP.NET Core.
