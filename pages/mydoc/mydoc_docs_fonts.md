---
title: Creating Web Fonts
keywords: font, fonts, TTF, WOFF2, WOFF, OTF, Prince
last_updated: March 6, 2018
tags: [docs]
summary: "To create a web font from an existing desktop font, follow these simple steps"
sidebar: mydoc_sidebar
permalink: mydoc_docs_fonts.html
folder: mydoc
---

### Identify Local Font
- Grab font from Pageflex, local computer, etc.
- Go to [Font-Converter](https://font-converter.net/en) and upload the local font
- Select only the WOFF2 conversion format and check the "Include HTML/CSS template" option

{% include warning.html content="Need to confirm that WOFF2 is a font that Prince will work with." %}

### Upload Converted Font
- Unzip the downloaded font and go to the "fonts" folder and grab the converted WOFF2 file
- Upload it to S3 in the **_velma-assets > library > _shared > fonts > type_** folder making sure you make sure the visibility is set to "Everyone" during the upload wizard

{% include links.html %}
