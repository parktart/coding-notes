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



## Tanstack react-query

### useQuery

1. **`isPending`**:
   - **When It's True**: This is true when there's no cached data and no query attempt has finished yet. Essentially, it indicates that the query is in an initial pending state, waiting to start fetching.
   - **Use Case**: Useful for showing a loading state when a query is about to begin, especially when no data from a previous fetch is available in the cache.
2. **`isLoading`**:
   - **When It's True**: This is true whenever the first fetch for a query is in-flight. It's a combination of `isFetching` and `isPending`, specifically for the initial loading of the query.
   - **Use Case**: Ideal for showing a loading state when a query is initially executed and there is no existing data in the cache. This is particularly useful for the initial render of a component where you're fetching data for the first time.
3. **`isFetching`**:
   - **When It's True**: This is true whenever the `queryFn` is executing. It includes both the initial pending and background refetches.
   - **Use Case**: Best used when you want to show a loading state during any data fetching activity, including the initial fetch and subsequent refetches (like after invalidation or as part of a refetch interval). This is more comprehensive than `isLoading` as it covers all instances of data fetching.

### useMutation

`status` property (string) -  the current state of the mutation `idle`, `pending`, `error`, or `success`



1. **`isIdle`**:
   - **True When**: The mutation is in its initial state and has not been triggered yet (`status === 'idle'`).
   - **Use Case**: Useful for cases where you need to check if a mutation is yet to start.
2. **`isPending`**:
   - **True When**: The mutation is currently executing (`status === 'pending'`).
   - **Use Case**: Ideal for showing loading indicators or disabling buttons while the mutation is in progress.
3. **`isSuccess`**:
   - **True When**: The mutation completed successfully (`status === 'success'`).
   - **Use Case**: Great for triggering success messages or actions that depend on the successful completion of the mutation.
4. **`isError`**:
   - **True When**: The mutation encountered an error (`status === 'error'`).
   - **Use Case**: Useful for displaying error messages or handling fallback logic when a mutation fails.

