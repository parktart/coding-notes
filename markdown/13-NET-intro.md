# .NET Development Intro



### C#

C# is similar to Java and C++ (is an object-oriented language)

modern programming language developed by Microsoft as a **part of the .NET framework**

C# is a general-purpose programming language

which means it can be used to build a wide range of applications including..

desktop applications, web applications, mobile apps, games, and more

is designed to be simple, safe, and easy to use, with features such as automatic memory management and garbage collection

commonly used for developing applications for Windows OS, though it can be used to develop applications for other platforms as well (Linux, macOS, iOS, and Android) using the .NET Core framework

additionally C# can be used for cross-platform development - allowing developers to write code that can run on multiple platforms with minimal changes



### .NET

.NET serves as an umbrella term for Microsoft's entire suite of software development technologies, including frameworks, libraries, and runtime environments.

This set of free and open-source technologies allows developers to create a variety of applications, including web, desktop, mobile, and gaming using multiple programming languages such as C#, Visual Basic, and F#

.NET provides a large class library, language interoperability, garbage collection, and other features to simplify and accelerate application development

It also includes a runtime environment called the Common Language Runtime (CLR), which provides services such as memory management, type safety, and exception handling

.NET Framework, ASP.NET, and ASP.NET Core all fall under the .NET ecosystem



### .NET Framework

.NET Framework was the original framework in the .NET ecosystem, primarily designed for creating Windows-based applications

ASP.NET, a component of .NET Framework, was tailored for building dynamic web pages and web applications

Over time, .NET Framework's community has matured, but its growth is seen as limited due to its Windows-centric nature. It's perceived as becoming obsolete compared to newer platforms in the .NET ecosystem, with Microsoft now only providing security and reliability updates for it



### ASP.NET

ASP.NET is a framework for developing web applications and services

Initially part of the .NET Framework, it has evolved over time, but ASP.NET has been widely used for building web applications since the early 2000s

ASP.NET Core was a redesign of ASP.NET, this next-generation version of ASP.NET represents a significant departure from the previous ASP.NET framework

Cross-platform and open source, ASP.NET Core can run on Windows, macOS, and Linux

and introduced a more modular and lightweight architecture

ASP.NET Core also includes support for building not only web applications but also cross-platform desktop applications and cloud-based microservices



### .NET Core and .NET 5/6

.NET Core is a cross-platform, high-performance framework for building modern, cloud-based, internet-connected applications, including web, mobile, desktop, gaming, IoT, and AI applications. It's seen as a successor to .NET Framework with a focus on modularity, performance, and cross-platform support

With the advent of .NET 5 and .NET 6, Microsoft aims to unify the .NET ecosystem, bringing together the best of .NET Framework, .NET Core, and Mono/Xamarin under a single runtime and framework with interoperable libraries

.NET 6 continues the vision of unifying the platform, offering superior performance, compatibility, and features suitable for a broad array of application types



### SQL

SQL (Structured Query Language) is a standardized programming language used for managing and manipulating **relational** databases. It provides a set of commands and syntax for creating, modifying, and querying databases.

SQL is widely used in various industries and applications for managing and querying data. It provides a standardized way to interact with relational databases, allowing developers and database administrators to efficiently store, retrieve, and manipulate data. Different database management systems (DBMS) such as MySQL, Oracle, Microsoft SQL Server, and PostgreSQL implement SQL with slight variations, but the core SQL syntax and concepts remain consistent across most implementations.



### PostgreSQL

PostgreSQL, often referred to as just 'Postgres', is a popular open-source relational database management system (RDBMS) that follows the SQL standards closely. It is known for its robustness, reliability, and advanced features.

PostgreSQL fully supports SQL and adheres to the SQL standards. It provides a comprehensive set of SQL commands for data manipulation, querying, and database management, including SELECT, INSERT, UPDATE, DELETE, CREATE, ALTER, and DROP statements.

PostgreSQL is widely used in a range of applications, from small-scale projects to large-scale enterprise systems.

PLV8 is an extension for the PostgreSQL database system that enables the execution of JavaScript code within the database. It combines the power of PostgreSQL's data management capabilities with the flexibility and functionality of JavaScript. PLV8 allows you to write and execute JavaScript code directly within the PostgreSQL database server. This means you can leverage the full capabilities of JavaScript for data processing, manipulation, and complex logic directly within the database.



### Visual Studio

Visual Studio is an IDE (integrated development environment) primarily designed for with the .NET ecosystem

Visual Studio provides a rich set of features for building, testing, debugging, and deploying software applications

both Visual Studio and VSCode can be used for C# development, but Visual Studio is the more powerful and feature-rich option, especially for large-scale software development projects

VSCode is a popular choice for smaller projects or cross-platform development



### LocalDB

LocalDB is a lightweight version of Microsoft SQL Server that is designed for developers to easily create and manage local databases for development and testing purposes. It provides a simplified, on-demand instance of SQL Server that can be used without the need for a full installation or dedicated server.

LocalDB provides a simplified installation experience compared to the full SQL Server installation. It is a user-instance database engine that is automatically started and stopped on demand, reducing the system resource usage.

Database File: LocalDB stores its databases in a single file that can be easily moved or shared. The file has the `.mdf` extension and contains both the database schema and data.

LocalDB allows developers to easily create, manage, and query databases within their development environment. It provides a subset of features compared to the full SQL Server, making it ideal for local development and testing scenarios. It is particularly useful for building and testing applications that rely on a SQL Server backend and allows developers to focus on application development without the need for a full SQL Server installation.



### Insight.Database

Insight.Database is an open-source micro-ORM (Object-Relational Mapping) library for .NET that simplifies database access and data mapping in applications. It provides a lightweight and efficient way to interact with databases, reducing the amount of boilerplate code required for data access and increasing developer productivity.

As a micro-ORM, Insight.Database offers a lightweight and streamlined approach to object-relational mapping. It focuses on simplicity, performance, and flexibility, providing a minimalistic set of features compared to full-fledged ORMs.

data access layer

