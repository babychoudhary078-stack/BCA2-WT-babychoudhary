# Day 9 — Images, Colors & Backgrounds

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 2 — HTML Fundamentals
🧪 **Lab Experiments:** 3 (continued), 4

---

## Learning Objectives

By the end of this session, students will be able to:
- Insert and configure images using the `<img>` tag
- Control image size with `width` and `height` attributes
- Apply background colors to pages and elements
- Change text and font colors using HTML attributes
- Create anchor links to the top of the page

---

## 1. Images in HTML (`<img>` Tag)

```html
<img src="path/to/image.jpg" alt="Description of image" width="300" height="200">
```

| Attribute | Required | Purpose |
|-----------|----------|---------|
| `src` | ✅ | Path/URL of the image |
| `alt` | ✅ | Alternative text (shown if image fails to load; used by screen readers) |
| `width` | Optional | Width in pixels or percentage |
| `height` | Optional | Height in pixels or percentage |
| `title` | Optional | Tooltip text on hover |

### Image Sources

```html
<!-- Local image (relative path) -->
<img src="images/photo.jpg" alt="My Photo">

<!-- Local image (from parent folder) -->
<img src="../images/logo.png" alt="Logo">

<!-- External image (URL) -->
<img src="https://via.placeholder.com/300x200" alt="Placeholder">
```

### Common Image Formats

| Format | Extension | Best For |
|--------|-----------|----------|
| **JPEG** | `.jpg`, `.jpeg` | Photographs (lossy compression) |
| **PNG** | `.png` | Graphics with transparency |
| **GIF** | `.gif` | Animated images, simple graphics |
| **SVG** | `.svg` | Scalable vector graphics (logos, icons) |
| **WebP** | `.webp` | Modern format (smaller file sizes) |

### Image Size Tips

```html
<!-- Fixed size in pixels -->
<img src="photo.jpg" alt="Photo" width="400" height="300">

<!-- Percentage (responsive) -->
<img src="photo.jpg" alt="Photo" width="100%">

<!-- Only set one dimension, the other auto-adjusts proportionally -->
<img src="photo.jpg" alt="Photo" width="400">
```

---

## 2. Colors in HTML

### Color Representation

| Method | Syntax | Example |
|--------|--------|---------|
| **Color Name** | `color="red"` | 147 named colors |
| **Hex Code** | `color="#FF0000"` | # + 6 hex digits (RRGGBB) |
| **RGB** | Used in CSS | `rgb(255, 0, 0)` |

### Common Color Names & Hex Codes

| Color | Name | Hex Code |
|-------|------|----------|
| 🔴 | `red` | `#FF0000` |
| 🟢 | `green` | `#008000` |
| 🔵 | `blue` | `#0000FF` |
| ⚫ | `black` | `#000000` |
| ⚪ | `white` | `#FFFFFF` |
| 🟡 | `yellow` | `#FFFF00` |
| 🟠 | `orange` | `#FFA500` |
| 🟣 | `purple` | `#800080` |

### How Hex Colors Work

```
#FF5733
 └┤└┤└┤
  R  G  B

R = FF (255) → Maximum Red
G = 57 (87)  → Some Green
B = 33 (51)  → Little Blue

Result: An orange-red color
```

---

## 3. Background Colors & Text Colors

### Page Background Color

```html
<body bgcolor="#F0F0F0">
    <!-- Light gray background for the entire page -->
</body>
```

### Text Colors with `<font>` Tag (Deprecated but in syllabus)

```html
<font color="red" size="5" face="Arial">Red text in Arial</font>
<font color="#0000FF" size="3">Blue text</font>
```

| Attribute | Purpose | Values |
|-----------|---------|--------|
| `color` | Text color | Name or hex code |
| `size` | Font size | 1 (smallest) to 7 (largest) |
| `face` | Font family | `Arial`, `Times New Roman`, etc. |

> ⚠️ The `<font>` tag and `bgcolor` attribute are **deprecated in HTML5**. Use CSS instead (Unit 4). We learn them here to understand the concept.

---

## Practical Session

