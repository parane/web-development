# React Server Components (RSC)

React Server Components (RSC) are a new feature in React that allows components to be rendered on the server. This approach can improve performance and scalability by offloading some of the rendering work from the client to the server. 


## Key Concepts
Server-Side Rendering: Components are rendered on the server and sent to the client as HTML.
Streaming: The server can stream the rendered HTML to the client, allowing the client to start displaying content before the entire page is fully rendered.
Data Fetching: Data fetching can be done directly within the server components, reducing the need for client-side data fetching and state management.


```jsx

// app/page.js
import React from 'react';

// This is a server component
const Home = async () => {
    // Fetch data on the server
    const res = await fetch('https://api.example.com/data');
    const data = await res.json();

    return (
        <div>
            <h1>Home Page</h1>
            <pre>{JSON.stringify(data, null, 2)}</pre>
        </div>
    );
};

export default Home;

```

### Explanation:
The Home component is a server component.
Data is fetched directly within the component using fetch.
The component is rendered on the server and the HTML is sent to the client.

React Server Components allow you to build more efficient and scalable applications by leveraging server-side rendering and streaming.


# Client -Side Component in react 

Client-side components in React are components that are rendered on the client (browser) rather than on the server. These components are typically used for interactive parts of the application that require user interaction, state management, and dynamic updates. 

## Key Concepts
Rendering on the Client: Client-side components are rendered in the browser, allowing for dynamic updates and interactions.
State Management: These components can manage their own state using hooks like useState and useReducer.
Lifecycle Methods: Client-side components can use lifecycle methods (or hooks) such as useEffect to perform side effects like data fetching, subscriptions, or manual DOM manipulations.
Interactivity: They handle user interactions such as clicks, form submissions, and other events.

```jsx

import React, { useState, useEffect } from 'react';

const Counter = () => {
    const [count, setCount] = useState(0);

    useEffect(() => {
        document.title = `Count: ${count}`;
    }, [count]);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
};

export default Counter;
```

### Explantion
The Counter component is a client-side component.
It uses the useState hook to manage the count state.
The useEffect hook is used to update the document title whenever the count changes.
The component renders a button that increments the count when clicked.

```jsx
'use client';

import { useState } from 'react';

export default function LikeButton() {
    const [likes, setLikes] = useState(0);

    function handleClick() {
        setLikes(likes + 1);
    }

    return <button onClick={handleClick}>Like ({likes})</button>;
}
```


[more detail](https://nextjs.org/docs/app/building-your-application/rendering)