# 🎨 CSS3 & Flexbox/Grid Cheatsheet

## 🔹 Basic CSS Syntax
```css
selector {
    property: value;
}
```

## 🔹 CSS Selectors
```css
/* Universal Selector */
* { margin: 0; padding: 0; }

/* Element Selector */
p { color: blue; }

/* Class Selector */
.box { border: 1px solid black; }

/* ID Selector */
#unique { font-size: 20px; }

/* Attribute Selector */
input[type="text"] { border: 1px solid gray; }

/* Pseudo-class */
a:hover { color: red; }

/* Pseudo-element */
p::first-letter { font-size: 24px; }
```

---

## 🔹 CSS Box Model
```css
div {
    width: 200px;
    height: 100px;
    padding: 10px;
    border: 5px solid black;
    margin: 20px;
}
```

---

## 🔹 CSS Positioning
```css
div {
    position: relative; /* static, absolute, fixed, sticky */
    top: 10px;
    left: 20px;
}
```

---

## 🔹 CSS Display & Visibility
```css
div {
    display: block; /* inline, flex, grid, inline-block, none */
    visibility: hidden; /* visible, collapse */
}
```

---

## 🔹 CSS3 Flexbox
```css
.container {
    display: flex;
    justify-content: center; /* flex-start, flex-end, space-between, space-around */
    align-items: center; /* flex-start, flex-end, stretch */
    flex-wrap: wrap; /* nowrap, wrap-reverse */
    gap: 10px;
}

.item {
    flex: 1;
    min-width: 100px;
    background: lightblue;
    padding: 20px;
}
```

### Flex Properties
```css
.item {
    flex-grow: 1; /* Distribute available space */
    flex-shrink: 1; /* Shrink if necessary */
    flex-basis: 100px; /* Default size */
    align-self: flex-start; /* flex-end, center, stretch */
}
```

---

## 🔹 CSS3 Grid
```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
    grid-template-rows: auto 200px;
    gap: 10px;
}

.item {
    background: lightcoral;
    padding: 20px;
}
```

### Grid Item Placement
```css
.item {
    grid-column: span 2; /* Merges two columns */
    grid-row: 1 / 3; /* Starts at row 1 and ends at row 3 */
}
```

---

## 🔹 CSS3 Animations
```css
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.box {
    animation: fadeIn 2s ease-in-out;
}
```

---

## 🔹 CSS3 Transitions
```css
.button {
    transition: background-color 0.3s ease-in-out;
}

.button:hover {
    background-color: blue;
}
```

---

## 🔹 Media Queries (Responsive Design)
```css
@media (max-width: 600px) {
    body {
        background-color: lightgray;
    }
}
```

---