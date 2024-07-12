>[!info] version 
>this assumes react router v6

 Typically with nested routes, the parent `Route` acts as a wrapper over the child `Route`. This means that both the parent **and** the child `Route`s get rendered. In our example above, only the child `Route` is being rendered.

suppose you have a button that takes open a new view in the same page (if you look at obsidian side bar consider tha page names are the buttons and the pages are the nested children)

A real-life example of this UI could look similar to Twitter's [/messages](https://twitter.com/messages) route. When you go to `/messages`, you see all of your previous conversations on the left side of the screen. Then, when you go to `/messages/:id`, you still see all your messages, but you also see your chat history for `:id`.


Now, the last thing you need to do is tell React Router **where** in the parent `Route` (`Messages`) should it render the child `Route` (`Chats`).
To do this, you use React Router's [[Outlet]] component.

```jsx
import { Outlet } from "react-router-dom";

function Messages() {
  return (
    <Container>
      <Conversations />
      <Outlet />
    </Container>
  );
}
```

