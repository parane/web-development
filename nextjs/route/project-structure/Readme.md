## Project structure

```md
my-next-app/
├── app/
│   ├── (auth)/
│   │   ├── components/
│   │   │   └── LoginForm.js
│   │   ├── pages/
│   │   │   └── login.js
│   │   ├── hooks/
│   │   │   └── useAuth.js
│   │   ├── services/
│   │   │   └── authService.js
│   │   └── styles/
│   │       └── auth.module.css
│   ├── dashboard/
│   │   ├── components/
│   │   │   └── Dashboard.js
│   │   ├── page.tsx
│   │   ├── hooks/
│   │   │   └── useDashboard.js
│   │   ├── services/
│   │   │   └── dashboardService.js
│   │   └── styles/
│   │       └── dashboard.module.css
│   ├── layout.tsx         // Global layout
│   ├── page.tsx           // Home page (route: /)
├── public/               // Static files (accessible at /)
├── styles/               // Global styles
│   └── globals.css
├── components/           // Shared components
│   └── Header.js
├── next.config.js        // Next.js configuration
├── package.json          // Project dependencies
└── README.md             // Project documentation
```

[Project Structure](https://nextjs.org/docs/app/getting-started/project-structure)


### Pages
In Next.js, the pages directory is used for file-based routing. Each file in this directory corresponds to a route in your application. This approach is straightforward and automatically creates routes based on the file structure.


```md
my-next-app/
├── app/
│   ├── about/
│   │   └── page.js       // About page (route: /about)
```
### Layouts

Layouts are used to define the structure of your application. They typically include common elements like headers, footers, and sidebars. In Next.js, you can create layout components that wrap your page components to provide a consistent look and feel across your application.

```md
my-next-app/
├── app/
│   ├── layout.js         // Global layout
│   ├── page.js           // Home page (route: /)
│   ├── about/
│   │   └── page.js       // About page (route: /about)
```

```jsx
// app/layout.js
import React from 'react';

const Layout = ({ children }) => {
    return (
        <div>
            <header>Header</header>
            <main>{children}</main>
            <footer>Footer</footer>
        </div>
    );
};

export default Layout;
```

```jsx
// app/page.js
import React from 'react';
import Layout from './layout';

const Home = () => {
    return (
        <Layout>
            <h1>Home Page</h1>
        </Layout>
    );
};

export default Home;

```


##