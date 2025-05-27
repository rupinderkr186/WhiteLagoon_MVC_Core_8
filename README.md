# Concepts used in project
## .Net Core Release Timeline
### Traditional Asp.Net Timeline
![image](https://github.com/user-attachments/assets/aef1cdcd-5aac-409b-a275-7b972054299c)

### .Net Core Roadmap
![image](https://github.com/user-attachments/assets/eaea9c52-1a7c-4985-abf0-d3b33a8cc74e)


## Benefits of .Net Core
![image](https://github.com/user-attachments/assets/6fcaa7b4-8b6b-4f26-b43f-5be3fb8f9436)

## Clean Architecture
### Some points for Clean Architecture
  1. One of the most commonly used **`architectural pattern`**
  2. It is a design pattern that **promotes separation of concern** by splitting one large application into **multiple layers** in a **circular design** each layer here will have its own responsibility and their dependencies
  3. **Inward Dependency**: Fundamental behind clean architecture is to create a layer design where **central core of the application is independent of any external dependency** when we have multiple circular layer the dependencies will always Point inward so a layer in clean architecture cannot have outward dependency it must always be an inward.

### Layers of Clean Architecture
![image](https://github.com/user-attachments/assets/f2e2a7c9-7118-42a7-9be5-25a91d1b5d56)

## Project
### Project Type
Create an Asp.net Core Web App(Model-View-Controller) project with c# language and use the .net9 as framework.

## .csproj project file
![image](https://github.com/user-attachments/assets/15e263a4-fb71-4f87-8be5-8d29721be668)

### Understanding `<ImplicitUsings>enable</ImplicitUsings>` in .NET Core MVC Projects

#### 📘 What Is It?

The setting:

```xml
<ImplicitUsings>enable</ImplicitUsings>
```

in a `.NET 6+` project `.csproj` file enables **implicit global using directives**, making common namespaces available automatically without needing explicit `using` statements in each file.

---

#### ✅ What Does It Do?

When enabled, the .NET SDK **automatically includes frequently used namespaces** globally for your project. This helps to reduce repetitive boilerplate in each `.cs` file.

---

#### 📦 Typical Implicit Usings in ASP.NET Core (MVC)

For projects using the `Microsoft.NET.Sdk.Web` SDK (e.g., ASP.NET Core MVC apps), the following namespaces are commonly included implicitly:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
```

The actual list may vary depending on the project type and SDK version.

---

#### 📂 How to View Implicit Usings

To see what namespaces are included automatically, open:

```
obj/Debug/net6.0/YourProject.GlobalUsings.g.cs
```

This auto-generated file contains all the injected global `using` statements.

---

#### ⚙️ How to Enable or Disable

##### Enable

```xml
<PropertyGroup>
  <ImplicitUsings>enable</ImplicitUsings>
</PropertyGroup>
```

##### Disable

```xml
<PropertyGroup>
  <ImplicitUsings>disable</ImplicitUsings>
</PropertyGroup>
```

Or omit the property entirely to use the SDK's default behavior.

---

#### 💡 Related Setting: `<Nullable>enable</Nullable>`

This setting enables **nullable reference types** for improved null-safety:

```xml
<PropertyGroup>
  <Nullable>enable</Nullable>
</PropertyGroup>
```

---

#### ✅ Benefits of Implicit Usings

- ✂️ Less boilerplate
- 🧼 Cleaner code files
- 🚀 Faster development

---

#### ❓ When to Avoid It

- When you want **full control** over all `using` directives
- In projects with **strict code standards or analysis rules**

---

#### 📎 Conclusion

Using `<ImplicitUsings>enable</ImplicitUsings>` simplifies .NET development by reducing redundant `using` directives. It's especially helpful in ASP.NET Core and console apps using .NET 6 and newer.

---
## launchSetting.json(inside Properties)
![image](https://github.com/user-attachments/assets/edb5af2f-5d3d-479b-a775-c1fdf8403e06)


### Explanation of `launchSettings.json` in ASP.NET Core

The file shown is `launchSettings.json`, a configuration file used by .NET projects (typically ASP.NET Core) to define how the application should be launched during development.

This file resides in the `Properties` folder of a .NET project and is **not used in production** — it only affects how the project runs locally in development environments using Visual Studio, Visual Studio Code, or the `dotnet` CLI.

---

### Breakdown of the File

#### 1. `$schema`
```json
"$schema": "https://json.schemastore.org/launchsettings.json"
```
- This is a schema reference for validation and IntelliSense in supporting editors like Visual Studio.

---

#### 2. `profiles`
This section defines **how different environments or servers launch the app**. Here, there are two profiles: `http` and `https`.

---

### Profile: `http`
```json
"http": {
  "commandName": "Project",
  "dotnetRunMessages": true,
  "launchBrowser": true,
  "applicationUrl": "http://localhost:5276",
  "environmentVariables": {
    "ASPNETCORE_ENVIRONMENT": "Development"
  }
}
```

- **`commandName`**: `"Project"` tells Visual Studio to run the project as defined.
- **`dotnetRunMessages`**: `true` enables logging messages like "Now listening on...".
- **`launchBrowser`**: `true` automatically opens your default browser when the app runs.
- **`applicationUrl`**: Specifies the base URL used to host the app (HTTP only here).
- **`environmentVariables`**: Sets environment variables, like `"ASPNETCORE_ENVIRONMENT": "Development"` — important for loading the correct `appsettings.{env}.json`.

---

### Profile: `https`
```json
"https": {
  "commandName": "Project",
  "dotnetRunMessages": true,
  "launchBrowser": true,
  "applicationUrl": "https://localhost:7278;http://localhost:5276",
  "environmentVariables": {
    "ASPNETCORE_ENVIRONMENT": "Development"
  }
}
```

- Same properties as the HTTP profile, but:
- **`applicationUrl`** includes both HTTPS (`7278`) and HTTP (`5276`) bindings.
- This setup is useful for apps that serve both secure and insecure traffic in development.

---

### Summary

- This file controls **local development startup settings** for an ASP.NET Core app.
- It can define multiple **profiles** (e.g., different ports, environments).
- Commonly used to:
  - Set launch URLs
  - Automatically open a browser
  - Define environment (Development, Staging, Production)

