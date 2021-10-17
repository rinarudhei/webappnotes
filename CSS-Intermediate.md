<a id="route"></a>
# **CSS Intermediate**

- **Date:** `10/17/2021`
- **Link: https://htmldog.com/guides/**
- **Contents:**
  - [Time, Mark, Presentational](#Time-Mark-Presentational)
  - [Table: Columns, Header & Footer](#Table)
  - [Accessible Links](#Accessible-Links)
  - [Accessible Forms](#Accessible-Forms)
  - [HTML Form Part1: More Attributes](#HTML5-Part1)
  - [HTML Form Part2: Input Types](#HTML5-Part2)
  - [Embedded Content](#Embedded-Content)

### **Pseudo Classes**
#### **Links**
  - **link**, targeting unvisited links, and **visited**, targeting, you guessed it, visited links, are the most basic pseudo classes.
```css
a:link {
    color: blue;
}

a:visited {
    color: purple;
}
```

#### **Dynamic Pseudo Classes**
  - **active** is for when something activated by the user, such as when a link is clicked on.
  - **hover** is for a when something is passed over by an input from the user, such as when a cursor moves over a link.
  - **focus** is for when something gains focus, that is when it is selected by, or is ready for, keyboard input. 
  -  **focus** is most often used on form elements but can be used for links. Although most users will navigate around and between pages using a pointing device such as a mouse those who choose note to, or are unable to do so, such as those with motor disabilities, may navigate using a keyboard or similar device. Links can be jumped between using a tab key and they will gain focus one at a time.

  ```css
  a:active {
    color: red;
}

a:hover {
    text-decoration: none;
    color: blue;
    background-color: yellow;
}

input:focus, textarea:focus {
    background: #eee;
}
```

#### **First Child**
- **first-child**
- **last-child**
- **target**
  - The **:target** CSS pseudo-class represents a unique element (the target element) with an id matching the URL's fragment
``` 
http://www.example.com/index.html#section2 
```
```html
<section id="section2">Example</section>
```
```css
:target {
  border: 2px solid black;
}
```
- **first-of-type()**
- **nth-of-type()**
- **nth-child()**

### **Shorthand Properties**
- **margin & padding**
```css
p {
    margin: 1px 5px 10px 20px;
}
```
- **borders**
```css
p {
    border: 1px red solid;
    border-width: 1px 5px 5px 1px;
    border-color: red green blue yellow;
}
```
- **fonts**
```css
p {
    font: italic bold 12px/2 courier;
}
```

