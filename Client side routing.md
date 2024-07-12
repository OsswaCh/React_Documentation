Client-side routing is a fundamental concept in modern single-page applications (SPAs) that allows for navigation within the application without a full page reload.

 the performance on the frontend of a website is directly affected by things like the number of pages loaded initially, the amount of data fetched and displayed, and the time taken to switch from one page to another. Client-side _rendering_ and _routing_ give a subtle sense performance of your application, and it's essential to use the power of your frontend framework to your advantage

Client-side routing is handled solely by JavaScript on the page. Whenever a user clicks on a link, the URL bar changes and a different view is rendered on the page. This view could be anything—JSX or HTML. Single-page applications give a ==smooth sense of navigation as they don't refresh the whole page when a route is performed==. Even when a request is made to the server to fetch data, it only seems as if static HTML pages are rendered on the frontend. Thus, single-page applications are direct beneficiaries of client-side routing, and this is one major reason for their growing popularity and delivery of great user experience.

### Pros

- Routing between components is fast as the amount of data that renders is less. The rest of the data is rendered by the DOM, and even when there's tons of HTML and CSS to render, the DOM handles that part in the blink of an eye. Using lazy loading, any delay in rendering HTML is compensated for.
- For better user experience, animations and transitions can be easily implemented when switching between different components.
- It gives a real sense of a single-page application in action. No separate pages are rendered, and the current page doesn't refresh to load a new view.

### Cons

- The initial loading time is considerably large as all the routes, components, and HTML have to be loaded at once when the application first mounts . The whole website or web app needs to be loaded on the first request.
- There is unnecessary data download time for unusable views that cannot be anticipated on the first render of the application.
- It generally requires an external library, which means more code and more dependency on external packages, unlike routing on the server-side.
- Client-side routing and rendering convert JavaScript to HTML, making search engine crawling less optimized.