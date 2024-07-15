
>[!info] reference:  https://www.webrecto.com/react/navigate-to-another-page-on-button-click-in-react

The latest react-router version 6 introduced a `useNavigate()` hook. It is a part of the react-router-dom package and is imported into the application from the same package. 

==The `useNavigate()` hooks return a function that navigates the URL in the react application. This `navigate()` method allows programmatically routing inside the react project.==

>[!info] **Note:** In the latest version of react-router-dom, The useHistory() hook has been deprecated.


### Syntax
```jsx
import { useNavigate } from "react-router-dom"
const navigate = useNavigate()
navigate(to, { state={}, replace=false })
```
The navigate method takes two parameters:

**1:** The first parameter is to pass the page path the same as which location you want to open the page.

**2:** The second parameter is optional.

**navigate("/employee"):** It is navigate to a certain URL.

**navigate(-1):** It is navigate to the previous page.

**navigate(1):** It is navigate to the next page.

> **Note:** The navigate(-1) and navigate(1) method works the same as the browser back and forward button.

###  Redirect to another page on button click
```jsx
import React from 'react';
import { useNavigate } from "react-router-dom";

const Employee = () => {
  const navigate = useNavigate()

  const gotToNewPage=()=>{
    navigate("/customer");
  }
  return (
    <>
      <h3>Employee List</h3>
      <button onClick={() => gotToNewPage()} className="btn">Go to Customer Page</button>
    </>
  );
};
export default Employee;
```

## Using the condition to redirect the another page in the React

In this example, we use some logic to render the navigate() method to redirect the users to a different page. The navigate() function is called only if the `pagePath` state is true and if the `pagePath` state is false it will not redirect to any page.

```jsx
import React, {useState} from 'react';
import { useNavigate } from "react-router-dom";

const Employee = () => {
  const [pagePath, setPagePath] = useState(true)
  const navigate = useNavigate()

  const gotToNewPage=()=>{
    if(pagePath){
      navigate("/customer")
    }
    else{
      return null
    }
  }
  return (
    <>
      <h3>Employee List</h3>
      <button onClick={()=>gotToNewPage()} className="btn">Go to Customer Page</button>
    </>
  );
};
export default Employee;
```
