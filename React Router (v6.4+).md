you can follow using the following recourses
https://reactrouter.com/en/main/start/tutorial (tutorial)


## Adding a router
```jsx
import * as React from "react";
import * as ReactDOM from "react-dom/client";
import {
  createBrowserRouter,
  RouterProvider,
} from "react-router-dom";
import "./index.css";

const router = createBrowserRouter([
  {
    path: "/",
    element: <div>Hello world!</div>,
  },
]);

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
);

```


what to add
```jsx
import { createBrowserRouter, RouterProvider, } from "react-router-dom";
//rest of the code
const router = createBrowserRouter([ 
	{ path: "/",
	 element: <div>Hello world!</div>, 
	 }, ]);
//rest of the code
<React.StrictMode> 
	<RouterProvider router={router} /> 
</React.StrictMode>
```

>[!info] Root route
This first route is what we often call the "root route" since the rest of our routes will render inside of it. It will serve as the root layout of the UI, we'll have nested layouts as we get farther along.

## Not found errors
this happens when you type in an invalid 
**Set the `<ErrorPage>` as the [`errorElement`](https://reactrouter.com/en/main/route/error-element) on the root route**
![[Pasted image 20240712112604.png]]

code to add 
```jsx
import ErrorPage from "./error-page";
//rest of code
const router = createBrowserRouter([ 
	{ path: "/", 
	element: <Root />, 
	errorElement: <ErrorPage />, //add this line of code
	 }, ]);
```

this or you can create your own error page component and insert it instead of <ErrorPage />

## Linking other pages
```jsx 
import Contact from "./routes/contact"; 
const router = createBrowserRouter([ 
{ 
 path: "/", 
 element: <Root />, 
 errorElement: <ErrorPage />, 
 }, 
 { 
 path: "contacts/:contactId", 
 element: <Contact />, 
 }, 
 ]);
```
Now if we click one of the links or visit `/contacts/1` we get our new component!

## [[nested route]]
```jsx 
const router = createBrowserRouter([ 
{ 
	path: "/", 
	element: <Root />, 
	errorElement: <ErrorPage />, 
	children: [ 
		{ 
			path: "contacts/:contactId", 
			element: <Contact />, 
			}, 
		], 
	}, ]);
```

 We need to tell the root route _where_ we want it to render its child routes. We do that with [[Outlet]](https://reactrouter.com/en/main/components/outlet)
 

## [[Client side routing]] 

 when we click the links in the sidebar, the browser is doing a full document request for the next URL instead of using React Router.

Client side routing allows our app to update the URL without requesting another document from the server. Instead, the app can immediately render new UI. Let's make it happen with [`<Link>`](https://reactrouter.com/en/main/components/link) [[Link]].

## unstable_viewTransition

>[!info] 
The **View Transitions API** provides a mechanism for easily creating animated transitions between different website views. This includes animating between DOM states in a single-page app (SPA), and animating the navigation between documents in a multi-page app (MPA).

The `unstable_viewTransition` prop enables a [View Transition](https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API) for this navigation by wrapping the final state update in `document.startViewTransition()`:

```jsx
<Link to={to} unstable_viewTransition>
  Click me
</Link>
```
If you need to apply specific styles for this view transition, you will also need to leverage the [`unstable_useViewTransitionState()`](https://reactrouter.com/en/main/hooks//use-view-transition-state) hook (or check out the `transitioning` class and `isTransitioning` render prop in [NavLink](https://reactrouter.com/en/main/components/nav-link)):

## Loaders
https://www.youtube.com/watch?v=K-bxVELldCc&t=62s

only work with new versions of the router that have the **createBorwserRouter**
- a way we can load stuff into a component before it renders 
- if  i have a page that loads data from an API --> loaders would allow us to fetch that data into the app before the component renders in the brower --> inside the component we wiont have to use hooks like use effect to fetch the data (no loading into local states as well ) 

creating the loader

this can be in any file because it is exported
```jsx
// data loader: loading data from an api
export const careersLoader = async () => {
  const res = await fetch('http://localhost:4000/careers')

  return res.json()
}
```

the component that uses the data
```jsx
import { Link, useLoaderData } from "react-router-dom"

export default function Careers() {
  const careers = useLoaderData()

  return (
    <div className="careers">
      {careers.map(career => (
        <Link to='/' key={career.id}>
          <p>{career.title}</p>
          <p>Based in {career.location}</p>
        </Link>
      ))}
    </div>
  )
}

```

the router
```js
import Careers, { careersLoader } from './pages/careers/Careers'

//rest of the code 

const router = createBrowserRouter(
  createRoutesFromElements(
    <Route path="/" element={<RootLayout />}>

      </Route>
      <Route path="careers" element={<CareersLayout />}>
        <Route 
          index 
          element={<Careers />} 
          loader={careersLoader} //line to direct the loader  
        />
      </Route>
</Route>
  )
)
```

TODO: finish the form part

