---
title: Print Dispatching
keywords: rpc, Print Dispatching, dispatch, vendor dispatch, vendor, engine, Amazing Mail, VFS_Job_VendorDispatch_AM, throttling, vfs, service
last_updated: April 27, 2017
tags: [vfs, service, rpc]
summary: "Every evening, the VFS Print Dispatching System executes.  It is looking for any job in a 'Rendered' status and gathers them up and submits them to the Vendor Engine for processing. After dispatching, the job gets set to 'Dispatched' status.  When the job is on its way to Amazing Mail, the status is set to 'Sending'. This is how it works."
sidebar: product1_sidebar
permalink: vfs_printDispatching.html
folder: product1
---

### Admin Web
**To query jobs to be dispatched:**
- Select **'Velma'** from the Sponsor filter drop down (if not already selected)
- Select **'Rendered'** from the Status filter drop down
- Date Filter - select **Custom Range** and look back a few days

**To query jobs that are currently being re-queued or in a dispatched state.**
- Select **'Velma'** from the Sponsor filter drop down (if not already selected)
- Select **'Dispatched'** from the Status filter drop down
- Date Filter - select **Custom Range** and look back a few days
- Anything in a dispatched state is currently going through processing to print Vendor.

**To query jobs that are currently being sent to Amazing Mail:**
- Select **'Velma'** from the Sponsor filter drop down (if not already selected)
- * Select **'Sending'** from the Status filter drop down
- Date Filter - select **Custom Range** and look back a few days

#### Detailed Workflow

### Technologies
##### Figure 1
##### Figure 2
##### Figure 3

### AWS Lambda

### VFS Amazing Mail Vendor Engine

### Throttling Explained








{% include links.html %}
