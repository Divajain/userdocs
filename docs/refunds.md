---
id: refunds
title: Refunds
sidebar_label: Refunds
---

## Collecting refunds
To collect a refund against a payment, simply hit the "Refund" button or quick action on the payment record. You'll then be presented with a dialog:

![Refund dialog](/userdocs/img/payments/refund_dialog.png)

You can choose to refund up to the original amount of the payment. The refund will then be processed immediately.

Multiple refunds can be issued against the same payment, so long as your payment provider allows this and the total amount refunded does not exceed the original transaction value.

Note that your user must have the "Asperato refunds" permission set applied in order to be able to process refunds. This is supplied with the managed package. If your refunds are being declined, you may need to speak to your payment processor - some disable refunds by default, and require them to be manually activated before you can refund payments.
 
## Refunds with direct debit
Processing refunds from direct debit payments can be risky, since a customer has the legal right to ask their bank to refund the payment at any time (even if you have previously refunded the original transaction.) This means you could easily end up with a "double refund", and subsequently have to resort to legal means to claim back the funds.
