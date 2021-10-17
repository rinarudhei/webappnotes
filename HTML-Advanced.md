<a id="route"></a>
# **HTML Intermediate**

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

### <a id="Time-Mark-Presentational"></a>**Text: Time, Mark, and "Presentational"**

- **Time**
```html
<p>Written by Doctor Who on <time datetime="2052-11-21">Thursday 21st November 2052</time>.</p>
```
- **Mark**
```html
<blockquote>
    <p>He wants to play with his <mark>Legos</mark></p>
</blockquote>

<p>The person being quoted is clearly American because, for some odd reason, they pluralise "Lego".</p>
```

- **Presentational**
  - **hr**, no longer “horizontal rule”, is a thematic break, between paragraphs, for example, like those found in many a chapter of many a book.
small, used for small print. Arguably a fair point, “small print” has taken on a meaning beyond “print that is small”.
  - **s**, no longer “strikethrough”, is for text that is no longer correct (eg, this is <s>presentational, not</s> meaningful). Hmm. OK. Maybe. del still seems fine to most normals, though.
  - **u**, no longer “underline”, is for text that is unarticulated. It’s also “useless” but bonus point for the abbreviation remaining intact.
  - **i**, no longer “italic”, is for text in an alternate voice or representing a different quality of text. So, like, differently emphasized, then (see note below).
  - **b**, no longer “bold”, stands for “text to which attention is being drawn without conveying importance or suggesting an alternative voice” (and even that’s paraphrasing). b also stands for “bollocks.”
  - **sub** and **sup** are still subscript and superscript and yet, at the same time, they’re somehow not presentational anymore.

### <a id="Table"></a>**Table: Columns, Header & Footer**
- **colgroup** & **col**
  - These tags allow you to define the table columns and style them as desired, which is particularly useful if you want certain columns aligned or colored differently, as, without this, you would need to target individual cells.

```html
<table>
    <colgroup>
        <col>
        <col class="alternative">
        <col>
    </colgroup>
    <tr>
        <td>This</td>
        <td>That</td>
        <td>The other</td>
    </tr>
    <tr>
        <td>Ladybird</td>
        <td>Locust</td>
        <td>Lunch</td>
    </tr>
</table>
```

```html
<table>
    <colgroup>
        <col>
        <col span="2" class="alternative">
    </colgroup>
```
- **Caption interlude**
```html
<table>
    <caption>Locust mating habits</caption>
<!-- etc. -->
```
  - A caption will appear above the table by default, although using the CSS **caption-side: bottom** will, well, do what you would expect.
  - The mightier **figcaption** would be preferable to **caption** if you are marking up a table as the sole content of a **figure** element. See the Sectioning page for more.
  
- **Header and Footer**
  - **thead**, **tfoot** and **tbody** allow you to separate the table into header, footer and body, which can be handy when dealing with larger tables.

```html
<table>
    <thead>
        <tr>
            <td>Header 1</td>
            <td>Header 2</td>
            <td>Header 3</td>
        </tr>
    </thead>
    <tfoot>
        <tr>
            <td>Footer 1</td>
            <td>Footer 2</td>
            <td>Footer 3</td>
        </tr>
    </tfoot>
    <tbody>
        <tr>
            <td>Cell 1</td>
            <td>Cell 2</td>
            <td>Cell 3</td>
        </tr>
        <!-- etc. -->
    </tbody>
</table>
```

### <a id="Accessible-Links"></a>**Accessible Links**
- **Tabbing**
  - Users who do not or cannot use pointing devices can **tab** through links and, as such, links should be in a logical tabbing order. The **tabindex** attribute allows you to define this order although if the HTML is linear, as it should be, a logical tabbing order should automatically fall into place.
```html
<ul>
    <li><a href="here.html" tabindex="1">Here</a></li>
    <li><a href="there.html" tabindex="3">There</a></li>
    <li><a href="limbo.html" tabindex="2">Limbo</a></li>
</ul>
```
- **Link Titles**
  - If you have a link that isn’t self-descriptive, or the link destination could benefit from being explained in more detail, you can add information to a link using the **title** attribute.
  - **Another tip: Don’t have links open something in a new window or tab.** It’s precious to think your page is important enough to stay alive while a user visits elsewhere anyway. We all know how to use the back button. We know how to close windows and tabs, too, but if you can’t actually see that that’s what has happened…

- **Access Key**
  - Access keys allow easier navigation by assigning a keyboard shortcut to a link (which will usually gain focus when the user presses “Alt” or “Ctrl” + the access key).
```html
<a href="somepage.html" accesskey="s">Some page</a>
```
- **Skipping HTML**
  - To aid tabbing, you can supply links that allow users to jump over chunks of your web page. You might want to allow someone to jump over a plethora of navigation links, for example, so they can just read a page’s main content rather than cycle through all of the links:
```html
<header>
    <h1>The Heading</h1>
    <a href="#content">Skip to content</a>
</header> 

<nav>
    <!--loads of navigation stuff -->
</nav>

<section id="content">
    <!--lovely content -->
</section>
```
  - You probably won’t want this link to be displayed visually - it’s a peculiar link to see for abled-bodied users and screen reader users won’t need to see it (it will be read out). So you can use CSS to render it invisible but it could also be beneficial to those with motor disabilities so you might also want to consider making it visible when it has focus from being tabbed to using the **:focus** CSS pseudo class.

