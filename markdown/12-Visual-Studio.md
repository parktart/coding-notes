# Visual Studio



## Windows cmd

`devenv` (Visual Studio IDE Command-Line Tool):

- You would typically use `devenv` when you want to perform operations related to Visual Studio itself, such as managing projects, solutions, and the Visual Studio IDE.
- Examples of `devenv` usage:
  - Opening a Visual Studio solution: `devenv MySolution.sln`
  - Building a specific project within a solution: `devenv MySolution.sln /Build "MyProject"`
  - Running Visual Studio from the command line: `devenv`
- `devenv` is specific to Visual Studio and is primarily used for managing the development environment and working with Visual Studio projects.



`dotnet` (Dotnet CLI):

- You would typically use `dotnet` when you want to perform operations related to building, running, and managing .NET applications and libraries.
- Examples of `dotnet` usage:
  - Creating a new console application: `dotnet new console`
  - Building a .NET project: `dotnet build`
  - Running a .NET application: `dotnet run`
  - Managing NuGet packages: `dotnet add package`
- `dotnet` is a cross-platform tool that can be used to interact with .NET projects and solutions, regardless of whether they were created in Visual Studio or another development environment.



In summary, if you are working with Visual Studio itself, managing solutions, projects, and the Visual Studio IDE, you would use `devenv`. On the other hand, if you want to build, run, and manage .NET applications and libraries, regardless of the development environment, you would use `dotnet`.



### devenv

`devenv file-or-directory-name-or-.sln-file` opens the file/folder/solution in Visual Studio

`devenv /build mysln.sln` builds the specified solution or project according to the configuration of the specified solution

`devenv /run mysln.sln` compiles and runs the specified solution

`devenv /edit file.txt` open file in current Visual Studio window

https://learn.microsoft.com/en-us/visualstudio/ide/reference/devenv-command-line-switches?view=vs-2022



### dotnet

`dotnet new`: Creates a new project or file from a template.

- Example: `dotnet new console` creates a new console application.

`dotnet restore`: Restores the dependencies and NuGet packages of a project.

- Example: `dotnet restore` restores the project dependencies.

`dotnet build`: Builds a .NET project.

- Example: `dotnet build` builds the project in the current directory.

`dotnet run`: Runs a .NET application.

- Example: `dotnet run` executes the application in the current directory.

`dotnet test`: Runs unit tests in a .NET project.

- Example: `dotnet test` runs the unit tests in the current project.

`dotnet publish`: Publishes a .NET project for deployment.

- Example: `dotnet publish --configuration Release` publishes the project in the Release configuration.

`dotnet clean`: Cleans the output and intermediate files of a .NET project.

- Example: `dotnet clean` removes the build artifacts and intermediate files.

`dotnet add`: Adds a reference, package, or other resource to a .NET project.

Example: `dotnet add package Newtonsoft.Json` adds the Newtonsoft.Json NuGet package to the project.

`dotnet remove`: Removes a reference or package from a .NET project.

- Example: `dotnet remove package Newtonsoft.Json` removes the Newtonsoft.Json NuGet package from the project.

`dotnet watch`: Watches for file changes and automatically rebuilds/restarts the application.

- Example: `dotnet watch run` starts the application and watches for changes.

