---
title: VFS Tokens and sample Data
keywords: tokens, token, VFS, vf-var, vf-show, vf token
last_updated: January 31, 2017
tags: [docs]
summary: "Quick guides and sample data for using different types of tokens within a document."
sidebar: mydoc_sidebar
permalink: mydoc_docs_VFSTokens.html
folder: mydoc
---

Tokens are used within HTML to create merged output from data derived from a user's accounts, a partner selected for a particular piece, or from the library's document properties.  They are constructed in a variety of ways but always contain the parent node first (the underlined un-indented items below) followed by a period and then the child property (indented items); e.g. ```user.cellPhone```
Most common will be the use of the standard replace token ```vf-var="user.cellPhone"``` but it is also acceptable to use the legacy {% raw %} ```{{user.cellPhone}}``` {% endraw %} (formerly: ```$$user.cellPhone$$```)  when the circumstance requires it, such as constructing a URL.  You can also use another special token to hide an entire element if variable data is missing:  ```vf-show="user.cellPhone"```.  In other words, "Show the element if the selected data is present. If it's not, don't."
Another important token is ```vf-insert```.  This token will insert another file into the area defined and would be applied as Example 4 demonstrates below.

##### Example 1
```html
<span vf-var="user.cellPhone" vf-show="user.cellPhone">Cell: 208-854-7900</span>
```
##### Example 2
```html
<div vf-show="user.cellPhone">
<span>Cell: </span><span vf-var="user.cellPhone">208-854-7900</span>
 </div>
```
##### Example 3
```html
<span vf-var="user.address1>5465 E. Terra Linda Way</span> <span vf-show="user.address2"> ,</span> <span vf-var="user.address2" vf-show="user.address2">Suite 293</span>
```
##### Example 4
```html
<div id="contactAreaContainer" vf-insert="template.contactArea">Contact Information</div>
```
In the Example 1 above, the entire span will be removed if the cell phone is missing.  If it is present, the contents of the span (Cell: 208-854-7900) will be replaced with just the cell phone.  To pre-pend variable data with a label, follow Example 2.
In the Example 2 above, we can pre-pend variable data with a label, but remove the entire container if the cell phone value is missing, thereby avoiding a hanging label with nothing attached to it.
In the Example 3 above, we can bring Address 1 and Address 2 together with a comma separating the two fields, but remove both the comma and the Address 2 line if there is no Address 2 present.

---
### User Token list with sample data

