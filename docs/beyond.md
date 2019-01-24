---
id: beyond
title: Beyond the core package
sidebar_label: Beyond the core package
---

## Enabling multiple currencies
Multiple currencies can be used, but must first be enabled in the Salesforce org. Some payment service providers may also require you to contact them to enable multiple currencies.
When multiple currencies have been enabled in your org, you will see another `currency` field available on each Salesforce object (Authorisation, Payment, etc.) This currency should usually be set to match the local currency of the billing address specified.
 
## Linking Payments and Authorisations to other Salesforce Objects
Custom fields can be created on any of the objects included with the package, including Payment and Authorisation. This functionality can be used to link payments and authorisations to other core or custom objects you may have in your org.
Salesforce provide details of this process here.
 
## Automation in Salesforce
Automation is a big topic, and not one that can be covered in any great level of detail within this documentation. If you are not comfortable with the automation features Salesforce provides (such as Visual Workflows and Process builder) then we recommend you obtain assistance from a certified Salesforce consultant.