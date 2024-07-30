
>[!info] Reference: https://react.dev/reference/react/useContext


`useContext` is a React Hook that lets you read and subscribe to [context](https://react.dev/learn/passing-data-deeply-with-context) from your component.
```jsx 
const value = useContext(SomeContext)
```

#### Parameters [](https://react.dev/reference/react/useContext#parameters "Link for Parameters")

- `SomeContext`: The context that you’ve previously created with [`createContext`](https://react.dev/reference/react/createContext). The context itself does not hold the information, it only represents the kind of information you can provide or read from components.
#### Returns [](https://react.dev/reference/react/useContext#returns "Link for Returns")

`useContext` returns the context value for the calling component. It is determined as the `value` passed to the closest `SomeContext.Provider` above the calling component in the tree. If there is no such provider, then the returned value will be the `defaultValue` you have passed to [`createContext`](https://react.dev/reference/react/createContext) for that context. The returned value is always up-to-date. React automatically re-renders components that read some context if it changes.

- `useContext()` call in a component is not affected by providers returned from the _same_ component. The corresponding `<Context.Provider>` **needs to be _above_** the component doing the `useContext()` call.
- React **automatically re-renders** all the children that use a particular context starting from the provider that receives a different `value`. The previous and the next values are compared with the [`Object.is`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is) comparison. Skipping re-renders with [`memo`](https://react.dev/reference/react/memo) does not prevent the children receiving fresh context values.


## Usage

### Passing data deeply into the tree [](https://react.dev/reference/react/useContext#passing-data-deeply-into-the-tree "Link for Passing data deeply into the tree")

Call `useContext` at the top level of your component to read and subscribe to [context.](https://react.dev/learn/passing-data-deeply-with-context)

``` jsx
import { useContext } from 'react';
function Button() 
	{  const theme = useContext(ThemeContext);  // ...
```

To pass context to a `Button`, wrap it or one of its parent components into the corresponding context provider:

``` jsx
function MyPage() {  
	return (    
		<ThemeContext.Provider value="dark">      
			<Form />    
		</ThemeContext.Provider>  );}
		
function Form() {  // ... renders buttons inside ...}
```

It doesn’t matter how many layers of components there are between the provider and the `Button`. When a `Button` _anywhere_ inside of `Form` calls `useContext(ThemeContext)`, it will receive `"dark"` as the value.