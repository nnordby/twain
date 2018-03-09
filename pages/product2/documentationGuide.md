---
title: Name of Document
keywords: key1, key2, key 3
last_updated: May 01, 2020
tags: [docs]  
summary: "Summarize the document and the information that it should cover."
sidebar: product2_sidebar
permalink: documentationGuide.html
folder: product2
---

### Title 1

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

<!-- You can include tips in your documents to help information stand out beyond just simple   -->
{% include tip.html content="You can include highlighted information by using the 'include' syntax.  See the documentation for more information and styles" %}

### Title 2

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

#### Sub item 1

```js
'.source.gfm':
  'Front Matter':
    'prefix': 'fm'
    'body': """
    ---
    title: Name of Document
    keywords: rpc, Product Service, product, vfs, service
    last_updated: April 27, 2017
    tags: [vfs, service, rpc]
    summary: "Manages products within the VFS Product Library."
    sidebar: product1_sidebar --Options: mydoc_sidebar, product2_sidebar
    permalink: vfs_productService.html
    folder: product1 --Options: mydoc, product1, product2
    ---
    """
  'Alert Note':
    'prefix': 'alert note'
    'body': '{% include note.html content="This is my note. All the content I type here is treated as a single paragraph." %}'
  'Alert Tip':
    'prefix': 'alert tip'
    'body': '{% include tip.html content="This is my tip. All the content I type here is treated as a single paragraph." %}'
  'Alert Warning':
    'prefix': 'alert warning'
    'body': '{% include warning.html content="This is my warning. All the content I type here is treated as a single paragraph." %}'
  'Alert Important':
    'prefix': 'alert important'
    'body': '{% include important.html content="This is my important info. All the content I type here is treated as a single paragraph." %}'
  'Callout Default':
    'prefix': 'callout default'
    'body': '{% include callout.html content="This is my primary callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="default" %}'
  'Callout Primary':
    'prefix': 'callout primary'
    'body': '{% include callout.html content="This is my primary callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="primary" %}'
  'Callout Danger':
    'prefix': 'callout danger'
    'body': '{% include callout.html content="This is my danger callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="danger" %}'
  'Callout Success':
    'prefix': 'callout success'
    'body': '{% include callout.html content="This is my success callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="success" %}'
  'Callout Info':
    'prefix': 'callout info'
    'body': '{% include callout.html content="This is my info callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="info" %}'
  'Callout Warning':
    'prefix': 'callout warning'
    'body': '{% include callout.html content="This is my warning callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="warning" %}'


  'Documentation Template':
    'prefix': 'doc template'
    'body': """
    ---
    title: Name of Document  <!--The name of the document  -->
    keywords: key1, key2, key 3  <!-- Enter the keywords that will assist in searches  -->
    last_updated: May 01, 2020  <!-- Change the date the document was updated -->
    tags: [docs]
    summary: "Summarize the document and the information that it should cover."
    sidebar: product2_sidebar   <!-- Identify the navigation menu that this article will appear in  -->
    permalink: documentationGuide.html  <!-- permalink will be the markdown name of the document represented as an html Document -->
    folder: product2 <!-- Name of the document folder this article appears in  -->
    ---

    ### Title 1

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

    <!-- You can include tips in your documents to help information stand out beyond just simple   -->
    {% include tip.html content="You can include highlighted information by using the 'include' syntax.  See the documentation for more information and styles" %}

    ### Title 2

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

    #### Sub item 1




    {% include links.html %}
    """
  'Image Include':
    'prefix': 'img include'
    'body': '{% include image.html file="company_logo.png" url="http://nsn.solutions" alt="NSN Solutions" caption="This is a sample caption" %}'
```

{% include image.html file="company_logo.png" url="http://nsn.solutions" alt="NSN Solutions" caption="This is a sample caption" %}

{% include links.html %}
