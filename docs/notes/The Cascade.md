---
id: x1snd235gwi9ispqu08u0og
title: The Cascade
desc: ''
updated: 1712934226899
created: 1712932100370
---
## The CSS Cascade

- Rules sometimes conflict
  - Unexpected results
- Important to understand the Cascade to avoid this (the C in CSS - Cascading Style Sheets)

### Specificity

- More specific declarations take precedence over more general ones
  - Inline styles are the _most_ specific
  - Each type of selector has a level of specificity:
        1. ID selectors - most specific
        2. Class selectors
        3. Type selectors - least specific
  - A rule with a greater number of selectors of the same type will have precedence over one with fewer such selectors:

- E.g.:
  - both rules use only class selectors
    - Rule 2 has more class selectors so it is more specific
      - Therefore, rule 2 will take precedence and the font color displayed will be red

```html
<div class="main">
    <div class="list subsection">Red text</div>
</div>
```

```css
/* rule 1*/
.subsection {
    color: blue;
}

/*rule 2*/
.main .list {
    color: red;
}
```

- However, if we change subsection to an ID and select it in rule 1, it will take precedence over the class selectors in rule 2
  - ID always beats class

```html
<div class="main">
    <div class="list" id="subsection">Blue text</div>
</div>
```

```css
/* rule 1*/
#subsection {
    color: blue;
}

/*rule 2*/
.main .list {
    color: red;
}
```

```html
<div class="main">
    <div class="list" id="subsection">Red text on yellow background</div>
</div>
```

- In the following example, rule 1 uses only an ID, whereas rule 2 uses both a class and an ID
  - Neither rule has a more specific selector
    - Both have an ID selector so equal on that count
      - but rule 2 has more class selectors (1 vs 0) so it has higher specificity
        - Rule 2 takes precedence, so the font color will be red.
          - But the background colour in rule 1 will still be applied because there is no conflicting declaration in rule 2

```css
/* rule 1*/
#subsection {
    background-color: yellow;
    color: blue;
}

/*rule 2*/
.main #subsection{
    color: red;
}
```

- Both rules below have the same specificity:
  - rule 1 uses chaining (no space)
  - rule 2 uses a descendant combinator (space) but this adds nothing to the specificity

```css
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class .second-class {
  font-size: 24px;
}
```

- Likewise, the child combinator '>' here does not change the specificity

```css
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class > .second-class {
  font-size: 24px;
}
```

- Here the type selector (lowest specificity value) takes precedence over the universal selector (no specificity at all)

```css
/* rule 1 */
* {
  color: black;
}

/* rule 2 */
h1 {
  color: orange;
}
```

### Inheritance

- Certain properties applied to an element will be automatically inherited by the elements descendants
  - primarily typography properties, e.g.:
    - color
    - font-size
    - font-family

- Exception when an element is directly targeted
  - always beats inheritance
    - e.g. here, parent has higher specificity as it is an ID selector
      - but child (a class selector) will still apply the blue font colour applied because it is directly targeting the child element

```html
<div id="parent">
  <div class="child"></div>
</div>
```

```css
#parent {
  color: red;
}

.child {
  color: blue;
}
```

### Rule Order

- If all else is equal and two selectors are completely tied and there are still conflicting rules:
  - the rule defined last will take precedence
    - here the warning rule will be applied if there is a conflict as it is defined last

```css
.alert {
  color: red;
}

.warning {
  color: yellow;
}
```
