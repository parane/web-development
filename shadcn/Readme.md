# Shadcn UI

**Purpose**: Shadcn is a modern CSS framework for beautifully designed components that you can copy and paste into your apps.

## Key Features

- **Shadow DOM**: Encapsulates styles and markup, ensuring that styles do not leak out and affect other parts of the application.
  ```html
  <template id="my-component">
    <style>
      :host {
        display: block;
        background-color: #f0f0f0;
        padding: 10px;
        border-radius: 5px;
      }
    </style>
    <div>
      <slot></slot>
    </div>
  </template>

  <script>
    class MyComponent extends HTMLElement {
      constructor() {
        super();
        const template = document.getElementById('my-component').content;
        const shadowRoot = this.attachShadow({ mode: 'open' });
        shadowRoot.appendChild(template.cloneNode(true));
      }
    }
    customElements.define('my-component', MyComponent);
  </script>


- **Custom Elements**: Define new HTML elements with custom behavior and styling. 
```html
<template id="scoped-styles">
  <style>
    :host {
      color: blue;
    }
    .inner {
      font-size: 20px;
    }
  </style>
  <div class="inner">
    Scoped styles example
  </div>
</template>

<script>
  class ScopedStyles extends HTMLElement {
    constructor() {
      super();
      const template = document.getElementById('scoped-styles').content;
      const shadowRoot = this.attachShadow({ mode: 'open' });
      shadowRoot.appendChild(template.cloneNode(true));
    }
  }
  customElements.define('scoped-styles', ScopedStyles);
</script>
```