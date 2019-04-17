---
id: merchantgroups
title: Merchant Groups
sidebar_label: Merchant Groups
---

**Note: This feature will be available from version 2.12 of Asperato ONE.**

## Introduction
Before the introduction of merchant groups, Asperato ONE allowed you to connect any PSP for a given currency and payment route. For example, you may have had a Stripe account for GBP and EUR card payments, a GoCardless account for GBP and EUR direct debit payments, and a Cybersource account for USD card payments. However, if you needed to connect a second PSP to use for a subest of (for example) GBP card payments, then this wasn't possible without manual customisation.

Merchant groups enable you to set up different groups of PSP connections, and then assign those groups to different payments and authorisations.

Merchant groups can be created and used in both lightning and classic. The screenshots here show the process in lightning experience, however it is near identical in classic. If you're struggling, just drop us a line at support@asperato.com and we'll do our best to help out.

## In what situation would I want to use merchant groups?
You can use them however you wish. We find the most common use case is with different legal entities - a franchise for example may have a single Salesforce org managing a few hundred stores across a region, and each of those stores would have their own merchant accounts. The merchant group functionality facilitates this use case by allowing a new merchant group to be set up per store.

## Do I have to use merchant groups?
No. If, for any given currency and payment route, you only need a single PSP connected, then you can carry on using the package exactly as before, with no changes. The new merchant group functionality is backwards compatible. If you don't need to use it, your existing PSP connections, payments and authorisations will all be created and processed as before against a pre-defined "Default" merchant group.

## Creating a new merchant group
Head to the Asperato Setup page, and hit the "New Group..." button:

![New group button](/userdocs/img/merchant_group/newgroupbutton.png)

Then type in the new group name in the dialog that appears. Be careful here - the group name *cannot* be changed later, aside from deleting and re-adding the merchant group.

![New group dialog](/userdocs/img/merchant_group/newgroupdialog.png)

You'll then see the new group created and selected on the setup page. It will be empty - you'll need to populate it with at least one PSP connection before you can use it:

![New group created](/userdocs/img/merchant_group/newgroupcreated.png)

## Adding PSP connections to a merchant group
To add a PSP connection to a merchant group, first select the group on the Asperato Setup page, then hit the "Add new connection" button.

For a more in-depth description of this process, see <a href="https://asperato.github.io/userdocs/docs/connectingpsp">here</a>.

## Assigning a merchant group to a payment or authorisation
Assigning a merchant group to a payment or authorisation is just a case of populating the "Merchant group" field with the correct merchant group. For example, when creating a payment object:

![New payment](/userdocs/img/merchant_group/newpayment.png)

...just fill in the "Merchant group" field that appears to the right hand side of the "Amount" field. When populating the Merchant group field via an API call, or via Apex, the field name needed is "asp04_Merchant_group__c". When the payment or authoristaion is then processed, it will be processed using the PSP connections specified in that merchant group.

If the "merchant group" field is left blank then the "Default" merchant group will be assigned and used instead to ensure backwards compatibility.

## Assigning a merchant group to a repeat payment
For a merchant group to be assigned to a repeat payment (a payment attached to an authorisation), then the merchant group field on both the payment and authorisation objects *must* match exxactly. If they do not, then the payment will not be processed but instead return a failure status of "Merchant groups must match."

## Assigning a merchant group to a payment schedule
There is no need to assign a merchant group to a payment schedule directly - the merchant group used will be the one that is set on the authoristaion object attached to the payment schedule.

## Renaming merchant groups
Merchant groups deliberately *cannot* be renamed, as this would break any automation in place that relied on the merchant group's name. If the group has to be renamed, it should be first deleted, then a new one created with the correct name, then the PSP connections re-established against the new group.
