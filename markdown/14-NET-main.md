# .NET Development





## .NET web development





## .NET and React

#### Kestrel (C#) vs React (node) Dev Server

in an ASP.NET Core with React.js web app



Yes, that's correct. In a typical setup of an ASP.NET Core web application with a React.js frontend (created using the `create-react-app` template), you'll need to start both the Kestrel web server for the backend and the development server for the React frontend.

Here's how the process generally works:

1. **Start Kestrel Web Server:** When you hit Ctrl + F5 or run the application without debugging in Visual Studio, it starts the Kestrel web server hosting your ASP.NET Core backend. This server handles API requests, serves static files, and manages the backend logic.
2. **Start React Development Server:** For the React.js frontend part of your application, you need to navigate to the `ClientApp` folder (where the React code is located) using your command-line interface. Once you're inside the `ClientApp` folder, you can run `npm start` or `yarn start` to start the React development server. This server compiles your React code, handles hot-reloading, and serves your frontend assets.
3. **Access the Application:** With both servers running, you can access your application through a web browser. The React development server usually runs on a different port (e.g., `http://localhost:3000`), and the Kestrel server runs on a separate port (e.g., `http://localhost:5000`). The React server is often configured to proxy API requests to the Kestrel server, allowing you to develop the frontend and backend together seamlessly.

Remember that the React development server is primarily meant for development and debugging. In production, the React code is typically bundled and served by the backend server (Kestrel), and you won't need to run the React development server.

To summarize, you do indeed need to start both the Kestrel web server (through Visual Studio) and the React development server (using `npm start` in the `ClientApp` folder) to have a fully functioning ASP.NET Core web application with a React.js frontend during development.



The React development server has several purposes:

1. **Hot-Reloading:** It provides hot-reloading functionality, which means that when you make changes to your React code, the server automatically updates the application in the browser without requiring a full page reload. This speeds up development and allows you to see changes in real-time.
2. **Module Bundling:** The development server uses tools like Webpack under the hood to bundle your React code and assets into a format that the browser can understand. This bundling process optimizes the code for delivery to the browser.
3. **Proxying API Requests:** Often, during development, your React frontend needs to communicate with the backend API served by Kestrel. The React development server can be configured to proxy API requests to the backend server. This allows you to make API calls as if they were being made from the same domain, avoiding cross-origin issues during development.



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

