---
id: psppassthrough
title: PSP Passthrough Parameters
sidebar_label: PSP Passthrough Parameters
---

# Introduction

Some PSPs allow us to pass specific data on a per-transaction basis. This data could be references for accounting or auditing purposes, additional fields required by some classes of organisations (such as financial institution data), internal payment descriptions, additional customer data, or anything else you require to be sent to your PSP for each transaction. Asperato allows this data to be sent by way of the "PSP passthrough parameters" field.

Before you choose to use this field, you should be aware of the following points:

 - The data set on the field is PSP specific. This means if you switch to another PSP, and populate the same data on the field, it may not be passed to the new PSP in the same way.
 - The field isn't visible on the default layout for either payments or authorisations, so must be added manually if you wish to view it.
 - The data must be entered as a syntactically valid JSON object containing key-value pairs. This makes it unsuitable for manual use. Instead, a process should be used that collects the required data on a separate screen, formats the data appropriately, then inserts it into the field. Some development work is likely to be involved here, so we would strongly suggest appointing a qualified Salesforce consultant to help you manage this process.
 - The data will be sent both for repeat and web based transactions.
 - Invalid data specified in this field may cause transactions to fail.

# Current PSP support

Current support is limited to GoCardless and Sagepay. If you require support for an additional field, or an additional gateway, then let us know at support@asperato.com.

## GoCardless

GoCardless supports sending a description for either a payment or authorisation using a single "description" key.

Example:

```
{"description": "test description"}
```

Note that this is different from setting a custom mandate or payment reference, which can be achieved by setting the "custom reference" field (if you have custom references enabled and available on your GoCardless account.)

## Sagepay

Sagepay supports the use of this field for specifying per-transaction financial institution (6012) data. More information is available [here](https://asperato.github.io/userdocs/docs/fiparams).
