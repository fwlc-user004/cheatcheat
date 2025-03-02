# 🏗️ HTML5 Comprehensive Cheatsheet

## 🔹 Basic Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Hello, HTML5!</h1>
</body>
</html>
```

## 🔹 Meta Tags
```html
<meta name="description" content="A brief description of the page">
<meta name="keywords" content="HTML, CSS, JavaScript">
<meta name="author" content="Your Name">
<meta name="robots" content="index, follow">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## 🔹 Headings
```html
<h1>Main Heading</h1>
<h2>Subheading</h2>
<h3>Section Title</h3>
<h4>Subsection Title</h4>
<h5>Smaller Heading</h5>
<h6>Smallest Heading</h6>
```

## 🔹 Paragraphs & Line Breaks
```html
<p>This is a paragraph.</p>
<p>This is another paragraph with a line break.<br>This is a new line.</p>
```

## 🔹 Text Formatting
```html
<b>Bold</b>
<strong>Strong (SEO Friendly)</strong>
<i>Italic</i>
<em>Emphasized (SEO Friendly)</em>
<u>Underline</u>
<mark>Highlighted Text</mark>
<small>Smaller Text</small>
<del>Strikethrough</del>
<ins>Inserted Text</ins>
<sub>Subscript</sub>
<sup>Superscript</sup>
```

## 🔹 Links
```html
<a href="https://example.com">Clickable Link</a>
<a href="https://example.com" target="_blank">Open in New Tab</a>
<a href="mailto:someone@example.com">Send Email</a>
<a href="tel:+1234567890">Call Now</a>
<a href="#section">Jump to Section</a>
```

## 🔹 Images
```html
<img src="image.jpg" alt="Description of Image" width="300" height="200">
```

## 🔹 Lists
```html
<!-- Unordered List -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>

<!-- Ordered List -->
<ol>
    <li>First Item</li>
    <li>Second Item</li>
    <li>Third Item</li>
</ol>

<!-- Definition List -->
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
</dl>
```

## 🔹 Tables
```html
<table border="1">
    <tr>
        <th>Name</th>
        <th>Age</th>
        <th>City</th>
    </tr>
    <tr>
        <td>John</td>
        <td>30</td>
        <td>New York</td>
    </tr>
</table>
```

## 🔹 Forms
```html
<form action="submit.php" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <label for="message">Message:</label>
    <textarea id="message" name="message"></textarea>
    
    <input type="submit" value="Submit">
</form>
```

## 🔹 Form Elements
```html
<input type="text" placeholder="Text Input">
<input type="password" placeholder="Password">
<input type="email" placeholder="Email">
<input type="number" placeholder="Number">
<input type="date">
<input type="checkbox"> Check me
<input type="radio" name="option" value="1"> Option 1
<input type="radio" name="option" value="2"> Option 2
<select>
    <option>Option 1</option>
    <option>Option 2</option>
</select>
```

## 🔹 Semantic Elements
```html
<header>Website Header</header>
<nav>Navigation Menu</nav>
<main>Main Content</main>
<article>Article Content</article>
<section>Section Content</section>
<aside>Sidebar</aside>
<footer>Website Footer</footer>
```

## 🔹 Multimedia
```html
<!-- Audio -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
</audio>

<!-- Video -->
<video controls width="500">
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>
```

## 🔹 HTML5 APIs
```html
<!-- Geolocation API -->
<button onclick="getLocation()">Get Location</button>
<p id="location"></p>
<script>
    function getLocation() {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(function(position) {
                document.getElementById("location").innerHTML = "Latitude: " + position.coords.latitude + " Longitude: " + position.coords.longitude;
            });
        } else {
            alert("Geolocation is not supported by this browser.");
        }
    }
</script>
```

## 🔹 Accessibility (ARIA)
```html
<button aria-label="Close">X</button>
<nav role="navigation">Main Menu</nav>
```

## 🔹 Favicons
```html
<link rel="icon" type="image/png" href="favicon.png">
```

---