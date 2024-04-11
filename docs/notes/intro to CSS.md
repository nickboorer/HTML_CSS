---
id: 7qfafap6x6ac8y4q1rjo05g
title: intro to CSS
desc: ''
updated: 1712838871808
created: 1712755462665
---
## Basic Syntax

- rules:
  - selector {
  - property: value pair;
    }

```css
div.bold-text {
    font-weight: 700;
}
```

### Selectors

- refer to the HTML elements that the rules apply to
  - the HTML that is being **selected**

#### Universal Selector

- an asterisk
- selects everything in the file:

```css
* {
    color: purple;
}
```

- Every element in the HTML element would have the colour purple applied

#### Type Selectors

- Select all elements of the specified type
- Simply the name of the element
- Here all of the div elements in the file would be selected and have the colour white applied:

```css
div {
    color: white;
}
```

#### Class Selectors

- Select all elements with the specified class
  - an attribute added to an element tag
  - same class can be added to a range of different elements and element types
  - an element can have multiple classes, each separated by a white space
- Here, all elements with the 'class="alert-text"' attribute would be selected and coloured red
  - Note that class selectors start with a full-stop, immediately followed by the name of the class:

```css
.alert-text {
    color: red;
}
```

#### ID Selectors

- Similar to class selectors
- Select all elements with the specified ID (another element that can be added to an HTML element tag)
- An element can only have one ID (unlike classes)
- IDs can be overused and classes should be used instead if possible
- ID selectors start with a hash rather than a full stop
- Here, we select the element with the 'id="title"' attribute and give it a red background:

```css
#title {
    background-color: red;
}
```

#### Grouping Selectors

- E.g., two groups of elements that share some attributes.
- Here, both the unread and read classes have the same white font and black background, but each then have several unique characteristics:

```css
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

- To avoid repetition, we can group the common design features together using the two selectors as a comma-separated list:

```css
.read,
.unread {
    color: white;
    background-color: black;
}

.read {
    /*Several unique declarations*/
}

.unread {
    /*Several unique declarations*/
}
```

#### Chaining Selectors

- Chain selectors as a list _without separation_, meaning that only elements that have attributes that match both of the selectors
- Can chain any combination of selectors
  - _except_ more than one type selector - an element cannot be two different types at the same time...
- Here, only elements that have the classes "subsection" and "header" will be selected:

```css
.subsection.header {
    color: red;
}
```

- Here, we chain a class (subsection) and an id (preview):

```css
.subsection#preview {
    color: blue;
}
```

#### Descendant Combinator

- Combinators combine multiple selectors which have a relationship
  - unlike chaining or grouping
- Descendant combinators use a single space between each selector
- Select elements that match the last selector as long as they have an ancestor (parent, grandparent) that matches the previous selector
- Here, we have two descendants of ancestor (child (A) and grandchild (B)) with the class "content"
  - there is also another div with the class "content" (C) that is not a descendant of "ancestor"

```html
<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<!-- C -->
<div class="contents"></div>
```

- The following descendant combinator will select elements A and B, because they are descendants of ancestor, but it will not select C

```css
.ancestor .contents {
    /*some declarations*/
}
```

### Properties

- An introductory list of commonly used properties:
  - color: - text colour
  - background-color: - background colour
    - Values:
      - keywords: red, transparent
      - HEX codes
      - RGB values
      - HSL values
  - font-family: font
    - single value or comma-separated list
      - font family name e.g., "Times New Roman"
      - generic family name e.g., serif
    - best practice to include a list, starting with most desired font and moving to a generic font family as a fallback:
            'font-family: "Times New Roman", serif;'
  - font-size: - value should not contain whitespace: 'font-size: 22px'
  - font-weight: boldness of the text
    - Values: keywords e.g., 'bold' or number up to 1000 (usually increments of 100): 'font-weight: 700'
  - text-align: - aligns text horizontally within the element e.g., 'text-align: center;'
  - image height and width - to avoid distorting the image, if you want to change its size from the default original size, you should set its height to auto and then specify the width
    - Even if the original size is being retained, explicitly declaring these values makes the page load faster and means that it doesn't suddenly change the size and layout of the page when it loads last
      - the declaration ensures that space is reserved for the image to load into
    - Here, we are resizing an image with a 500px height and 1000px width. The declarations below mean that the height it now 250px because the aspect ratio is preserved:

```css
img {
    height: auto;
    width: 500px;
}
```

### Adding CSS to HTML

- Three methods:
  - External CSS
  - Internal CSS
  - Inline CSS - avoid!

#### External CSS

- A separate file for CSS - usually called 'styles.css' (doesn't have to be though!)
  - Linked inside of the HTML head element with a self-closing link element
    - href = location of css file
    - rel specifies relationship between HTML file and linked file (required)

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

- Keeps HTML and CSS separated - smaller and cleaner HTML file
- Only need to edit CSS in one place - handy where several pages in a website share the same styles

#### Internal CSS

- Instead of a separate CSS file, the CSS is added directly into the HTML file inside a pair of style tags within the head element
  - No link element is needed because there is no file to link to

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>
  ...
</body>
```

- Useful for adding styles to a single page of a website
- Can inflate size of HTML drastically

#### Inline CSS

- Styles applied directly to HTML elements
- Strongly discouraged
  - quickly gets very messy
  - requires a lot of repetition if applying the same style to several elements
    - bloat
    - very difficult to change, troubleshoot or update
  - overrides the other two methods - unexpected results

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```
