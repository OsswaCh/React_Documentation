(ps: I am merely documenting what i learn as go, this is by no means a tutorial)

Important Notice: 
- The follwoing uses react router V6.4+
- React 18.2.0


## Protected Routes
view [[React Router (v6.4+)]]

Protected routes are **routes in a web application that require the user to be authenticated before they can access them**. These routes are typically used to protect sensitive or private content that should only be accessible to authenticated users

how i'm doing it so far 
```jsx
//ProtectedRoute.jsx

import React, {useState} from 'react'
import { Navigate } from 'react-router-dom'

function ProtectedRoute({children, ...rest}) {
  const [user, setUser] = useState(null);
  if (!user) {
    return <Navigate to="/" />}
  return children
} 
export default ProtectedRoute;
```



```jsx
import React from 'react';
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

function App() {

// Define the routes
const router = createBrowserRouter([
  {
    path: '/',
    element: <Login />,
    errorElement: <PageNotFound />,
  },
  {
    path: '/creation-de-compte',
    element: (
      <React.Fragment>
        <ProtectedRoute />
        <AccountCreation />
      </React.Fragment>
    ),
  },
  {
    path: '/test',
    element: <TestPage />,
  },
  {
    path: 'dashboard',
    element:  
    <React.Fragment>
        <ProtectedRoute />
        <Dashboard />
      </React.Fragment>,
  },
]);
  return (
    <div>
      {/* deffer the entry point of the app to react router define above */}
      <RouterProvider router={router} />
    </div>
  );
}
export default App;
```

## preventDeafault

The preventDefault function is a key player in React event handling. Utilized within event handlers, it **lets you control the default actions the browser typically executes**. This control over events, specifically form submissions, is essential for creating a dynamic and responsive React app.

```jsx
const handleSubmit = (e) => { 
	e.preventDefault(); // Here you would typically handle the login logic 
	console.log("Login attempt with:", email, password); 
	};
```