### <a id="Accessible-Forms"></a>**Accessible Forms**
- **Label**
  - Each form field should have its own explicit label. The **label** tag sorts this out, with a for **attribute** that associates it to a form element:
   - Both **name** and **id** attributs are typically required; the name for the form to handle that field and the id for the label to associate it to.
```html
<form>
    <label for="yourName">Your Name</label>
    <input name="yourName" id="yourName">
    <!-- etc. -->
```

- **Field set and Legend**
```html
<form action="somescript.php" >
    <fieldset>
        <legend>Name</legend>
        <p>First name <input name="firstName"></p>
        <p>Last name <input name="lastName"></p>
    </fieldset>
    <fieldset>
        <legend>Address</legend>
        <p>Address <textarea name="address"></textarea></p>
        <p>Postal code <input name="postcode"></p>
    </fieldset>
    <!-- etc. -->
```

- **Option Groups**
  - The **optgroup** element groups options in a select box. It requires a **label** attribute, the value of which is displayed as a non-selectable pseudo-heading preceding that group in the drop-down list of visual browsers.

```html
<select name="country">
  <optgroup label="Africa">
      <option value="gam">Gambia</option>
      <option value="mad">Madagascar</option>
      <option value="nam">Namibia</option>
  </optgroup>
  <optgroup label="Europe">
      <option value="fra">France</option>
      <option value="rus">Russia</option>
      <option value="uk">UK</option>
  </optgroup>
  <optgroup label="North America">
      <option value="can">Canada</option>
      <option value="mex">Mexico</option>
      <option value="usa">USA</option>
  </optgroup>
</select>
```

- **Navigating Fields**
  - Like links, form fields (and field sets) need to be navigated to without the use of a pointing device, such as a mouse. The same methods used in links to make this task easier can be used on form elements — tab stops and access keys.

  - The **accesskey** and **tabindex** attributes can be added to the individual form tags such as input and also to legend tags.
```html
<input name="firstName" accesskey="f" tabindex="1">
```
### <a id="HTML5-Part1"></a>**HTML5 Forms Pt.1: Input Types**
- **Search**
  - Used for a search query text box, this performs exactly as a standard text input should.
```html
<input type="search" name="search">
```

  - The main intention of the inclusion of this input type in the HTML5 specification is one of style. As well as making your HTML clearer, you can also target this element with a CSS attribute selector:

```css
input[type=search] { background: url(magnifyingglass.png) right no-repeat) }
```
- **Telephone, URL, and email addresses**
```html
<input type="tel" name="telephone_number">
<input type="url" name="web_address">
<input type="email" name="email_address">
```
  - You can use the **:valid** and **:invalid** CSS3 pseudo classes to style these fields depending on whether their content is considered valid.
  ```css
  input[type=email]:valid { background: green }
input[type=email]:invalid { background: red }
```

- **Number and Ranges**
```html
<input type="number" name="quantity" step="2" min="20" max="30">
```

  - You can use the **:valid** and **:invalid** pseudo classes in relation to this, too. If the user were to type “12”, for example, that would be invalid, because it isn’t between 20 and 30. If they typed “23” that would also be invalid because it isn’t a multiple of 2.
  - **range**
  ```html
  <input type="range" name="temperature" min="15" max="25" step="0.5" value="18.5">
  ```
### <a id="HTML5-Part2"></a>**HTML5 Forms Pt.2: Input Types**
  ### **More Attributes**
  - **Placeholder Text**
  - **Auto Focus**
  - **Data List**
    - A data list takes the form of a list of suggestions that accompanies a text field:

```html
<input name="country" list="country_name">
<datalist id="country_name">
    <option value="Afghanistan">
    <option value="Albania">
    <option value="Algeria">
    <option value="Andorra">
    <option value="Armenia">
    <option value="Australia">
    <option value="Austria">
    <option value="Azerbaijan">
    <!-- etc. -->
</datalist>
```

### <a id="Embedded-Content"></a>**Embedded Content: Video, Audio, and Canvas**
#### **Video**
```html
<video src="kitties.mp4" controls></video>
```

- **Poster**
  - You can specify a placeholder image, which will be displayed before the video is played, with the poster attribute.

- **Fallback Content**

  - Why, fall-back content: content that is displayed if the browser doesn’t understand the video element. That could be a few words, a chunk of HTML, or a “really funny” and “highly original” Lolcats image.
```html
<video src="kitties.mp4" controls>
    <img src="hahahaha.jpg" alt="Hilarious cat and caption saying 'soz'.">
</video>
```
- **Alternative Content**
```html
<video controls>
    <source src="kitties.mp4" type="video/mp4; codecs='avc1, mp4a'">
    <source src="kitties.webm" type="video/webm; codecs='vp8.0, vorbis'">
    <p>Browser no likey HTML 5.</p>
</video>
```
#### **Audio**
  - Applying audio is just like applying video. Using the audio tag, the structure is the same as using video and the attributes src, controls, autoplay and loop can all be used in the same way.
```html
<audio src="meow_mix.mp3" controls>
    Your stupid browser doesn't support HTML 5 audio.
</audio>
```
#### **Canvas**
  - A major addition to HTML5 is the canvas element. It is designed to provide a canvas onto which JavaScript can be used to paint all manner of dynamic images such as graphs, animated sprites, or daft cat pictures.
```html
<canvas id="wittykitty" width="800" height="450">
    <!-- Fall-back content here, just like with video and audio -->
</canvas>
```



