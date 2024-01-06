# React Libraries





## React Router

`"react-router-dom"`



### Using BrowserRouter

React Router can be implemented in various ways. One of the simpler implementations is using the `BrowserRouter` component.

In your main entry file (usually `main.jsx` or `index.jsx`)

```jsx
// main.jsx
import ReactDOM from 'react-dom/client';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

const container = document.getElementById('root');
const root = ReactDOM.createRoot(container);

root.render(
    <BrowserRouter>
      <App />
    </BrowserRouter>
);
```

**BrowserRouter** wraps the entire application to enable routing



In `App.jsx`, use `Routes` and `Route` from `react-router-dom` to define your application's navigation structure:

```jsx
// App.jsx
import { lazy } from 'react';
import { Route, Routes } from 'react-router-dom';
import Layout from './components/Layout';
import Logout from './pages/Logout';
const Dashboard = lazy(() => import('./pages/Dashboard'));
const About = lazy(() => import('./pages/About'));
const PageNotFound = lazy(() => import('./pages/PageNotFound'));

const App = () => {
    return (
        <Routes>
            <Route path="/" element={<Layout />}>
                <Route index element={<Dashboard />} />
                <Route path="about/*" element={<About />} />
                <Route path="*" element={<PageNotFound />} />
            </Route>
            <Route path="logout" element={<Logout />} />
        </Routes>
    );
};

export default App;
```

- **Routes**: Container for all `Route` components.
- **Route**: Defines a path and the component to render. Nested routes can be used for layouts.
  - `<Layout />` Serves as a common layout for nested routes.
  - `<Dashboard />` Renders on the index route (`/`).
  - `<About />` Renders on the `/about/*` path, with support for nested routes.
  - `<PageNotFound />` Renders for any undefined paths (wildcard `*`).
  - `<Logout />` Renders on the `/logout` path.



But if `Dashboard`, `About`, and `PageNotFound` are rendered within the `Layout` component, where exactly are they rendered?

```jsx
// Layout.jsx
import { Suspense } from 'react';
import { Outlet } from 'react-router-dom';
import Navbar from './Navbar';
import Footer from './Footer';

const Layout = () => {
    return (
        <>
            <Navbar />
            <Suspense fallback={<Loading />}>
                <main>
                    <Outlet />
                </main>
            </Suspense>
            <Footer />
        </>
    );
};

export default Layout;
```

The `Layout` component serves as a common structure for your application's pages. It typically includes elements like a navigation bar and a footer. The child routes (e.g., `Dashboard`, `About`, `PageNotFound`) are rendered inside the `Layout` component using the `Outlet` component from `react-router-dom`.



Let's keep going with a further nested route by making the `About` page..

```jsx
// About.jsx
import { Route, Routes, Navigate, Outlet } from 'react-router-dom';
import { Suspense, lazy } from 'react';
import Loading from '../shared/Loading';
const GeneralInfo = lazy(() => import('./GeneralInfo'));
const Locations = lazy(() => import('./Locations'));

const About = () => {
    return (
        <Routes>
            <Route
                path="/"
                element={
                    <Suspense fallback={<Loading />}>
                        <Outlet />
                    </Suspense>
                }
            >
                <Route index element={<GeneralInfo />} />
                <Route path="locations" element={<Locations />} />
                <Route path="*" element={<Navigate replace to="/about" />} />
            </Route>
        </Routes>
    );
};

export default About;
```

The `About` component can include nested routes for more detailed sections like `GeneralInfo` and `Locations`. The `Navigate` component from `react-router-dom` is used to redirect any unmatched paths to a default route.

- **Suspense**: Provides a loading state (`<Loading />`) while the child components are being loaded.
- **Outlet**: Renders the nested routes (`GeneralInfo` or `Locations`).
- **Navigate**: Redirects any unmatched paths to the `/about` route, ensuring a fallback for invalid URLs under `/about`.



You'll note that when using the `react-router-dom` `Outlet` component we always wrap it in the React `Suspense` component and lazy load any component that will be rendered at `Outlet`. This can reduce the initial load time of your app.



