<a id="route"></a>
# **CSS Advanced**

- **Date:** `10/18/2021`
- **Link: https://htmldog.com/guides/**
- **Contents:**
  - [Universal, Child, and Adjacent Selectors](#Universal-Child-Adjacent-Selectors)
  - [At-Rules:@import, @media](#At-Rules)
  - [Attribute Selectors](#Attribute-Selectors)
  - [CSS Transitions](#CSS-Transitions)
  - [Transformation](#Transformations)

### <a id="Universal-Child-Adjacent-Selectors"></a>**Universal, Child, and Adjacent Selectors**
#### **Universal Selector**
- Using an asterisk (“ * ”), you can target everything under the sun. You can use it by itself to set global styles for a page, or as a descendant of a selector to set styles of everything within something.
```css
* {
    margin: 0;
    padding: 0;
}

#contact * {
    display: block;
}
```

#### **Child Selector**
- A greater-than symbol (“>”) can be used to specify something that is a child of something else, that is, something immediately nested within something.

- with this html
```html
<ul id="genus_examples">
    <li>Cats
        <ul>
            <li>Panthera</li>
            <li>Felis</li>
            <li>Neofelis</li>
        </ul>
    </li>
    <li>Apes
        <ul>
            <li>Pongo</li>
            <li>Pan</li>
            <li>Homo</li>
        </ul>
    </li>
</ul>
```
- and the following CSS
```css
#genus_examples > li { border: 1px solid red }
```
- …a red border would be drawn around “Cats” and “Apes” only, rather than around every single list item (which would be the case with #genus_examples li { border: 1px solid red }). This is because the likes of “Panthera” and “Felis” are grandchildren of “genus_examples”, not children.

#### **Adjacent Selectors**
- A plus sign (“+”) is used to target an adjacent sibling of an element, essentially, something immediately following something.

```html
<h1>Clouded leopards</h1>
<p>Clouded leopards are cats that belong to the genus Neofelis.</p>
<p>There are two extant species: Neofelis nebulosa and Neofelis diardi.</p>
```
```css
h1 + p { font-weight: bold }
```
- Only the first paragraph, that following the heading, will be made bold.
- A further, CSS 3, “general sibling” selector uses a tilde (“~”) and will match an element following another regardless of its immediacy. So, in the above example, h1 ~ p { font-weight: bold } will style all paragraphs after the top-level heading but if there were any ps preceding the h1, these would not be affected.

[back to top](#route)

### <a id="At-Rules"></a>**At-Rules: @import, @media, and @font-face**
- **@import**
  - is used to bolt another stylesheet onto your existing one. @import rules **must** be placed at the top of a stylesheet, before any other rules.
```css
@import url(morestyles.css);
```
- **@media**
  - @media can be used to apply styles to a specific media, such as print.

```css
  @media print {
    body {
        font-size: 10pt;
        font-family: times, serif;
    }

    #navigation {
        display: none;
    }
}
```
  - Values that follow “@media” can include **screen**, **print**, **projection**, **handheld**, and **all**, or a **comma-separated** list of more than one

  - You might also want to fiddle with a device’s viewport to get it to play how you want. Leaping back over to HTML, the following meta element will force a device to render a page at the width of the viewport (rather than attempting to show a wider-width design and zooming out, which it will do by default if the page can be wider than the viewport’s width) and also prevent the user from zooming in and out:

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```
- The benefit of this is that you can control exactly what is applied to what physical screen size. And although it’s painful to remove user controls, if the design is delightfully swell and made just for that diddy little screen, there shouldn’t be a need to zoom.

- The HTML Dog web site takes this approach: instead of a small device attempting to render a bigger, fatter web page by shrinking it down, the CSS turns it into a single-column design made specifically for such a device.

- **@font-face**
```css
@font-face {
  font-family: "font of all knowledge";
  src: local("font of all knowledge"), local(fontofallknowledge), url(fontofallknowledge.woff);
  font-weight: 400;
  font-style: normal;
}
```

[back to top](#route)

### <a id="Attribute-Selectors"></a>**Attribute Selectors**
```css
abbr[title] { border-bottom: 1px dotted #ccc }
```
```css
input[type=text] { width: 200px; }
```
```css
input[type=text][disabled] { border: 1px solid #ccc }
```

- [attribute^=something] will match a the value of an attribute that begins with something.
- [attribute$=something] will match a the value of an attribute that ends with something.
- [attribute*=something] will match a the value of an attribute that contains something, be it in the beginning, middle, or end.

```css
a[href^=http] {
    padding-right: 10px;
    background: url(arrow.png) right no-repeat;
}
```
[back to top](#route)

### <a id="CSS-Transitions"></a>**CSS Transitions**
- Transitions allow you to easily animate parts of your design without the need for the likes of JavaScript.

- The transition property, however, is much more powerful, allowing smooth animation (rather than a jump from one state to another). It is a shorthand property that combines the following properties (which can be used individually if you so choose):

- transition-property: which property (or properties) will transition.
- transition-duration: how long the transition takes.
- transition-timing-function: if the transition takes place at a constant speed or if it accelerates and decelerates.
- transition-delay: how long to wait until the transition takes place.
```css
a:link {
    transition: all .5s linear 0;
    color: hsl(36,50%,50%);
}
a:hover {
    color: hsl(36,100%,50%);
}
```
- For a transition to take place, only transition-duration is required, the rest defaulting to transition-property: all; transition-timing-function: ease; transition-delay: 0;. So you could, for example, simply declare transition: .5s.

#### **Targeting specific properties**
```css
a:link {
    transition: .5s;
    transition-property: color, font-size;
...
```
```css
a:link {
    transition: color .5s, font-size 2s;
...
```
#### **Easing**
- OK, so transition-timing-function (catchy!) is the least obvious fella. It effectively states how the browser should deal with the intermediate states of the transition.

- It follows a cubic Bézier curve. Yeah. Obviously, we know all about them from infant school, but, to get down to it, at the most basic level you can use ease or linear.

- **ease** produces a gradual acceleration at the start of the transition and a gradual deceleration at the end. **linear** maintains a constant speed throughout. Other values include ease-in and ease-out.

[back to top](#route)

### <a id="Transformations"></a>**Transformations**
```css
transform: rotate(-10deg);
```
```css
transform: skew(20deg,10deg);
```
```css
transform: scale(2);
transform: scale(1,2);
```
```css
transform: translate(100px,200px);
```
```css
transform: rotate(-10deg) scale(2);
```
  - The order of the values is important - the latter will be executed before the former. In the previous example, the box will be scaled and then rotated. It is, therefore, different to transform: scale(2) rotate(-10deg);, which will be rotated and then scaled.

  - Alternatively, you could use the **matrix** function. matrix does the whole lot - rotating, skewing, scaling, and translating. It takes six values:
```css
transform: matrix(2,-0.35,0.35,2,0,0);
```
  - **matrix**(https://www.w3.org/TR/css-transforms-1/#mathematical-description)

```css
transform-origin: 0 0;
```
  - And all of that’s just with two measly dimensions. transform is a leviathan with even greater power that can also be used for three-dimensional magic. On the most basic level, you can use rotateX and rotateY, which will rotate “towards” or “away” from you on the x- and y-axis, and there are the likes of translate3d, scale3d, and the intimidating matrix3d, all of which have even greater browser difficulties than their 2D counterparts.

[back to top](#route)

