# CSS styling

In Next.js, you can style your components using various methods, including CSS Modules, global CSS, tailwind and styled-components. Here are examples of each method:

(More Reference)[https://nextjs.org/learn/dashboard-app/css-styling]



## 1. Global CSS

Global CSS can be used to apply styles across the entire application.

If you look inside the /app/ui folder, you'll see a file called global.css. You can use this file to add CSS rules to all the routes in your application - such as CSS reset rules, site-wide styles for HTML elements like links, and more.

1. create a global css file , global.css in /app/ui

```css
body {
    margin: 0;
    font-family: Arial, sans-serif;
}
```

2. global styles to your application by navigating to /app/layout.tsx and importing the global.css file:

```tsx

import '@/app/ui/global.css';
 
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

If you take a look inside global.css, you'll notice some @tailwind directives:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## 2. Tailwind CSS

Tailwind CSS is a utility-first CSS framework that allows you to build custom designs without writing any CSS. To use Tailwind CSS in your Next.js application, you need to install the tailwindcss package:

```bash
npm install tailwindcss
```

Next, create a new file called Home.js in /app/ui and add the following code:

```jsx  
const Home = () => {
  return (
    <div className="flex items-center justify-center min-h-screen bg-gray-100">
      <h1 className="text-4xl font-bold">Home Page</h1>
    </div>
  );
};

export default Home;
```


## 3. CSS Modules

CSS Modules are a way to write CSS that's scoped to a single component. This means that you can write CSS without worrying about class name collisions or global styles affecting other components.

Inside /app/ui, create a new file called home.module.css and add the following CSS:

```css
.container {
    padding: 20px;
    background-color: #f0f0f0;
}
```

Next, import the CSS file into /app/page.tsx and apply the styles to the container div:

```tsx
import styles from '@/app/ui/home.module.css';
const Home = () => {
    return (
        <div className={styles.container}>
            <h1>Home Page</h1>
        </div>
    );
};

export default Home;
```


Tailwind and CSS modules are the two most common ways of styling Next.js applications. Whether you use one or the other is a matter of preference - 
you can even use both in the same application!
eg:
```tsx
<div className={`${styles.container} flex items-center justify-center min-h-screen bg-gray-100`}>
```


## 4. Styled Components

Styled-components allow you to write CSS-in-JS. CSS-in-JS libraries such as styled-jsx, styled-components, and emotion.

To use styled-components in your Next.js application, you need to install the styled-components package:

```bash
npm install styled-components
```

Create a new file called Home.js in /app/ui and add the following code:

```jsx
import styled from 'styled-components';
const Container = styled.div`
    padding: 20px;
    background-color: #f0f0f0;
`;

const Home = () => {
    return (
        <Container>
            <h1>Home Page</h1>
        </Container>
    );
};

export default Home;
```


## Conditional Styling with clsx


clsx is a utility for constructing className strings conditionally. It helps you combine multiple class names based on certain conditions, making it easier to manage dynamic class names in your components.

To use clsx in your Next.js application, you need to install the clsx package:

```bash
npm install clsx
```

Next, import clsx into your component and use it to conditionally apply class names:

```tsx
import clsx from 'clsx';

const Button = ({ primary, disabled }) => {
  return (
    <button
      className={clsx('btn', {
        'btn-primary': primary,
        'btn-disabled': disabled,
      })}
    >
      Click me
    </button>
  );
};

export default Button;
```

Conditional Classes: You can pass an object where the keys are class names and the values are boolean expressions. If the expression evaluates to true, the class name will be included in the final string.

Styled Components: Encapsulates styles within components, supports dynamic styling, and allows for CSS-in-JS.
clsx: Utility for conditionally combining class names, useful for managing dynamic class names without writing CSS-in-JS.
