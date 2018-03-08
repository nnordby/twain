---
title: Introduction to Object Oriented CSS
keywords: OOCSS, Object Oriented CSS, BEM, Docs, setup
last_updated: April 27, 2017
tags: [docs]
summary: "When we work at scale, we often find that we spend a large amount of our time deciphering, maintaining, and refactoring CSS. This is the reason we should focus so much on things like architectures, naming conventions, methodologies, etc.: because writing CSS is easy; looking after it is not."
sidebar: mydoc_sidebar
permalink: doc_OOCSS.html
folder: doc_creation
---
### **Introduction to Object Oriented CSS**

When we work at scale, we often find that we spend a large amount of our time deciphering, maintaining, and refactoring CSS. This is the reason we should focus so much on things like architectures, naming conventions, methodologies, etc.: because writing CSS is easy; looking after it is not.

It's particularly important when working in a team of independent designers that a naming methodology is adopted.  There are a number to choose from, and some may make more sense for email pieces versus print pieces.  The important thing when working with a naming convention is that we keep it super simple.   One of the methodologies that I like and have pursued is BEM.  BEM – meaning block, element, modifier – is a front-end naming methodology thought up by the guys at Yandex. It is a smart way of naming your CSS classes to give them more transparency and meaning to other designers. They are far more strict and informative, which makes the BEM naming convention ideal for teams of designers on larger projects that might last a while.   

Pure BEM naming convention follows this pattern:

    .block {}
    .block__element {}
    .block--modifier {}

 - `.block` represents the higher level of an abstraction or component.
 - `.block__element` represents a descendent of `.block` that helps form `.block` as a whole.
 - `.block--modifier` represents a different state or version of `.block.`

The reason for double rather than single hyphens and underscores is so that your block itself can be hyphen delimited, for example:

    .site-search {} /* Block */
    .site-search__field {} /* Element */
    .site-search--full {} /* Modifier */

The point of BEM is to tell other designers more about what a class doing from its name alone. By reading some HTML with some classes in, you can see how – if at all – the chunks are related; something might just be a component, something might be a child, or element, of that component, and something might be a variation or modifier of that component. To use an analogy/model, think how the following things and elements are related:

    .person {}
    .person__hand {}
    .person--female {}
    .person--female__hand {}
    .person__hand--left {}
These all make sense, but are somewhat disconnected. Take `.female` for example; female what? What about `.hand`; a hand of a clock? A hand in a game of cards? By using BEM we can be more descriptive but also a lot more explicit; we tie concrete links to other elements of our code through naming alone.

Velma's use of BEM should be adaptive, but also follow some basic principles.  If we construct our documents with the idea of using containers (rigid, absolutely positioned DIVs with hidden overflows) for block-level elements, a typical structure will look like this:

> **Block**  -  "#doc-container"  CSS ***id*** indicates a container block  
> **Element** -  ".doc-container_name"  CSS ***class*** of the same name of the container  
> **Modifier**  -  ".doc-container_nameName"  CSS used to modify the contents of an element  


A typical Velma BEM style would look something like this:

    #doc-descriptionContainer  (Block)
	    .doc-description_stats  (Element)
		    .doc-description_statsTable  (Modifier)
		    .doc-description_statsTable td:nth-child(odd)  (Modifier)
	    .doc-description_houseInfo  (Element)
		    .doc-description_houseInfoTable  (Modifier)
The use of the word *"Container"* is redundant considering that all containers have a CSS ID which immediately identifies it, but might be useful as an additional way of quickly recognizing the element you are working with.  Nesting the classes within the container is another very useful way of quickly identifying a blocks element or modifier that you wish to edit.

{% include links.html %}
