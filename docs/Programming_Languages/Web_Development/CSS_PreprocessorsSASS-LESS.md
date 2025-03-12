# 🎨 CSS Preprocessors: SASS & LESS Comprehensive Cheatsheet

## 🔹 Introduction
CSS Preprocessors like **SASS** and **LESS** extend CSS by adding features like **variables, nesting, mixins, functions, and more**. They help in writing **more maintainable and scalable** stylesheets.

---

## 🔹 Installation
### ✅ Install SASS:
```sh
npm install -g sass
```
Or use it via CLI:
```sh
sass input.scss output.css
```

### ✅ Install LESS:
```sh
npm install -g less
```
Or compile LESS to CSS:
```sh
lessc input.less output.css
```

---

## 🔹 Variables
### ✅ Definition:
Variables store reusable values like colors, fonts, and breakpoints.

### 📌 SASS:
```scss
$primary-color: #3498db;
body {
  background-color: $primary-color;
}
```

### 📌 LESS:
```less
@primary-color: #3498db;
body {
  background-color: @primary-color;
}
```

### 📌 Global vs Local Variables in LESS:
```less
@global-color: blue;
.container {
  @local-color: red;
  color: @local-color; // Only available inside .container
}
```

---

## 🔹 Nesting
### ✅ Definition:
Nesting allows writing CSS selectors inside other selectors, improving readability.

### 📌 SASS:
```scss
nav {
  ul {
    list-style: none;
  }
  li {
    display: inline;
  }
}
```

### 📌 LESS:
```less
nav {
  ul {
    list-style: none;
  }
  li {
    display: inline;
  }
}
```

---

## 🔹 Mixins
### ✅ Definition:
Mixins are reusable blocks of styles that can be included in multiple elements.

### 📌 SASS:
```scss
@mixin button-styles {
  background-color: #27ae60;
  color: white;
  padding: 10px;
}
button {
  @include button-styles;
}
```

### 📌 LESS:
```less
.button-styles() {
  background-color: #27ae60;
  color: white;
  padding: 10px;
}
button {
  .button-styles();
}
```

---

## 🔹 Functions & Operations
### ✅ Definition:
Functions perform operations like calculations on values.

### 📌 SASS:
```scss
$base-size: 16px;
h1 {
  font-size: $base-size * 2;
}
```

### 📌 LESS:
```less
@base-size: 16px;
h1 {
  font-size: @base-size * 2;
}
```

### 📌 Using Maps in SASS:
```scss
$colors: (
  primary: #3498db,
  secondary: #e74c3c,
  success: #2ecc71
);

button {
  background-color: map-get($colors, primary);
}
```

---

## 🔹 Loops & Conditionals
### ✅ Definition:
SASS & LESS support loops and conditionals for dynamic styles.

### 📌 SASS (Loops):
```scss
@for $i from 1 through 5 {
  .box-#{$i} {
    width: $i * 10px;
  }
}
```

### 📌 LESS (Loops):
```less
.loop (@i) when (@i <= 5) {
  .box-@{i} {
    width: (@i * 10px);
  }
  .loop(@i + 1);
}
.loop(1);
```

### 📌 SASS Conditionals:
```scss
$theme: dark;

body {
  @if $theme == dark {
    background: black;
    color: white;
  } @else {
    background: white;
    color: black;
  }
}
```

### 📌 LESS Conditionals:
```less
.box (@theme) when (@theme = dark) {
  background: black;
  color: white;
}
.box (@theme) when (@theme = light) {
  background: white;
  color: black;
}
```

---

## 🔹 Importing & Modules
### ✅ Using `@use` in SASS (Better than `@import`):
```scss
// _variables.scss
$primary-color: blue;

// main.scss
@use 'variables';
body {
  background: variables.$primary-color;
}
```

### ✅ Importing in LESS:
```less
@import "buttons.less";
```

---

## 🔹 Performance Optimization Tips
- **Avoid excessive `@extend` in SASS** to prevent large CSS output.
- **Minimize deep nesting in LESS** for better performance.
- **Modularize styles** and use `@import` or `@use` wisely.
- **Use maps and functions** in SASS instead of repetitive code.

---


