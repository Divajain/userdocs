---
id: setup
title: Setup
sidebar_label: Setup
---

## Pre install considerations
 
### Trial period
By default, on first install from the Appexchange you will be granted a 60 day trial. You will be able to process test payments during this period. After the trial period you will be required to sign up to a yearly subscription. Please contact us for a detailed quote / contract.
 
### Upgrade an existing package
Asperato is a managed package, and can thus be <a href="https://help.salesforce.com/articleView?id=distribution_upgrading_packages.htm&amp;type=5" target="_blank">upgraded the same way you would install any other package.</a> Simply paste the link into the browser while logged into the Salesforce org, and follow the upgrade instructions.
 
### Supported Salesforce versions, Lightning vs Classic
The Asperato package can be used in both Lightning and Classic mode, the functionality is identical. The only exception is that initial ‘Setup’ needs to be completed in Lightning. The tabs are the same, and the buttons that appear as lightning quick actions in lightning experience will appear as standard Salesforce buttons in Salesforce Classic.

<a target="_blank" href="https://help.salesforce.com/articleView?id=000230642&amp;type=1">Users may switch between either interface without affecting functionality.</a>

### Paths
If you're using Asperato in Lightning experience, we provide paths on our objects to give you a visual display of the payment or authorisation status. If you wish to use these paths, you'll need to <a href="https://help.salesforce.com/articleView?id=path_enable.htm&type=5" target="_blank">follow the instructions here to enable paths.</a>
 
## Installing the package
Asperato ONE is installed <a href="https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3A00000EcrOnUAJ" target="_blank">from the Salesforce Appexchange.</a> After installation, head to the "Asperato Setup" tab and follow the on-screen instructions to complete the installation. 
 
Please note you must be in Lightning to complete this setup and have <a href="https://help.salesforce.com/articleView?id=domain_name_overview.htm&r=https%3A%2F%2Fwww.google.com%2F&amp;type=5" target="_blank">My Domain</a> configured.  
 
## Connect Salesforce to Asperato
Asperato is a Connected App. To securely connect Salesforce to Asperato:

 - Ensure you are in lightning experience, not classic
 - Navigate to the Asperato ONE app
 - Click on the "Asperato Setup tab"
 - Click the "Setup configuration" button

If you've completed the above successfully, you should see something like the following:

![Setup successful](/userdocs/img/overview/setup_success.png "Setup successful")
 
## Connecting Salesforce to your chosen Payment Service Providers
On the Asperato Setup page you will see a list of pre-connected payment service providers. These allow you to take immediate test payments. If you wish to connect your own payment service provider, [please see the instructions here](connectingpsp).
 
## Create your first payment request
*We're assuming you're connected to Stripe as a test gateway, which is the default on installing the package. If you've connected to another gateway instead, please see their documentation for appropriate test card details.*

Try out the connection and take a simple, one-off card payment:

- Navigate to the "Payments" tab
- Create a new Payment record:
  - For "Amount", select 10
  - For "Payment route", select card
- When the payment record has been created, click the "Process payment button".
- Fill in the form that appears using the following details:
  - Card number: `4242424242424242`
  - Name: `Boris Smith`
  - Expiry date: `10/22`
  - CVV: `123`

*Note that you should **never** use real card details in a test payment form. Doing so is insecure, and means you could be breaking PCI compliance regulations.*
 
Refresh the Salesforce payment record once complete to see the payment record completed. Congratulations - you've taken your first test payment!

## User permissions
You probably won't want all your Salesforce users to have permission to take payments. Asperato ONE ships with 3 <a href="https://help.salesforce.com/articleView?id=perm_sets_overview.htm&type=5" target="_blank">permission sets</a> that you can apply to relevant users in your org:

 - **Asperato standard user** - A user with this permission can setup payments, authorisations and payment schedules.
 - **Asperato refund user** - In addition to the above, this permission allows a user to issue refunds.
 - **Asperato full admin** - In addition to the above, this permission set provides access to all setup and administration features in the package.
