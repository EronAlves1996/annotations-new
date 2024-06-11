```html
<html lang="en-US">
  <head></head>
  <body>
    <header></header>
    <main>Main content</main>
    <footer>Footer content<footer>
  </body>
</html>
```
```css
html, body {
    height: 100%;
}

body {
    display: flex;
    flex-direction: column;
}

main {   
    flex: 1 0 auto; 
}

footer {
    flex-shrink: 0;    
}
```