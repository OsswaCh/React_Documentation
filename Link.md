A `<Link>` is an element that lets the user navigate to another page by clicking or tapping on it. In `react-router-dom`, a `<Link>` renders an accessible `<a>` element with a real `href` that points to the resource it's linking to. This means that things like right-clicking a `<Link>` work as you'd expect. You can use `<Link reloadDocument>` to skip client side routing and let the browser handle the transition normally (as if it were an `<a href>`).

```jsx
import * as React from "react"; 
import { Link } from "react-router-dom"; 
function UsersIndexPage({ users }) { 
	return ( 
		<div>
			<h1>Users</h1> 
			<ul> 
			{users.map((user) => ( 
				<li key={user.id}> 
					<Link to={user.id}>{user.name}</Link> 
				</li> ))} 
			</ul>
		  </div> ); }
```

## Relative links
A relative `<Link to>` value (that does not begin with `/`) resolves relative to the parent route, which means that it builds upon the URL path that was matched by the route that rendered that `<Link>`. It may contain `..` to link to routes further up the hierarchy. In these cases, `..` works exactly like the command-line `cd` function; each `..` removes one segment of the parent path.

By default, links are relative to the route hierarchy (`relative="route"`), so `..` will go up one `Route` level from the current contextual route. Occasionally, you may find that you have matching URL patterns that do not make sense to be nested, and you'd prefer to use relative _path_ routing from the current contextual route path. You can opt into this behavior with `relative="path"`:

## preventScrollReset

If you are using [`<ScrollRestoration>`](https://reactrouter.com/en/main/components/scroll-restoration), this lets you prevent the scroll position from being reset to the top of the window when the link is clicked.
==> it just prevents the reset when the user clicks the link.

```jsx
<Link to="?tab=one" preventScrollReset={true} />
```

## History: TODO
## replace : TODO

## State
The `state` property can be used to set a stateful value for the new location which is stored inside [history state](https://developer.mozilla.org/en-US/docs/Web/API/History/state). This value can subsequently be accessed via `useLocation()`.

```jsx
<Link to="new-path" state={{ some: "value" }} />
```

You can access this state value while on the "new-path" route:

```jsx
let { state } = useLocation();
```