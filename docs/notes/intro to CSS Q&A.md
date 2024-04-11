---
id: hx38ccfnkh5riqkl0yh5q9t
title: intro to CSS Q&A
desc: ''
updated: 1712843796418
created: 1712759979012
---
- **What is the syntax for class and ID selectors?**
  - **_Class_**: .
  - **_ID_**: #

- **How would you apply a single rule to two different selectors?**
  - use both selectors in the rule, separated by comma

- **Given an element that has an id of title and a class of primary, how would you use both attributes for a single rule?**
  - chain them: .title#primary

- **What does the descendant combinator do?**
  - it selects elements that have the child property only where they are nested within the parent property

- **What are the names of the three ways to add CSS to HTML?**
  - external
  - internal/embedded
  - inline

- **What are the main differences between the three ways of adding CSS to HTML?**
  - external css can be applied to multiple html files
  - it keeps css and html files separate
  - internal css can only apply to the html file it is contained within
    - useful for applying styles to a single html file
    - can cause the file to get very large
  - inline CSS makes changes directly within the HTML element itself
    - not considered good practice:
      - it overrides both of the other two methods if they also exist
      - it is very difficult to maintain and update accurately
