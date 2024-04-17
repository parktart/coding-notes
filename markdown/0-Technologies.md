# Technologies

## Full Stack plan

### Backend/API

- **Language and Framework:** Continue using **C# with .NET**. The .NET platform is versatile and fully capable of working with PostgreSQL, offering libraries and tools for seamless integration.
- **ORM:** Instead of Insight.Database, consider using **Npgsql** with **Dapper** or **Entity Framework Core**. Npgsql is the .NET data provider for PostgreSQL, offering a high-performance, easy-to-use driver for connecting your .NET applications to PostgreSQL. Dapper is a simple object mapper for .NET that is very lightweight and fast, similar in philosophy to Insight.Database. Entity Framework Core can also be used with PostgreSQL through the Npgsql Entity Framework Core provider, offering a more feature-rich ORM experience if needed.

### Frontend

- **Framework:** Stick with **React** using **Vite** for the frontend. This part of your stack doesn't need to change, as it's independent of the backend database choice.

### Database

- **Database System:** **PostgreSQL**. It's a powerful, open-source object-relational database system that has strong support for advanced data types and performance optimization features.

### IDE/Development Environment

- **IDE:** Continue using **Visual Studio IDE** for C# and .NET development. Visual Studio offers extensive support for .NET development and can be used effectively for both backend and frontend development, especially with extensions that enhance its functionality.
- **Additional Tools:** For PostgreSQL-specific tasks such as database design, management, and query optimization, you might use **pgAdmin** or **DBeaver**. These tools are not integrated into Visual Studio but are essential for managing PostgreSQL databases effectively.
- **Extensions and Tools for PostgreSQL in Visual Studio:** While Visual Studio might not have built-in support for PostgreSQL to the extent it does for SQL Server, extensions like **Npgsql for Visual Studio** (if available) can help bridge that gap, offering enhanced PostgreSQL support within the IDE.

### Version Control and Project Management

- **Version Control:** Continue using your existing version control system (e.g., Git) for managing your source code, including PostgreSQL database scripts and migrations, if you decide to manage these within the same repository as your application code.

### Summary

This recommended stack allows you to leverage your existing knowledge and experience with .NET, C#, React, and Visual Studio, while incorporating PostgreSQL as your database system. By adopting Npgsql and potentially Dapper or Entity Framework Core for data access, you can create a powerful and efficient full-stack application with PostgreSQL at its core. This approach offers a smooth transition with minimal disruption to your existing development practices.



Why use Insight.Database over Dapper?

Choosing between Dapper and Insight.Database for data access in a .NET application involves considering several factors such as performance, ease of use, community support, and feature set. Both are micro-ORMs (Object-Relational Mappers) designed to simplify data access while providing better performance than more heavyweight ORMs like Entity Framework. Here's a comparison to help understand why one might choose Dapper over Insight.Database:

### Performance

- **Dapper**: Known for its high performance, Dapper is very efficient in executing database queries and mapping the results to .NET objects. It adds minimal overhead to your database calls, making it one of the fastest data access libraries available for .NET.
- **Insight.Database**: Also designed for high performance, Insight.Database automatically maps query results to objects and is optimized for speed. While it is fast, benchmarks typically show Dapper having a slight edge in raw performance, especially in scenarios involving complex mappings and large datasets.

### Ease of Use

- **Dapper**: Dapper's API is straightforward and easy to understand, requiring explicit mapping between database queries and objects. This explicitness ensures clarity in how data mappings are handled but can lead to more boilerplate code compared to Insight.Database.
- **Insight.Database**: One of Insight.Database's main selling points is its "automagic" mapping capabilities, where it can automatically map query results to objects without requiring explicit mappings. This can significantly reduce boilerplate code and make it easier to write data access code quickly.

### Community Support and Ecosystem

- **Dapper**: As one of the most popular micro-ORMs in the .NET ecosystem, Dapper enjoys extensive community support. There are numerous resources available online, including tutorials, documentation, and forums. This popularity also means it's easier to find solutions to common problems and to recruit developers familiar with Dapper.
- **Insight.Database**: While Insight.Database has a dedicated user base and is well-regarded by those who use it, its community is smaller than Dapper's. This smaller community can mean fewer resources and less third-party support for integrating with other tools or libraries.

### Feature Set

- **Dapper**: Primarily focused on query execution and result mapping, Dapper keeps its feature set tight and focused. It does not try to abstract away SQL; instead, it embraces it, giving developers full control over their SQL queries.
- **Insight.Database**: Offers a wider range of features out of the box, including automatic interface implementation, advanced mapping capabilities, and more. These features can accelerate development speed for certain projects but may introduce additional complexity when debugging or customizing behavior.

### Conclusion

The choice between Dapper and Insight.Database often comes down to personal preference, project requirements, and the specific needs of your development team. Dapper might be preferred for its raw performance, widespread community support, and simplicity, making it a safe and reliable choice for many projects. On the other hand, Insight.Database's automatic mapping and rich feature set can significantly speed up development for projects where these features align well with project requirements.

Ultimately, both libraries offer significant advantages over traditional ORMs in terms of performance and direct control over SQL execution, and the choice between them should be informed by the specific needs and priorities of your project and team.



## Most Popular Languages

**Front End**: HTML, CSS, JavaScript, and their relevant frameworks (Angular, **React**, Vue, etc)

**Back End**: Java, Python, Ruby, and their relevant frameworks (Express, Ruby on Rails aka Rails)

**Most Commonly Used Languages in order (2022)..**
JavaScript
HTML/CSS
SQL
Python
TypeScript
Java
C#
Bash/Shell
PHP
C++
C
PowerShell
Go
Kotlin
Rust
Ruby

