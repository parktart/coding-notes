# Microsoft SQL Server



## RDBMS

Most Popular Relational Database Management Systems (RDBMS)..

- Oracle Database
- MySQL
- Microsoft SQL Server
- PostgreSQL
- SQLite



## SQL Server

SQL Server 2022 - introduced hybrid integration with Azure

This document will mainly cover SQL Server 2019



#### SQL Server Editions

- Express (max 1.4 GB RAM - 4 Cores) - free
- Web 
- Standard (max 128 GB RAM - 24 Cores)
- Enterprise (unlimited RAM - unlimited CPU)
  - with two 'sub' additions: Developer and Evaluation - both are free for non-prod data



#### Authentication Mode

To access a SQL Server instance, authentication mode can be either..

1. **Windows Authentication**:
   - Also known as Windows Integrated Security or Trusted Connection
   - Leverages the authentication mechanisms of the Windows operating system (Windows login credentials are used)
   - Admins are responsible for managing which users have access
   - (SSO) capable - if already signed in to Windows, do not need to provide additional credentials when connecting to the SQL Server
   - Generally considered more secure because it relies on the security measures of the Windows operating system
2. **SQL Server Authentication**:
- Also known as SQL Authentication, requires users to provide a SQL Server-specific username and password
   - These credentials are stored within SQL Server - admins are responsible for storing and managing passwords
- Can be used when connecting from non-Windows systems





















ok