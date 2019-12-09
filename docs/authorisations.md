---
id: authorisations
title: Authorisations
sidebar_label: Authorisations
---

## Overview of Authorisations in Salesforce
Authorisation records are used when you want to collect and save a payment method from one of your customers. The authorisation object in Salesforce is used to store a saved payment method that can authorise payments in the future. An authorisation can be created for any payment route aside from Paypal.
 
Saved payment method details, such as card or account number are always tokenised to protect you and your customer from fraud, don’t accept anything less.
 
Your customer can register multiple authorisations with you, so you could have both a card payment method on record as well as a Direct Debit mandate in place.
 
Asperato will always maintain these records, updating Salesforce with any state changes that you need to be aware of (such as if your customer cancels a direct debit.) Acting on these state changes is something you can do via Salesforce automation.
 
Key fields include:

<table>
<tr>
<th>Authorisation URL</th>
<td>This is the link you provide to your customer to enable them to provide authority to save a payment method.</td>
</tr><tr>
<th>Status</th>
<td>Tells you if the Authorisation is ready to use or not.</td>
</tr><tr> 
<th>Status description </th>
<td>A descriptive text showing the reason related to the current status. Might contain the reason for cancellation or failure for example.</td>
 </tr><tr>
<th>Payment Route Options</th>
<td>Allows you to choose which Authorisation routes are available to your customer to use. E.g. Card, Direct Debit or ACH</td>
</tr><tr>
<th>Payment Route Selected</th>
<td>Tells you which type of payment method has been granted by the customer.</td>
</tr></table>
 
Autorisations have to be ‘In Force’ before they can be used to collect payments.
 
 
## Required data 
“Available payment routes” is the only required field on the authorisation object. Optional address fields can be populated if necessary, which will pre-fill the payment page when the authorisation is processed.
 
## Statuses
The following statuses are available on the authorisation object:

<table>
<tr>
<th>Awaiting submission</th>
<td>The authorisation has not yet been processed through a payment service provider.</td>
</tr><tr>
<th>Pending</th>
<td>This status is used for direct debits, and indicates the authorisation has been processed but is not yet in force. Direct debit authorisations have a lead time of a few days before they become active - see <a href="https://support.gocardless.com/hc/en-gb/articles/360000593445-Timing-cycles" target="_blank">Timing cycles</a> for details. This status isn’t relevant for card authorisations, as they become active (or fail) instantly.</td>
</tr><tr>
<th>In force</th>
<td>The authorisation has been confirmed, is valid, and can be used to authorise a payment.</td>
</tr><tr>
<th>Cancelled</th>
<td>The authorisation has been cancelled at the request of the payor, or at your request.</td>
</tr><tr>
<th>Failed</th>
<td>The authorisation is not valid / no longer valid and cannot be used to take payments.</td>
</tr><tr>
<th>Expired</th>
<td>The authorisation has expired, and can no longer be used to take payments.</td>
<tr>
</table>
 
## Creating and Requesting Authorisations
 
Authorisations can either be processed internally to the org (for example, if an agent in a call centre was taking details over the phone to set up an authorisation) or externally (if a link to setup the authorisation is required outside of Salesforce.)
 
The Asperato package can cover both of these use cases.
 
To process an authorisation internally, hit the “Process authorisation” button. This will appear as a standard button in classic, and a quick action in lightning:
 
![Process authorisation button](/userdocs/img/auth/process_authorisation.png "Process authorisation button")
 
An overlay will appear showing the payment form. When this form is submitted, details of the authorisation will then show on the Salesforce object:
 
![Auth details](/userdocs/img/auth/auth_details.png "Auth details")
 
To supply a link for processing externally, look for the “Ecommerce URL” field on the authorisation object:
 
![ECOM URL](/userdocs/img/auth/auth_ecom_url.png "ECOM URL")
 
This will contain a URL pointing to a webpage for the user to enter their details to set up the authorisation, and can be distributed by any means necessary (email, IM, etc.) When the user has completed the form, the authorisation object will be populated in Salesforce the same way as before.

## Custom references (2.12+)

Some PSPs allow you to specify a custom reference attached to an authorisation. You can specify this by using the "Custom reference" field available on the authorisation object.

However, note that not all PSPs or PSP account types support custom references, and some often have restrictions on the maximum length of a reference. You should check your PSPs documentation for any rules around specifying custom references. Note that setting a custom reference where they are not supported, or setting an invalid custom reference may cause a transaction to fail.

## Importing Authorisations to Salesforce
 
If you require existing authorisations from your PSP to be populated in Salesforce, then please contact support@asperato.com with details of your requirements.