**Databases by Most Popular 2022**
MySQL
PostgreSQL
SQLite
MongoDB
Microsoft SQL Server

**Web Frameworks by Most Popular 2022**
Node.js BE
React.js FE
jQuery FE
Express BE
Angular FE
ASP.NET Core BE
Vue.js FE
ASP.NET BE
Django BE
Angular.js FE
Ruby on Rails BE

**Fundamental Tools for web developers by most popular**
Docker
npm
Yarn
Homebrew
Kubernetes

**Most Popular IDE**: Visual Studio Code (VSCode)

**Most Used Collaboration Tools**: like Teams for devs
Jira Work Management
Confluence
Trello

<u>FRONT END</u>: client side

**React**: an open-source JavaScript framework that can be used to build interactive user interfaces across Web, Mobile, Desktop, etc (created by Meta/Facebook)
note React Native is a mobile development framework (used to make mobile apps)

**Angular**: an open-source JavaScript framework - runs smoothly on web and mobile - better for bigger enterprise-level applications (created by Google)

**Vue.js**: an open-source JavaScript framework - a lightweight competitor to React and Angular - for building SPAs single page applications (created by Google)

**jQuery**: an open-source JavaScript framework - lightweight and fast - old school but still very popular

**JavaScript**: a high-level, interpreted programming language conforming to the ECMAScript specification - the language is considered weakly typed, multi-paradigm, and dynamic

**HTML**:

**HTML5**:

**CSS**:

**Swift**:

<u>BACK END</u>: server side

**Ruby on Rails**: an open-source Java based back-end framework for Ruby

**Django**: an open-source Python based back-end framework

**ASP.NET Core**: an open-source back-end framework compatible with JavaScript-based front-end frameworks

**Node.js**: an open-source JavaScript runtime that executes JS code externally through the chrome V8 engine

**Express**: an open-source back-end framework for Node.js

**Java**: a general-purpose programming language, Java features class-based, concurrent, object-oriented funtions
designed to minimize implementation dependencies, Java allows application developers to 'write once, run away'
Java is one of the most popular programming languages used today, especially for client-server software applications

**C**:

**C++**:

**C#**: a general-purpose, multi-paradigm programming language, C# encompasses imperative, strong typing, functional, declarative, object-oriented, component-oriented and generic programming disciplines. Developed by Microsoft within the .NET initiative, C# received approval as a standard by ISO and ECMA.

**Python**: a general-purpose, high-level, interpreted programming language - Python's design philosophy emphasizes code readablility by using significant whitespace
and providing clear programming on large and small scales

**XML**:

**PHP**:

**MongoDB**:



## The Stacks

==**MEAN**:== is a free and open-source JavaScript software stack - all components of the MEAN stack support programs written in JavaScript (MEAN applications can be writen in one language for both server and client side)

| Software | Type               | Side      |
| -------- | ------------------ | --------- |
| MongoDB  | data-base          | back end  |
| Express  | framework          | back end  |
| Angular  | framework          | front end |
| NodeJS   | javascript runtime | back end  |

language: JavaScript or TypeScript (front end)

* * *

==**MERN**:==

| Software | Type               | Side      |
| -------- | ------------------ | --------- |
| MongoDB  | data-base          | back end  |
| Express  | framework          | back end  |
| React    | framework          | front end |
| NodeJS   | javascript runtime | back end  |

language: JavaScript or TypeScript (front end)

* * *

**MEVN**:

| Software | Type               | Side      |
| -------- | ------------------ | --------- |
| MongoDB  | data-base          | back end  |
| Express  | framework          | back end  |
| Vue      | framework          | front end |
| NodeJS   | javascript runtime | back end  |

language: JavaScript or TypeScript (front end)

* * *

==**PERN**:== with PostgreSQL (a dependable, secure, enterprise-grade SQL-based database system - used at large enterprises like Healthcare and Banking)

| Software   | Type               | Side      |
| ---------- | ------------------ | --------- |
| PostgreSQL | data base          | back end  |
| Express    | framework          | back end  |
| React      | framework          | front end |
| NodeJS     | javascript runtime | back end  |

language: JavaScript or TypeScript (front end)

* * *

==**LAMP**:== lamp denotes one of the most common solution stacks for many of the web's most popular applications - it now refers to a generic software stack model - and its components are largely interchangeable - Used reliably by web developers for more than 20 years - simple and stable way to develop high performance websites and apps - time tested stack

| Software        | Type      | Side     |
| --------------- | --------- | -------- |
| Linux           | OS        | -        |
| Apache          | server    | back end |
| MySQL           | data base | back end |
| PHP/Python/Perl | language  | back end |

language: JavaScript or TypeScript (front end)

* * *

**LEMP**:

| Software | Type      | Side     |
| -------- | --------- | -------- |
| Linux    | OS        | -        |
| Nginx    | ?         | ?        |
| MySQL    | data base | back end |
| PHP      | language  | back end |

language: JavaScript or TypeScript (front end)

* * *

**Django**:

| Software | Type      | Side     |
| -------- | --------- | -------- |
| Django   | ?         | back end |
| MySQL    | data base | back end |
| Python   | language  | back end |

language: JavaScript or TypeScript (front end)

* * *

==**Ruby on Rails**:==

| Software | Type      | Side     |
| -------- | --------- | -------- |
| Ruby     | Language  | back end |
| SQLite   | data base | back end |
| Rails    | framework | -        |

language: Ruby

* * *

**Java C#**:

| Software | Type | Side |
| -------- | ---- | ---- |

language: JavaScript or TypeScript (front end)

