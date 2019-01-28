---
id: payments
title: Payments
sidebar_label: Payments
---

## Collecting one-off payments
For simple one-off payments without an authorisation (that require payment details to be entered), simply create a payment object with the required amount, and select the payment route options you wish to allow on the payment page.
 
You can then access the payment page via one of two ways:
 
 - If the customer is providing you with payment details as you are in the org (such as over the phone), then hit the “Process payment” button on the top-right of the screen, then enter the required details into the form.
 - If you wish to provide the customer with a link to the payment page that they can complete at their own convenience, copy the “Ecommerce URL” field and supply this to the customer (this might be via email, IM, or any other means.)
 
## Manually collecting ad-hoc payments against an existing authorisation
 
Ad hoc payments can easily be taken where a related authorisation record is already set up.

1. Navigate to the authorisation record for which you wish to set up a payment. Under the payment related list for the authorisation, select `New`:
 
![New payment from auth](/userdocs/img/payments/payment_related_auth.png)
 
Note that the authorisation field will be pre-populated with the required authorisation record.

2. Enter the required amount, and then hit Save. This will create the payment record with the authorisation attached.

3. Navigate to the payment record, then hit the Process payment button.
 
## Automatically collecting payments against an existing authorisation
 
Payments can be automatically collected against an existing authorisation by creating a payment object where the following conditions are true:
 - The payment record is set to “Awaiting submission”
 - The payment record is attached to an authorisation
 - The attached authorisation's status is “In force”
 
An overnight batch job will run and attempt to collect any payments that fulfil these above criteria.
 
This payment object can be created manually as above. However, more commonly in practice, it can also be created automatically as part of a Lightning flow, Process, Apex trigger or any other method Salesforce provides for automation.
 
## Required data
 
The required fields for a payment are: 

 - Available payment routes
 - Amount 
 - Currency (only if multi-currency payments are enabled for the Salesforce org.)
 
When creating a payment from an authorisation, the authorisation field will automatically be populated with the correct record ID.
 
## Statuses
Payment statuses are provided as follows:
 
<table>
<tr>
<th>Awaiting submission</th>
<td>The payment has not yet been processed or submitted to your payment service provider.</td>
</tr><tr>
<th>Submitted for collection</th>
<td>The payment has been submitted to your payment service provider, but the outcome of this transaction is not yet known. This is used for direct debit payments which will take a few days to clear.</td>
</tr><tr>
<th>Collected from Customer</th>
<td>The payment has been collected from the customer and has been confirmed.</td>
</tr><tr>
<th>Failed</th>
<td>The payment failed to collect. There are a variety of reasons why this could happen, in this case there should be a reason documented in the “Status description” field.</td>
</tr>
</table>
 
## Cancellations / Refunds in Salesforce
If you wish to refund a payment, navigate to the payment record and press the “Refund” button. This will show as a standard button in classic, and a quick action in lightning:
 
![Refund button](/userdocs/img/payments/refund_button.png)
 
You’ll then see the refund dialog, where you can either choose to refund a specified amount (up to the original amount of the payment).
 
![Refund dialog](/userdocs/img/payments/refund_dialog.png)
 
Note that some payment service providers place restrictions on refunds. If this is the case, you will need to contact your payment service provider and ask them to enable refunds on your account.
