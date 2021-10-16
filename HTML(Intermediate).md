<a id="route"></a>
# **HTML & CSS**

- **Date:** `10/16/2021`
- **Link: https://htmldog.com/guides/**
- **Contents:**
  - [Abbreviations](#Abbreviations)
  - [Quotations](#Quotations)
  - [Citations](#Citations)
  - [Code](#Code)
  - [PreformattedText](#PreformattedText)
  - [MetaTags](#MetaTags)
  - [Tables: rowspan and colspan](#Tables:-rowspan-and-colspan)
  - [DescriptionList](#DescriptionList)
  - [Addresses](#Addresses)
  - [Definitions](#Definitions)
  - [BiDirectionalText](#BiDirectionalText)
  - [Editorial](#Editorial)

## **Beginner HTML**

### <a id="Abbreviations"></a>**Abbreviations**
- **abbr** is used to markup an abbreviation, a shortened form of a word or phrase.
```html
<p>This web site is about <abbr title="HyperText Markup Language">HTML</abbr> and <abbr title="Cascading Style Sheets">CSS</abbr>.</p>
```
### <a id="Quotations"></a>**Quotations**
- **blockquote** and **q** are used for quotations. blockquote is generally used for standalone often multi-line quotations whereas q is used for shorter, in-line quotations.
```html
<p>So I asked Bob about quotations on the Web and he said <q>I know as much about quotations as I do about pigeon fancying</q>. Luckily, I found HTML Dog and it said:</p>

<blockquote cite="http://www.htmldog.com/guides/html/intermediate/text/">
    <p>blockquote and q are used for quotations. blockquote is generally used for standalone often multi-line quotations whereas q is used for shorter, in-line quotations.</p>
</blockquote>

```
[back to top](#route)
- **Blockquotes** work very nicely with the HTML5 elements **figure** and **figcaption**, enabling a nice, semantic way to group a quotation with a citation:
```html
<figure>
    <blockquote>[Big old quotation about evolution]</blockquote>
    <figcaption>Charles Darwin</figcaption>
</figure>
```
### <a id="Citations"></a>**Citations**
- Just to make things nice and confusing, as well as a cite attribute, there is also a **cite** tag. This can be used to define the title of a work, such as a book.
```html
<p>According to <cite>the Bible</cite>, after six days God said <q>screw this for a lark, I'm having a nap</q>.</p>
```
[back to top](#route)
### <a id="Code"></a>**Code**
- **code** is used to represent any form of computer code. Further, **var** can be used for variables (which could be a variable in anything, not just in code - it could be a variable in an equation, for example), **samp** for sample output, and **kbd** (keyboard) for user input.
```html
<p>If you add the line <code><var>givevaderachuckle</var> = true;</code> to the <code>destroy_planet</code> subroutine and then type <kbd>ilovejabba</kbd> into the console, the big bad green Death Star laser will etch <samp>Slug Lover!</samp> on the planet's surface.</p>
```
[back to top](#route)
### <a id="PreformattedText"></a>**Preformatted Text**
- **pre** is preformatted text and is unusual in HTML tags that it takes notice of every character in it, including the white space (whereas other elements will ignore a consecutive space or a line-break, for example). It is most commonly used for blocks of code, where spacing, such as indentations, can be relevant.
```html
<pre><code>
&lt;div id="intro"&gt;
    &lt;h1&gt;Some heading&lt;/h1&gt;
    &lt;p&gt;Some paragraph paragraph thing thing thingy.&lt;/p&gt;
&lt;/div&gt;
</code></pre>
```
[back to top](#route)
### <a id="MetaTags"></a>**Meta Tags**
- Meta tags don’t do anything to the content that is presented in the browser window, but they are used by the likes of search engines to catalogue information about the web page.
```html
<head>
    <title>Air conditioners? YEAH conditioners!</title>
    <meta charset="utf-8">
    <meta http-equiv="refresh" content="3"><!--not recommended for sane people-->
    <meta name="description" content="This is my really, really, REALLY exciting web page about air conditioners">
```
[back to top](#route)
### <a id="Tables:-rowspan-and-colspan"></a>**Tables: rowspan and colspan**
```html
<table>
    <tr>
        <th>Column 1 heading</th>
        <th>Column 2 heading</th>
        <th>Column 3 heading</th>
    </tr>
    <tr>
        <td>Row 2, cell 1</td>
        <td colspan="2">Row 2, cell 2, also spanning Row 2, cell 3</td>
    </tr>
    <tr>
        <td rowspan="2">Row 3, cell 1, also spanning Row 4, cell 1</td>
        <td>Row 3, cell 2</td>
        <td>Row 3, cell 3</td>
    </tr>
    <tr>
        <td>Row 4, cell 2</td>
        <td>Row 4, cell 3</td>
    </tr>
</table>
```
[back to top](#route)
### <a id="DescriptionList"></a>**Description List**
```html
<h1>Some random glossary thing</h1>
<dl>
    <dt>HTML</dt>
    <dd>Abbreviation for HyperText Markup Language - a language used to make web pages.</dd>

    <dt>Dog</dt>
    <dd>Any carnivorous animal belonging to the family Canidae.</dd>
    <dd>The domesticated sub-species of the family Canidae, Canis lupus familiaris.</dd>

    <dt>Moo juice</dt>
    <dt>Cat beer</dt>
    <dt>Milk</dt>
    <dd>A white liquid produced by cows and used for human consumption.</dd>
</dl>
```
[back to top](#route)
### <a id="Addresses"></a>**Addresses**
- **address** should be used specifically for the contact details relating either to the entire web page (and so only used once) or to an **article** element
```html
<h3>Author contact details</h3>
<address>
<ul>
    <li>0123-456-7890</li>
    <li>author_dude@noplaceinteresting.com</li>
    <li>http://www.noplaceinteresting.com/contactme/</li>
</ul>
</address>
```
[back to top](#route)
### <a id="Definitions"></a>**Definitions**
- **dfn** is a definition term and is used to highlight the first use of a term. Like **abbr**, the **title** attribute can be used to describe the term.
```html
<p>Bob's <dfn title="Dog">canine</dfn> mother and <dfn title="Horse">equine</dfn> father sat him down and carefully explained that he was an <dfn title="A mutation that combines two or more sets of chromosomes from different species">allopolyploid</dfn> organism.</p>
```
[back to top](#route)
### <a id="BiDirectionalText"></a>**Bi-Directional Text**
- **bdo** can be used to reverse the direction of the text, and can be used to display languages that read right to left. The value of the required attribute **dir** can be **ltr** (left to right) or **rtl** (right to left).
```html
<bdo dir="rtl">god lmth</bdo>
```
[back to top](#route)
### <a id="Editorial"></a>**Editorial**
- **ins** and **del** are used to display editorial insertions and deletions respectively. Strictly speaking, they aren’t limited to text and can be used over whole swathes of content but, typically, they are used in moderation just like “Track Changes” feature in word processors tend to be.

- They can have the attributes **datetime** to indicate when the edit was made and cite, to point to a description as to why the edit has been made.
```html
<p>I have decided to <del datetime="2013-01-26">decrease</del> <ins cite="http://www.icecreamforall.com/changeofpolicy/">increase</ins> the amount of free ice cream that the State will provide for its citizens.</p>
```
- As with traditional word processor-based editing, the **ins** element is typically shown **underlined** and the **del** element is usually displayed with a **strikethrough**.

[back to top](#route)