```yaml
user:
  address1: "5465 E. Terra Linda Way"
  address1and2: "5465 E. Terra Linda Way, Suite 253"
  address2: "Suite 253"
  addressSingleLine:"5465 E. Terra Linda Way, Suite 253, Nampa, ID, 83687"
  cellPhone: "208-854-7911"
  city: "Nampa"
  cityStateZip: "Nampa, ID 83687"
  companyName: "1st Demo Mortgage Company"
  disclaimer: "1st Demo Mortgage Co. 5950 Symphony Woods Rd, STE 312, Columbia, MD 21044. NMLS #1324XXX. 1st Demo Mortgage Co. is the true legal name for 1st Demo Mortgage and may be abbreviated as 1st Demo Mortgage.  Not an offer of credit or commitment to make a loan; all approvals are subject to underwriting guidelines including but not limited to: acceptable current credit worthiness, income history, etc. Loan programs & options are subject to change at any time. 1st Demo Mortgage is not affiliated with, or an agent or division of a governmental agency or depository institution. 1st Demo Mortgage Co. is licensed as:  Florida Mortgage Lender License #MLD1XXX, Georgia Mortgage Lender License #40XXX, Illinois Residential Mortgage License #MB.676XXXX, Indiana-DFI First Lien Mortgage Lending License #23XXX, Indiana-DFI Subordinate Lien Mortgage Lending License #23XXX, Kentucky Mortgage Company License #MC327XXX, Louisiana Residential Mortgage Lending License #MC327XXX, Maryland Mortgage Lender License #21XXX, Mississippi Mortgage Lender License #1124XXX, New Jersey Residential Mortgage Lender License #1124XXX, North Carolina Mortgage Lender License #L-159XXX,Ohio Mortgage Broker Act Certificate of Registration #MB.804XXX.000, Ohio Mortgage Loan Act Certificate of Registration #SM.501XXX.000, Pennsylvania Mortgage Lender License #44XXX, South Carolina-BFI Mortgage Lender/Servicer License #MLS ñ 1124XXX, Tennessee Mortgage License #123XXX, Texas - SML Mortgage Banker Registration #123XXX, Virginia Broker License & Virginia Lender License #MC-5XXX, West Virginia Mortgage Lender License #ML-33XXX. (www.nmlsconsumeraccess.org)"
  email: "john.public@1stDemoMortgage.com"
  fax: "208-854-7901"
  firstName: "John"
  fullName: "John Public"
  iconsUrl: "https://as.velma.com/user/6560/settings/IndustryIcons-Email.jpg?versionId=b1igzL5Z8PKxAPtCKAWXjDND5_zyKfAD"
  id: "6560"
  lastName: "Public"
  logoUrlEmail: "https://as.velma.com/user/6560/settings/BusinessLogo-Email.jpg?versionId=5Lpg1zem3w9NWlHUEXdzSt0UX.TP8ESl"
  logoUrlPrint: "https://as.velma.com/user/6560/settings/BusinessLogo.jpg?versionId=CB3Z3evdAPYuX2Lm9VN0lmIchz1mdvt0"
  nmls: "4832167"
  officePhone: "208-854-7900"
  photoUrlEmail: "https://as.velma.com/user/6560/settings/PersonalPhoto-Email.jpg?versionId=1j4mqrg1GJUmL6R0.NGj2D7WyhVadcMw"
  photoUrlPrint: "https://as.velma.com/user/6560/settings/PersonalPhoto.jpg?versionId=rYNI5cavuwaSpf3x3CTMG04BqztR8lhs"
  signatureUrl: "https://www.velma.com/Images/EmptyDot.gif"
  state: "ID"
  title: "Senior Loan Officer"
  userName: "demo10@velmatools.com"
  website: "www.1stDemoMortgage.com"
  zip: "83687"
```
---
### Partner Token list with sample data
```yaml
partner:
  address1: "683 Stony Radial"
  address1and2: "683 Stony Radial"
  addressSingleLine: "683 Stony Radial, Blairsburg, MA, 09464"
  cellPhone: "701-545-5779"
  city: "Blairsburg"
  cityStateZip: "Blairsburg, MA 09464"
  companyName: "Tangdou Real Estate Advisors"
  email: "josiah_nieves6872@proinbox.com"
  fax: "701-845-8778"
  firstName: "Josiah"
  fullName: "Josiah Nieves"
  iconsUrl: "https://www.velma.com/Images/EmptyDot.gif"
  id: 22849
  lastName: "Nieves"
  logoUrlEmail: "https://as.velma.com/user/6560/partner/22849/BusinessLogo-Email.jpg?versionId=OULMRxEmZQtRm3xspeB1xVzqj_W12g3j"
  logoUrlPrint: "https://as.velma.com/user/6560/partner/22849/BusinessLogo.jpg?versionId=vpzHVtgpdODCyIxuXenZmh1R7VXoY1xJ"
  officePhone: "701-745-7779"
  photoUrlEmail: "https://as.velma.com/user/6560/partner/22849/PersonalPhoto-Email.jpg?versionId=mUHUTQbt9_mDfP6L07BCnW_HZMGIiFdn"
  photoUrlPrint: "https://as.velma.com/user/6560/partner/22849/PersonalPhoto.jpg?versionId=EA.tvk6TIKpB5C5QXBFY0ORY.ks1aW4B"
  signatureUrl: "https://www.velma.com/Images/EmptyDot.gif"
  state: "MA"
  title: "Real Estate Advisor"
  website: "http://www.tangdou.com"
  zip: "09464"
```
---
### Template Token list with sample data
```yaml
template:
  contactArea: "https://s3.amazonaws.com/velma-assets/library/27516/contactArea.html"
  description: "VFS Open House Flyer 1"
  disclaimerArea: "https://s3.amazonaws.com/velma-assets/library/27516/disclaimerArea.html"
  name: "PHE Open House Flyer"
  previewUrl: "https://as.velma.com/library/29213/Preview.jpg?versionId=llwNzNBmseS_8MzuZCU1J0X7EnT4wZ1x"
  shareWithPartner: "true"
  sku: "29213"
  thumb: "https://s3.amazonaws.com/velma-assets/library/29213/Thumb.JPG"
  url: "https://as.velma.com/library/29213/OHF_1.html?versionId=EBwq8W2wNw72mdSFAJxmluoEgMu2ezoS"
```
{% include tip.html content="For more technical information and additional Smart Tokens, refer to the [Token Service Documentation:](product1/mydoc_vfs_tokenservice_supportedTags.html)" %}



{% include links.html %}