### 🧪 Lab Experiment 4: Background Color & Back-to-Top Link

**Objective:** Change the background color of the page and create a link at the bottom that takes the user to the top of the page.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Colors and Navigation Demo</title>
</head>
<body bgcolor="#E8F5E9" id="top">

    <h1 align="center">
        <font color="#1B5E20">Mandsaur University</font>
    </h1>
    <h2 align="center">
        <font color="#388E3C">Department of Computer Applications</font>
    </h2>
    
    <hr>

    <h3><font color="#2E7D32">Section 1: About Us</font></h3>
    <p>
        Mandsaur University is a prestigious institution located in 
        <font color="blue"><b>Mandsaur, Madhya Pradesh</b></font>. 
        The university offers a wide range of programs across multiple disciplines.
    </p>
    
    <!-- Image inserted -->
    <p align="center">
        <img src="https://via.placeholder.com/500x300?text=Campus+View" 
             alt="University Campus" width="500">
    </p>

    <h3><font color="#2E7D32">Section 2: Our Programs</font></h3>
    <p>
        We offer <font color="red"><b>BCA</b></font>, 
        <font color="red"><b>BBA</b></font>, 
        <font color="red"><b>B.Tech</b></font>, and many more programs. 
        Each program is designed to provide students with practical skills 
        and theoretical knowledge.
    </p>

    <h3><font color="#2E7D32">Section 3: Facilities</font></h3>
    <p>Our state-of-the-art facilities include:</p>
    <p>
        &bull; Modern Computer Labs<br>
        &bull; High-speed Wi-Fi Campus<br>
        &bull; Digital Library<br>
        &bull; Smart Classrooms<br>
        &bull; Sports Complex<br>
        &bull; Hostel Accommodation
    </p>

    <h3><font color="#2E7D32">Section 4: Achievements</font></h3>
    <p>
        Our students have consistently performed well in national-level 
        competitions and have been placed in top IT companies. The university 
        has been recognized for its contribution to quality education.
    </p>

    <h3><font color="#2E7D32">Section 5: Contact</font></h3>
    <p>
        <font color="#333333">
        Mandsaur University<br>
        Rewas Dewda Road, Mandsaur<br>
        Madhya Pradesh - 458001<br>
        Phone: +91-XXXX-XXXXXX<br>
        Email: info@mandsauruniversity.edu.in
        </font>
    </p>

    <hr>
    
    <!-- Back to Top link -->
    <p align="center">
        <a href="#top"><b>&uarr; Back to Top</b></a>
    </p>

</body>
</html>
```

### 🧪 Lab Experiment 3 (Continued): Image Link Practice

Create a page with 3 images, each linking to a different page:

```html
<h2>Our Departments</h2>

<a href="bca.html">
    <img src="https://via.placeholder.com/200x150?text=BCA" 
         alt="BCA Department" width="200">
</a>

<a href="bba.html">
    <img src="https://via.placeholder.com/200x150?text=BBA" 
         alt="BBA Department" width="200">
</a>

<a href="btech.html">
    <img src="https://via.placeholder.com/200x150?text=B.Tech" 
         alt="B.Tech Department" width="200">
</a>
```

---

## Practice Exercise

Create `gallery.html` with:
1. Page background color set to a light shade
2. A title with a different font color
3. At least 5 images (use placeholder images)
4. Each image should have proper `alt` text
5. At least 2 images should be clickable links
6. Multiple sections with different colored headings
7. A "Back to Top" link at the bottom

---

## Summary

| Concept | Key Syntax |
|---------|-----------|
| Image | `<img src="path" alt="desc" width="N">` |
| Background color | `<body bgcolor="#color">` |
| Text color | `<font color="red">text</font>` |
| Hex colors | `#RRGGBB` (e.g., `#FF5733`) |
| Back to top | `<a href="#top">Back to Top</a>` with `id="top"` on body |
| Image formats | JPEG (photos), PNG (transparency), GIF (animation), SVG (vectors) |

---

*Day 9 of 55 | Unit 2 — HTML Fundamentals | Web Technology (25BCA060)*
