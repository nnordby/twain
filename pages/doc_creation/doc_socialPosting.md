---
title: Social Posting
keywords: posting, social, document, creation, doc creation, social posting
last_updated: March 8, 2018
tags: [docs]
summary: "For documents posted to social sites like Facebook & Twitter, specific meta data needs to be included"
sidebar: mydoc_sidebar
permalink: doc_socialPosting.html
folder: doc_creation
---

#### Setting up the document
Make sure the ```head``` section of your document looks like this:
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <!-- Open Graph Data -->
  <meta property="og:url" content="https://s3.amazonaws.com/vfs-job/beta/{{jobId}}/document" />
  <meta property="og:type" content="article" />
  <meta property="og:title" content="{{template.socialTitle}}" />
  <meta property="og:description" content="{{template.socialDescription}}" />
  <meta property="og:image" content="{{template.socialImage}}" />
  <!-- Twitter Card  -->
  <meta name="twitter:card" content="summary">
  <meta name="twitter:title" content="{{template.socialTitle}}">
  <meta name="twitter:description" content="{{template.socialDescription}}">
  <meta name="twitter:url" content="https://shared.velma.com/{{jobId}}/document">
  <meta name="twitter:image" content="{{template.socialImage}}">
  <link rel="stylesheet" href="https://s3.amazonaws.com/velma-assets/library/_templates/print/_common/unstyle.css">
  <title vfvar="title">Flyer</title>
  <style>
    #vfsFlyer {
      all: unset;
    }
  </style>
</head>
```
Your document properties will need to be setup to accommodate the template properties identified in the tokens in the meta data.  

{% include tip.html content="You **_don't_** need separate properties or tokens for the Open Graph Data and the Twitter data.  One set of properties will work for both of them." %}


A properly formatted post will appear like this when the Facebook share is invoked:
![](https://screencast-o-matic.com/screenshots/u/fUaP/1501715171795-69114.png)

The resulting post on Facebook will appear in the user's wall:
![](https://screencast-o-matic.com/screenshots/u/fUaP/1501716666015-2906.png)
---
#### The Meta data
```html
<!-- Open Graph Data -->
 <meta property="og:url" content="https://shared.velma.com/{{jobId}}/document" />
 <meta property="og:type" content="article" />
 <meta property="og:title" content="{{template.socialTitle}}" />
 <meta property="og:description" content="{{template.socialDescription}}" />
 <meta property="og:image" content="{{template.socialImage}}" />
 <!-- Twitter Card  -->
 <meta name="twitter:card" content="summary">
 <meta name="twitter:title" content="{{template.socialTitle}}">
 <meta name="twitter:description" content="{{template.socialDescription}}">
 <meta name="twitter:url" content="https://shared.velma.com/{{jobId}}/document">
 <meta name="twitter:image" content="{{template.socialImage}}">
```

##### Fulfillment Properties
  socialDescription  
  socialImage (include the full url path to the image)  
  socialTitle  
  socialSharing (set to true to turn sharing on)

##### Social Image Size
Facebook's 1200px x 630px seems to be a good size that covers the other two (Linkedin 646 x 220, Twitter 440 x 220)

[https://makeawebsitehub.com/social-media-image-sizes-cheat-sheet/](https://makeawebsitehub.com/social-media-image-sizes-cheat-sheet/)


{% include links.html %}
