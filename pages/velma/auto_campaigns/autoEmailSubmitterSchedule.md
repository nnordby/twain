---
title: Auto Email Submitter Schedule
keywords: Auto, Email, submitter, auto-campaign, Corp Marketing, email submitter, auto_campaign_email, trigger, schedule
last_updated: Mar 16, 2018
tags: [auto_campaigns, velma]
summary: "The Auto Email Submitter tool is responsible for sending out queued emails from the Auto-Campaign and Corp Marketing systems."
sidebar: mydoc_sidebar
permalink: autoEmailSubmitterSchedule.html
folder: auto_campaigns
---

The tool looks at the trigger date/time of records in the "auto_campaign_email" table. If the trigger time is "now" or has already passed, the tool will process the data list and submit emails to all recipients for the order.

{% include important.html content="Trigger dates marked for the **year 2100** indicate a need for manual handling." %}

{% include callout.html content="The tool runs daily at the following scheduled times:
	* Hourly from 2:00 AM to 8:00 AM
	* Every half hour from 8:00 AM to 6:30 PM" type="info" %}



### Full Schedule

* 2:00 AM
* 3:00 AM
* 4:00 AM
* 5:00 AM
* 6:00 AM
* 7:00 AM
* 8:00 AM
* 8:30 AM
* 9:00 AM
* 9:30 AM
* 10:00 AM
* 10:30 AM
* 11:00 AM
* 12:30 AM
* 12:00 PM
* 12:30 PM
* 1:00 PM
* 1:30 PM
* 2:00 PM
* 2:30 PM
* 3:00 PM
* 3:30 PM
* 4:00 PM
* 4:30 PM
* 5:00 PM
* 5:30 PM
* 6:00 PM
* 6:30 PM




{% include links.html %}
