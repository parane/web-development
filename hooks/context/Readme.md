## React context 

Problem: Props drilling 

![home.jpg](asset/props-drill.gif)
Props drilling is a term used in React to describe the process of passing data from a parent component to a deeply nested child component through multiple layers of intermediate components. This can lead to a situation where intermediate components receive props that they do not need, solely for the purpose of passing them down to their children

React Context is a feature that allows you to share state and data across your application without having to pass props down manually through every level of the component tree. 
It is particularly useful for global data that many components need to access, such as themes, language preference, user information, or settings.

Key Concepts
- Context Creation: You create a context using React.createContext().
- Provider: The context provider component makes the context available to any components that need it. The context provider component wraps the child components that need access to the shared data. It typically accepts a value prop that holds the data you want to share. 
- Consumer: Components that need the context can access it using the useContext hook or the Context.Consumer component (older way to read context).


## updating context state 

To update React Context in a child component, you need to pass a function from the context provider that allows the child component to update the context value.

```jsx
import React, { createContext, useContext, useState } from 'react';

// Create a context with default values
const MyContext = createContext();

export function MyProvider({ children }) {
    const [value, setValue] = useState('default value');

    return (
        <MyContext.Provider value={{ value, setValue }}>
            {children}
        </MyContext.Provider>
    );
}
```

```jsx
function MyComponent() {
    const { value, setValue } = useContext(MyContext);

    return (
        <div>
            <p>Value: {value}</p>
            <button onClick={() => setValue('new value')}>Change Value</button>
        </div>
    );
}
```

```jsx
function App() {
    return (
        <MyProvider>
            <MyComponent />
        </MyProvider>
    );
}

export default App;
```

The problem with using an **object literal** ({}) directly in the value prop of a context provider is that it creates a new object on every render. This can cause unnecessary re-renders of the context consumers, even if the values inside the object haven't changed.

To avoid this, you can use the useMemo hook to memoize the context value and only update it when the dependencies change.

```jsx
import React, { createContext, useContext, useState, useMemo } from 'react';

const MyContext = createContext();

export function MyProvider({ children }) {
    const [value, setValue] = useState('default value');
    const contextValue = useMemo(() => ({ value, setValue }), [value]);

    return (
        <MyContext.Provider value={contextValue}>
            {children}
        </MyContext.Provider>
    );
}
```

#### Reference 

![react-context](https://ui.dev/react-context)