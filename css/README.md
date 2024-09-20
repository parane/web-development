# CSS (Cascading Style Sheets)

**Purpose**: CSS is used to style and layout web pages, including the design, colors, and fonts.

## Key Features

- **Selectors**: Target HTML elements to apply styles.
  ```css
  p {
    color: blue;
  }
  ```

- **Box Model**: Defines the layout and spacing of elements.
  ![CSS.png](assets/CSS-Box-Model.webp)

  ```css
  div {
    width: 100px;
    padding: 10px;
    border: 5px solid black;
    margin: 20px;
  }

- **Flexbox and Grid**: Modern layout systems for creating complex designs.

![CSS.png](assets/grid.webp)

  ```css
  /* Flexbox */
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /* Grid */
  .grid-container {
    display: grid;
    grid-template-columns: auto auto auto;
  }
    ```

- **Responsive Design**: Media queries allow for different styles based on screen size.
```css
@media (max-width: 600px) { 
    body { 
        background-color: lightblue; 
    } 
} 
```

- **Animations and Transitions**: Create dynamic effects and animations
```css
.box { 
    width: 100px; 
    height: 100px; 
    background-color: red; 
    transition: width 2s; 
} 

.box:hover { 
    width: 200px; 
}
```
