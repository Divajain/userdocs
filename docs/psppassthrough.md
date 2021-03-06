---
id: psppassthrough
title: PSP Passthrough Parameters
sidebar_label: PSP Passthrough Parameters
---

**This feature requires version 2.13 or above of Asperato ONE.**

Some PSPs allow us to pass specific data on a per-transaction basis. This data could be references for accounting or auditing purposes, additional fields required by some classes of organisations (such as financial institution data), internal payment descriptions, additional customer data, or anything else you require to be sent to your PSP for each transaction. Asperato allows this data to be sent by way of the `PSP passthrough parameters` field.

Before you choose to use this field, you should be aware of the following points:

 - The data set on the field is PSP specific. This means if you switch to another PSP, and populate the same data on the field, it may not be passed to the new PSP in the same way.
 - The field isn't visible on the default layout for either payments or authorisations, so must be added manually if you wish to view it.
 - The data must be entered as a syntactically valid JSON object containing key-value pairs. This makes it unsuitable for manual use. Instead, a process should be used that collects the required data on a separate screen, formats the data appropriately, then inserts it into the field. Some development work is likely to be involved here, so we would strongly suggest appointing a qualified Salesforce consultant to help you manage this process.
 - The data will be sent both for repeat and web based transactions.
 - Invalid data specified in this field may cause transactions to fail.

# Current PSP support

Current support is limited to GoCardless and Sagepay. If you require support for an additional field, or an additional gateway, then let us know at support@asperato.com.

## GoCardless

### Description

GoCardless supports sending a description for payment records using a single "description" key. Note that this isn't supported for mandates.

The 'description' can be can be set by populating the PSP Passthrough Parameters field as follows:

```
{"description": "test description"}
```

If GoCardless sends notification emails to your customers, this description will be included. It is also visible for the payment record on the GoCardless dashboard. (Note that descriptions are not supported for mandates.)

By default, Asperato includes the Asperato transaction reference in the description field in GoCardless. Setting a custom description as above will remove the transaction reference from this field.

### Reference

GoCardless supports sending a reference for payment records using a single "reference" key. Note that this isn't supported for mandates.

The 'reference' can be can be set by populating the PSP Passthrough Parameters field as follows:

```
{"reference": "testref"}
```

This reference will appear on your customer’s bank statement.

**You must make sure any use of custom references is tested thoroughly in a sandbox prior to live deployment.** Support for custom references must be explicitly enabled by GoCardless, and there are strict restrictions in place around the reference format - different schemes have different maximum lengths, and some schemes require that the reference is unique. If you do not adhere to the correct format, or the custom reference functionality isn't enabled, your transactions will likely fail.

### Custom metadata

GoCardless supports sending custom pairs of key-value metadata for customer, payment and mandate records. At present up to three key-value pairs are supported for each record type (this limitation is on the GoCardless side, not the Asperato side.)

After processing, the metadata should be visible the relevant payment, customer or mandate object in the GoCardless dashboard.

#### Payment

The custom payment metadata can be set on the payment record in Salesforce, by populating the `PSP Passthrough Parameters` field as follows:

    {"payment_metadata":{"Key1":"Value1","Key2":"Value2","Key3":"Value3"}}
    
For example, the following would be valid:

    {"payment_metadata":{"InternalRef":"19583716","BedSize":"XL"}}

#### Authorisation

Custom metadata can be set for mandate and customer objects on the authorisation record in Salesforce, by populating the `PSP Passthrough Parameters` field as follows:

    {"customer_metadata":{"CustomerKey1":"CustomerValue1","CustomerKey2":"CustomerValue2"},"mandate_metadata":{"MandateKey1":"MandateValue1","MandateKey2":"MandateValue2"}}

Note that:

 - Up to three key-value pairs can be provided for `customer_metadata` and another three for `mandate_metadata` (six in total.)
 - Specifying both `customer_metadata` and `mandate_metadata` fields is not required.

## Sagepay

Sagepay supports sending a reference for payment records using a single "reference" key.  This reference is called "VendorData" in Sagepay's documentation.

The 'reference' can be set by populating the "PSP Passthrough Parameters" field as follows:

```
{"reference": "testref"}
```

From Sagepay's documentation: "The field accepts 200 standard alpha-numeric characters (Aa-Zz, 0-9) and is included in the transaction registration post."  
The value is shown in a column at the right of the transaction search table on the Sagepay dashboard as “Reference”.  Note that reference cannot contain characters such as underscores, if you include such characters the payment will fail.

Sagepay also supports the use of the PSP Passthrough Parameters field for specifying per-transaction financial institution (6012) data. More information is available [here](https://asperato.github.io/userdocs/docs/fiparams).
