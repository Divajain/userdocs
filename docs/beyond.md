---
id: beyond
title: Beyond the core package
sidebar_label: Beyond the core package
---

## Enabling multiple currencies
Multiple currencies can be used, but must first be enabled in the Salesforce org. Some payment service providers may also require you to contact them to enable multiple currencies.

When multiple currencies have been enabled in your org, you will see another `currency` field available on each Salesforce object (Authorisation, Payment, etc.) Set this currency field on your payment and authorisation objects according to the currency you wish to collect in.
 
## Linking Payments and Authorisations to other Salesforce Objects
Custom fields can be created on any of the objects included with the package, including Payment and Authorisation. This functionality can be used to link payments and authorisations to other core or custom objects you may have in your org.

Salesforce provide details of this process <a href="https://help.salesforce.com/articleView?id=adding_fields.htm&amp;type=5" target="_blank">here</a>. If you are unsure of this process you may wish to obtain assistance from a certified Salesforce consultant.
 
## Automation in Salesforce
Automation is a big topic, and not one that can be covered in any great level of detail within this documentation. If you are not comfortable with the automation features Salesforce provides (such as Visual Workflows and Process builder) then we recommend you obtain assistance from a certified Salesforce consultant.