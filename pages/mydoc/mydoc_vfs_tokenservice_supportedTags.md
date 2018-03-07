---
title: Token Service Supported Tags
keywords: tokens, token, VFS, tags, insert, replace, special
last_updated: February 22, 2017
tags: [docs]
summary: "This document describes the new vf-vars and token operations now supported by the token service. Note the vfvar (no hyphen) tokens are separate and not impacted by the vf-vars."
sidebar: mydoc_sidebar
permalink: mydoc_vfs_tokenservice_supportedTags.html
folder: mydoc
---

## Legacy Tokens
There are 2 legacy tokens supported by the tokenService:
- __Insert Token__: ```@@TOKEN@@```
- __Replace Token__: {% raw %} ``` {{TOKEN}} ```
{% endraw %}
### Insert Token
The insert token is used to pull data from a URL and place it into the active document.  The operations starts by finding the token. The search pattern is {% raw %} ```@@[a-zA-Z0-9._-]+@@} ``` {% endraw %}.  The value between the ```@@``` symbols are used to lookup a value in the _command packet_ sent with the request.  

It is expected that the value in the _command packet_ will be a URL. The system will fetch the content of that url and then replace the token, including the ```@@``` symbols.

__Example:__

```
<div>@@document.contactArea@@</div>
```

### Replace Token
The replace token is used to put data from a command packet into the active document. The operation starts by finding the token. The search pattern is {% raw %} ```{{[a-zA-Z0-9._-]+}}``` {% endraw %}. The value between the {% raw %} ```{{``` {% endraw %}symbols are used to lookup a value in the _command packet_ sent with the request.

It is expected that the value is string content: text or html. The system will take that data and replace the token, including the ```}}``` symbols.

__Example:__

```
<div>Hello, {{user.firstName}}</div>
```

## VFS Variables (vf-var)

VFS Variables are smarter tokens. All VFS Variables are implemented as html attributes and function in different ways depending on the target node and the specific VFS Variable used.

Each of these tokens will hold a value that references a path in the _command packet_. The _command packet_ value will be used in a specific operation depending on the vfs variable but effect the html node to which the vfs variable is applied.

- ```*[vf-insert]``` - Replaces the innerHtml of the node with data retrieved from a URL.
- ```*[vf-show]``` - Hides hides the html node if the value in cp is empty or missing.
- ```*[vf-html]``` - Sets the innerHtml.
- ```*[vf-text]``` - Sets the innerText.
- ```*[vf-title]``` - Sets title attribute
- ```*[vf-class]``` - Append to the class attribute
- ```*[vf-style]``` - Append to the style attribute
- ```img[vf-src]``` - Sets an image tag's src attribute
- ```img[vf-alt]``` - Sets an image tag's alt text attribute
- ```progress[vf-value]``` - Sets a progress's bar value attribute
- ```a[vf-href]``` - Sets an anchor tag's href attribute
- ```a[vf-tel]``` - Sets an anchor tag's href attribute using pattern _"tel:%s"_
- ```a[vf-mailto]``` - Sets an anchor tag's href attribute using pattern _"mailto:%s"_
- ```a[vf-thumb]``` - Sets an anchor tag's href attribute using pattern _"https://.../%s/document.thumb"_
- ```a[vf-preview]``` - Sets an anchor tag's href attribute using pattern _"https://.../%s/document.preview.1"_
- ```a[vf-output]``` - Sets an anchor tag's href attribute using pattern _"https://.../%s/finalOutput"_
- ```img[vf-thumb]``` - Sets an image tag's src attribute using pattern _"https://.../%s/document.thumb"_
- ```img[vf-preview]``` - Sets an image tag's src attribute using pattern _"https://.../${stage}/%s/document.preview.1"_

Several aliases exist to simplify document creation:

- ```*[vf-var]``` points to ```*[vf-html]```
- ```img[vf-ref]``` points to ```img[vf-src]```
- ```a[vf-ref]``` points to ```a[vf-href]```
- ```a[vf-mail]``` points to ```a[vf-mailto]```
- ```*[vfVar]``` points to ```*[vf-text]```
- ```img[vfVar]``` points to ```img[vf-src]```
- ```a[vfVar]``` points to ```a[vf-href]```

<sup>_Note: ```a[vfVar]``` has special handing for tel and mailto values.  See special
cases below for more information._</sup>

<sup>_Note: The ```*``` symbol above indicates that this vfs variable is valid on any tag. although it might not make sense on certain tags._</sup>

## Special Handling

Most tags function the same. They extract data from the _command packet_, manipulate it, then set the resulting value into a attribute, text, or html on the current node. ```vfVar```'s are different.  This is ```vfVar```, NOT ```vf-var```.

 ```*[vfVar]``` simply places the value found in the _command packet_ at the referenced path into the innerText of the node to which the attribute was applied. This is identical behavor to ```*[vf-text]```. The exception to this rule is if the tag is a ```<img />``` or ```<a />```.

 ```img[vfVar]``` will still pull the value from the _command packet_ but, rather then setting the innerText, it will set the ```src``` attribute of the image tag. This is identical behavior to ```img[vf-src]```.

 ```a[vfVar]``` will still pull the value from the _command packet_ but, rather then setting the innerText, it will set the ```href``` attribute of the anchor tag.  Additionally, the value set on the href attribute might be altered if the value currently in the href attribute (that is the value that exists before tokenization) starts with _tel:_ or _mailto:_.   If either of these strings are set, the system will maintain the prefix.

__Example:__

```
<a vfVar='user.phone' href='tel:5555555555'>Call me</a>
```

Assuming the _command packet_ has a value user.phone="1234567890", the resulting string from the above example will read as follows.

```
<a vfVar='user.phone' href='tel:1234567890'>Call me</a>
```
{% include links.html %}
