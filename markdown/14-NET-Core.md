# .NET Core



## MVC

ASP.NET Core Web App (MVC) is a framework for building web applications using the Model-View-Controller (MVC) architectural pattern. It provides a structured approach to developing web applications by separating concerns into distinct components.

The content of an ASP.NET Core Web App (MVC) project typically includes the following components:

1. Controllers: Controllers handle incoming HTTP requests, process user input, interact with models or services, and return appropriate responses. Controllers are typically C# classes that inherit from the `Controller` base class or its derived classes.
2. Views: Views are responsible for rendering the user interface and displaying data to the user. Views use a combination of HTML markup and Razor syntax to define the UI. Razor syntax allows you to embed C# code within the HTML markup to dynamically generate content.
3. Models: Models represent the data and business logic of the application. They define the structure and behavior of the application's data entities or domain objects. Models can be simple POCO (Plain Old CLR Object) classes or more complex entities with additional logic.
4. View Models: View Models are used to pass data from controllers to views. They are specifically designed to encapsulate the data required by a view and may combine data from multiple models or provide additional data manipulation logic.
5. Routing: ASP.NET Core MVC uses routing to map incoming URLs to the appropriate controllers and actions. Routing rules are defined in the `Startup.cs` file and can be configured to handle various URL patterns and parameters.
6. Middleware: Middleware components handle specific stages of the HTTP request-response pipeline. They can perform tasks such as authentication, authorization, logging, error handling, and more. Middleware can be added and configured in the `Startup.cs` file.
7. Configuration files: Configuration files such as `appsettings.json` provide settings and options for the application. They allow you to define various settings like database connection strings, logging configurations, or custom application settings.
8. Static files: Similar to ASP.NET Core Razor Pages, static files such as CSS stylesheets, JavaScript files, images, and other assets are commonly included to define the visual and interactive aspects of the web application.
9. Startup and Program files: The `Startup.cs` and `Program.cs` files contain the application's startup logic. They configure services, middleware pipeline, and other application-specific settings. They define how the application should behave and handle requests.

These components work together to build a web application using the ASP.NET Core MVC framework. The structure and content of an ASP.NET Core Web App (MVC) project may vary based on application requirements and architectural choices.



## MVC

https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-7.0&tabs=visual-studio

