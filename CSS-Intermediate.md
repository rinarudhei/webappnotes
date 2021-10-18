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
  - **:hover** is for a when something is passed over by an input from the user, such as when a cursor moves over a link.
  - **:focus** is for when something gains focus, that is when it is selected by, or is ready for, keyboard input. 
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
- **:first-child**
- **:last-child**
- **:target**
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
- **:first-of-type()**
- **:nth-of-type()**
- **:nth-child()**

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

### **CSS Property: Background**
```css
.shorthand1 { url("bg.jpg") 20% 0% / 99px 33px repeat-y fixed content-box padding-box #fff; }
/* ...is the equivalent of... */
.longhand1 {
    background-image: url("bg.jpg");
    background-position: 20% 0%;
    background-size: 99px 33px;
    background-repeat: repeat-y;
    background-attachment: fixed;
    background-origin: content-box;
    background-clip: padding-box;
    background-color: #fff;
}

.shorthand2 { background: fuchsia; }
/* ...is the equivalent of... */
.longhand2 {
    background-color: fuchsia;
    background-image: initial; /* (none) */
    background-position: initial; /* (0% 0%) */
    background-size: initial; /* (auto) */
    background-repeat: initial; /* (repeat) */
    background-attachment: initial; /* (scroll) */
    background-origin: initial; /* (padding-box) */
    background-clip: initial; /* (border-box) */
}
```
### **Display**
- **inline**
  - Displays an element as an inline element. Any height and width properties will have no effect.
- **inline-block**
  - Displays an element as an inline-level block container. You CAN set height and width values.
- **block**
  - The element will start on a new line and occupy the full width available. And you can set width and height values.
- **none**
  - Display nothing
- **display: none** and **visibility: hidden** vary in that **display: none** takes the element’s box completely out of play, whereas **visibility: hidden** keeps the box and its flow in place without visually representing its contents. For example, if the second paragraph of 3 were set to **display: none**, the first paragraph would run straight into the third whereas if it were set to **visibility: hidden**, there would be a gap where the paragraph should be.

### **Pseudo Elements**
- **::first-letter**
- **::first-line**
- **::before** & **::after**
  - The **before** and **after** pseudo elements are used in conjunction with the content property to place content either side of a box without touching the HTML.

## **Page Layout**
#### **Positioning**
- **static** is the default value and renders a box in the normal order of things, as they appear in the HTML.
- **relative** is much like static but the box can be offset from its original position with the properties top, right, bottom and left.
- **absolute** pulls a box out of the normal flow of the HTML and delivers it to a world all of its own. In this crazy little world, the absolute box can be placed anywhere on the page using top, right, bottom and left.
- **fixed** behaves like absolute, but it will absolutely position a box in reference to the browser window as opposed to the web page, so fixed boxes should stay exactly where they are on the screen even when the page is scrolled.
#### **Floating**
- Floating a box will shift it to the right or left of a line, with surrounding content flowing around it.
- **float: left**
- **float: right**
- **float: none**
- Then, if you do not want the next box to wrap around the floating objects, you can apply the **clear** property:
- **clear: left** will clear left floated boxes
- **clear: right** will clear right floated boxes
- **clear: both** will clear both left and right floated boxes.