---
title: Container Blocks
keywords: container, BEM, document, creation, doc creation, blocks, container block
last_updated: March 8, 2018
tags: [docs]
summary: "Containers are the building blocks of print documents and are necessary for the proper viewing and publishing of library pieces. Created properly, containers will ensure the correct placement of objects on the page and will protect objects from malformed content in other containers. "
sidebar: mydoc_sidebar
permalink: doc_containerBlocks.html
folder: product1 --Options: mydoc, product1, product2
---

Foundational to all document containers is the parent container which will surround all other containers. The parent container ```#doc-container``` reinforces the document dimensions and will look similar to this:

```css
#doc-container {
    width: 8.5in;
    height: 11in;
    top: 0in;
    left: 0in;  
    position: relative;
    background-color: rgb(255, 255, 255);
    margin: 0 auto;
}
```

{% include links.html %}
