---
id: fiparams
title: Financial institution parameters
sidebar_label: FI (6012) parameters
---

## Introduction
Some merchants, known as "6012 merchants", will have the requirement of supplying financial institution information to the PSP with each payment. The vast majority of customers will not have this requirement. If you're not sure, you can check with your payment service provider.

## PSP support
Not all PSPs support passing FI data. If you need a list of PSPs we currently interface with that support passing FI data, send a message to support@asperato.com and we'll let you know.

## Specifying FI data
You must collect the FI data that you need from your customer, and use that to populate the payment record before displaying the payment page. This data should be populated in the `PSP Passthrough Parameters` field in a JSON key / value format. The resulting field must contain valid JSON.

The keys that can be used for FI data in this field are as follows:

 - **`fiSurname`**  The surname of the recipient.
 - **`fiPostcode`** The postcode of the recipient. 
 - **`fiDoB`** The date of birth of the primary recipient in the format `YYYYMMDD`.
 
 Note that the keys are case sensitive.
 
 For example, a surname of "Windsor", postcode of "SW1A 1AA" and date of birth of "21st April 1926" would translate to the following JSON inserted into the `PSP Passthrough Parameters` field:
 
 ```
 {
     "fiSurname": "Windsor",
	 "fiPostcode": "SW1A 1AA",
	 "fiDoB": "19260421"
 }
 ```
 
 PSPs require a further FI field, `fiAccountNumber`, which is comprised of the first 6 and last 4 digits of the pan. However, you do not need to supply this field. Asperato will generate and send it automatically if other FI data is provided.