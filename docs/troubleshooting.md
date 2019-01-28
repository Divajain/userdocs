---
id: troubleshooting
title: Troubleshooting
sidebar_label: Troubleshooting
---

We only support the latest version of Asperato ONE. New packages, containing new bugfixes, are constantly being released. If you are having issues, as the first port of call please check if you are using the latest package version and upgrade if necessary:

https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3A00000EcrOnUAJ

If you are having issues that this page doesn't help you resolve, please email support@asperato.com with details of your issue.

## Can't collect refunds
This is likely to be one of a few scenarios:
 - Refunds are not enabled by your payment processor. If this is the case, you'll need to contact them to get this enabled.
 - A refund is not possible on this payment because of a restriction by your payment processor. Again, you'll need to contact them to find what this is - some processors only allow a certain number of refunds on a single payment, some only allow refunds after a certain length of time has passed, etc.
 - Your user does not have the required permissions to issue refunds. Asperato ships with an "Asperato refund user" permission set which you'll need to apply to the Salesforce user in question to allow them to issue refunds.
 
## The "Getting started page" is blank
You'll need to enable, and deploy "My Domain" to you users before you can view the "Getting started" page. [Please see instructions from Salesforce on how to do this](https://help.salesforce.com/articleView?id=domain_name_overview.htm&type=5).