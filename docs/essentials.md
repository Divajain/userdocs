---
id: essentials
title: Essentials
sidebar_label: Essentials
---

## Pre install considerations
 
### Trial period
By default, on first install from the Appexchange you will be granted a 60 day trial. You will be able to process test payments during this period. After the trial period you will be required to sign up to a yearly subscription. Please contact us for a detailed quote / contract.
 
### Upgrade an existing package
Asperato is a managed package, and can thus be [upgraded the same way you would install any other package](https://help.salesforce.com/articleView?id=distribution_upgrading_packages.htm&type=5). Simply paste the link into the browser while logged into the Salesforce org, and follow the upgrade instructions.
 
### Supported Salesforce versions, Lightning vs Classic
The Asperato package can be used in both Lightning and Classic mode, the functionality is identical. The only exception is that initial ‘Setup’ needs to be completed in Lightning. The tabs are the same, and the buttons that appear as lightning quick actions in lightning experience will appear as standard Salesforce buttons in Salesforce Classic.

[Users may switch between either interface without affecting functionality.](https://help.salesforce.com/articleView?id=000230642&type=1)
 
## Installing the package
The installation file can be downloaded from the Salesforce Appexchange. 
Then simply head to the ‘Asperato Setup’ tab and follow the on-screen instructions to complete the installation. 
 
Please note you must be in Lightning (see help) to complete this setup and have MyDomain (see help) configured. 
 
If you would like more information on how to install a package from the Appexchange, please see the Salesforce documentation here. 
 
## Connect Salesforce to Asperato
Asperato is a Connected App follow the onscreen instructions to securely connect Salesforce to Asperato.
 
## Connecting Salesforce to your chosen Payment Service Providers
On the Asperato Setup page you will see a list of pre-connected payment service providers. These allow you to take immediate test payments. At any stage you can connect your own PSP by following the instructions.
 
## Create your first payment request
Try out the connection and take a simple card payment.
Create new ‘Payment’ record, populate an amount of £10, select ‘Card’ as payment route, Enter contact details. Us the ‘Process Payment’ button or payment URL. Populate with test card details: `42424242424242`, any name, expiry date `10/22`, CVV `123`.
 
Refresh the Salesforce payment record once complete to see the record completed.