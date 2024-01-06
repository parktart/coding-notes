# Full Stack App

## Overview

Visual Studio 2022 template: React and ASP.NET Core

React Vite frontend

C# .NET 8 backend

SQL Server 2019 database

Insight.Database micro ORM

see `package.json` for a list of the various packages used in the React frontend

 

## Front-End



### package.json

React Vite front-end with C# .NET 8 back-end

```json
// package.json

{
  "name": "web.client",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "@hookform/resolvers": "^3.3.2",
    "@tanstack/react-query": "^5.13.4",
    "@tanstack/react-query-devtools": "^5.13.5",
    "@tanstack/react-table": "^8.10.7",
    "axios": "^1.6.2",
    "bootstrap": "^5.3.2",
    "classnames": "^2.3.2",
    "downshift": "^8.2.3",
    "luxon": "^3.4.4",
    "numeral": "^2.0.6",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-error-boundary": "^4.0.11",
    "react-helmet-async": "^2.0.3",
    "react-hook-form": "^7.49.2",
    "react-hot-toast": "^2.4.1",
    "react-icons": "^4.12.0",
    "react-number-format": "^5.3.1",
    "react-router-dom": "^6.21.0",
    "yup": "^1.3.3"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@vitejs/plugin-react": "^4.2.1",
    "eslint": "^8.55.0",
    "eslint-plugin-react": "^7.33.2",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.5",
    "sass": "^1.69.5",
    "vite": "^5.0.8"
  }
}
```

