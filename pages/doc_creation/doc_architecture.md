---
title: Velma Document Setup
keywords: BEM, Docs, setup, architecture
last_updated: March 08, 2018
tags: [docs]
summary: "When we work at scale, we often find that we spend a large amount of our time deciphering, maintaining, and refactoring CSS. This is the reason we should focus so much on things like architectures, naming conventions, methodologies, etc.: because writing CSS is easy; looking after it is not."
sidebar: mydoc_sidebar
permalink: doc_architecture.html
folder: doc_creation
---
### **Document Architecture**

Print pieces should be created by using containers.  Containers help define document blocks and help to insulate the activities in one container from intruding into or contaminating other containers.   The following examples help illustrate the use of containers in a couple of flyer scenarios:
#### Example 1:
![Figure 1](https://docs.google.com/drawings/d/1X3DMOJ0E49rAhF5NqTmuGwcumygTbttj3oDps06ifrs/pub?w=903&amp;h=586)
#### Example 2:
![Figure 2](https://docs.google.com/drawings/d/1NqVHvLNoWtuM_2FanERWVnyubTWZ73WH8sSjMdmlQnY/pub?w=903&amp;h=586)

{% include warning.html content="Failing to create strict containers with   ```overflow: hidden```  styling could have very negative consequences." %}

Here’s how the HTML would look using the 2nd example:
![Figure 3](https://screencast-o-matic.com/screenshots/pp/VXh/1496174842858-82427.png)

As you can see, all elements are contained within a Section which is within a main document container, which is within the document body.  Every block element needs to be namespaced which we will cover in the next section.

Using the BEM model and thoughtfully laid out using tabbed nesting, a container’s ID and corresponding element and modifier classes can be quickly identified and edited:
![Figure 4](https://screencast-o-matic.com/screenshots/pp/VXh/1496188249601-88534.png)

{% include links.html %}
