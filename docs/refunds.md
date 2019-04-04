---
id: refunds
title: Refunds
sidebar_label: Refunds
---

## Collecting refunds
To collect a refund against a payment, simply hit the "Refund" button or quick action on the payment record. You'll then be presented with a dialog:

![Refund dialog](/userdocs/img/payments/refund_dialog.png)

You can choose to refund up to the original amount of the payment. The refund will then be processed immediately. (Some payment service providers place restrictions on refunds by default. If this is the case, you will need to contact your payment service provider and ask them to enable refunds on your account.)

Multiple refunds can be issued against the same payment, so long as your payment provider allows this and the total amount refunded does not exceed the original transaction value.

Note that your user must have the "Asperato refunds" permission set applied in order to be able to process refunds. This is supplied with the managed package. If your refunds are being declined, you may need to speak to your payment processor - some disable refunds by default, and require them to be manually activated before you can refund payments.

## Refund process (card)
When a refund is submitted from Salesforce, the following flow of events takes place:

1. Salesforce securely sends the refund request through to the Asperato servers.
2. Asperato identifies the refund requested, the amount requested, and then instructs the card gateway to process the refund against the original transaction. Depending on the amount, this can either be a full or a partial refund.
3. The card gateway will (usually) perform some checks their side - this ensures the refund amount doesn't exceed the value of the original transaction, and sometimes limits the number of individual partial refunds that can be made against the same transaction.
4. The card gateway then executes the refund request, and returns the response to Asperato.
5. Asperato will parse the response from the card gateway, and create the relevant refund object in Salesforce. This in turn will update the "amount refunded" field on the original payment request, if the refund was successful.
 
## Refunds with direct debit
Processing refunds from direct debit payments can be risky. A customer is protected under the Direct Debit Scheme Rules; if a Direct Debit is collected in error, they should request a refund from their bank. This means you could easily end up with a "double refund", and subsequently have to resort to legal means to claim back the funds.
