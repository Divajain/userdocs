---
id: schedules
title: Payment Schedules
sidebar_label: Payment Schedules
---

***In real-world scenarios, the payment schedule object is rarely used, as the payments are not tied to any other process or object. The more common case is for payment records to be automatically created and submitted by an existing back end process.***

## Creating recurring payments (against existing authorisation)
 
Navigate to the authorisation record you want to use for the payment schedule. Select the dropdown arrow by the payment schedules related list, then hit the New button.
 
![Related list](/userdocs/img/payment_schedule/related_list.png)
 
The correct authorisation will already be pre-populated.
 
Fill in the rest of the required fields (see below for an explanation) and then hit the Save button.
The payment schedule is now active, and will collect overnight each time the following conditions are met:

- The "Next Payment Date" is set to either today, or is in the past
- The status of the Payment schedule is set to "Active"
- The status of the authorisation attached to the payment schedule is "In force"

If you wish to temporarily stop the payment schedule from collecting, then just edit the record, and change its status from “In force” to “Inactive”.

One important thing to note with regard to Direct Debits; Direct Debits take time to process so to make sure the payment is taken from the customer's bank account on the correct date the whole cycle starts a number of days before the actual due date ("Next Payment Date").  The number of days is a configuration parameter that is set to 4 by default.  If you make a Payment Schedule "Inactive" during that window then there might already be a payment being processed that you will need to deal with separately.

## Setting parameters for payment schedules
 
Required fields
<table>
<tr>
<th>Authorisation</th>
<td>Set to the authorisation record that should be used to collect the schedule payment.</td>
</tr><tr>
<th>Frequency</th>
<td>The frequency at which the payment should be collected.</td>
</tr><tr>
<th>Regular amount</th>
<td>The amount that should be taken from each payment.</td>
</tr><tr>
<th>Next payment date</th>
<td>The date that you want the payment schedule to start collecting. This will be updated (according to the frequency) each time the schedule collects.</td>
</tr><tr>
<th>Status</th>
<td>Either “In force” or “Inactive”. This should be set to “In force”, otherwise the schedule will not collect. If a “Final payment date” is set, then status will be automatically set to “Inactive” after the final payment has been taken.</td>
</tr><tr>
</table>

## Frequency options

The following frequency options are available:
 - Daily
 - Weekly
 - Monthly
 - Quarterly
 - Biannual
 - Annual


