https://legacy.reactjs.org/docs/context.html#contextprovider

[Context API](https://reactjs.org/docs/context.html#contextprovider) is meant for **sharing state** in the component tree.

> Context provides a way to **pass data through the component tree** without having to pass props down manually at every level.


> When React renders a component that subscribes to this Context object it will read the current context value from the closest matching `Provider` above it in the tree.


1. **Context Creation**: When you create a context using `React.createContext()`, you define a `Context` object that holds a `Provider` and a `Consumer` component. This object doesn't immediately store any value but sets up a system to pass values down the component tree.
    
2. **Provider Component**: The `Provider` component is where the context value is stored. It takes a `value` prop, which can be any data type (object, array, primitive value, etc.). This value is stored in the React component tree, specifically within the `Provider` component.
    
3. **Consumer or `useContext` Hook**: When a component consumes the context using the `Consumer` component or the `useContext` hook, React internally reads the value from the nearest matching `Provider` component up the tree. This value is fetched from memory, where React maintains the current state of the application.
    
4. **Memory Management**: React handles the storage and memory management of context values internally. Context values exist in memory as long as the React application is running, and the `Provider` is rendered. When the component tree updates, React recalculates which components need to re-render based on the context value changes.
    

In summary, React contexts are stored in the component tree's memory, within the `Provider` component, and are accessed by consumers throughout the tree.

[Local Storage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) is for storing data between sessions.

> The read-only localStorage property allows you to access a Storage object for the Document's origin; **the stored data is saved across browser sessions**.


