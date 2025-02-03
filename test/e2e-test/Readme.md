# End to end test

End-to-end (E2E) testing in React involves testing the entire application flow, from the user interface to the backend, to ensure that all components and systems work together as expected. E2E tests simulate real user interactions and verify that the application behaves correctly in a real-world scenario.  



## Common tools for E2E testing in React applications include:  

**Cypress:** A popular E2E testing framework that provides a rich API for interacting with the application and a powerful test runner.
**Selenium:** A widely-used tool for automating web browsers, often used for E2E testing.
**Puppeteer:** A Node library that provides a high-level API to control Chrome or Chromium over the DevTools Protocol.


## Cypress

Cypress is a modern, open-source end-to-end testing framework built for the web. It allows developers to write tests that simulate user
interactions in a real browser environment,
providing a powerful way to ensure your application
works as expected across different scenarios.

![Jest-Framework.webp](assets/cypress.png)

## Cypress testing 

```js
describe('My First Test', () => {
  it('Visits the app and checks for a specific element', () => {
    cy.visit('http://localhost:3000');
    cy.contains('Home Page').should('be.visible');
  });
});

```

```bash
npm run cypress:open
```