---
title: Markdown language
subtitle: 

# Summary for listings and search engines
summary: 

# Link this post with a project
projects: []

# Date published
date: '2022-05-10T00:00:00Z'

# Date updated
lastmod: ''

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin

tags:
  - Academic

categories:
  - Demo
---

## **What is Markdown?**

Markdown is a text markup language. Such texts are easy to write and read. They can be easily converted to HTML. Most programmers prefer Markdown for writing documentation, describing their projects, writing blogs, and so on.

## **What does it mean?**

A "markup language" is simply a set of conventions, rules.

Let's say you're texting a friend. They cannot make text bold or italic. You agree with a friend: if I write *something* like this between the asterisks, then consider it as italic text. And if I write **something** between two asterisks, then consider that this is bold text. You made up the rules.

Markdown is a set of such rules.

The rules are clear to different programs and sites. For example, the "Questions and Answers" in the Hexlet lessons support Markdown. This means that you can write texts there according to Markdown rules, and after clicking “Submit”, the markup will become real: text in single asterisks will become italic, text in double asterisks will become bold, and so on. This is the conversion from Markdown to HTML.

## **Why is this needed?**

1. To add markup where no real markup is possible. For example, in a simple text file or in the same SMS, where it is impossible to bold, create headings, highlight quotes, etc.
2. For more convenient writing of texts for subsequent conversion to HTML or other formats.

## **Markdown Syntax**

This is a quick reference to the basic elements of Markdown syntax. There is no single standard, and different versions of Markdown may differ in details. But the basic elements from the list below are supported in all standards.

### **Text selection**

*This text will be italic*</br>
_This text will be italic_

**This text will be bold**</br>
__This text will be bold__

_You can **insert** one type into another

### **Headers**

# This is the largest heading, it turns into an <h1> tag

'##' <h2>
'###' <h3>
'####' <h4>
'#####' <h5>
'######' <h6>

### **Links**

https://hexlet.io - the text of a simple link will become a clickable link automatically
You can make any text a link:

'[This is a Hexlet link]'(https://hexlet.io)

### **Quote**

'>' This is a wise quote</br>
'>' A wise man.

### **Pictures**

'![This is optional alt text]'(/assets/images/markdown/markdown.png)
The code
To highlight code (or any unformatted text), special characters are used - back ticks: `

Sometimes you need to add a piece of code `function(12);` to a regular line of text.
And sometimes you need to insert a whole block of code:

```javascript
const func = (num) => {
  if (num > 0) {
    return num - 1;
  }
  return num + 1;
};
```

### **Lists**

Unnumbered list:

'*' Paragraph
'*' One more item
  '*' Subitem
  '*' Another subitem</br>
Numbered list:

'one.' Paragraph
'one.' One more item
  'one.' Subparagraph
  'one.' Another subparagraph</br>
You can use any numbers in a numbered list - it doesn't matter. When converted to HTML or another format, the numbers will become correct and consistent (1, 2, 3, etc.).

More about Markdown</br>
[Markdown on Wikipedia](https://ru.wikipedia.org/wiki/Markdown)