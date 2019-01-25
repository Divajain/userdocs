---
id: gatewaykeys
title: PSP Keys
sidebar_label: PSP Keys
---

Asperato will require keys to connect to a user's payment service provider.

Unfortunately, retrieving these keys is not consistent across providers. For PSPs listed here, you should be able to find the keys using the following instructions. For those not listed, you will need to contact your payment service provider for instructions.

## Authorize.net
To connect Authorize.net to Asperato you will need the values for:

- API Login ID
- Transaction Key

If you don't know what these values are you can create new ones, but beware that this will expire the old ones and will there affect anything that is communicating with Authroize.net via their API.

Go to `Account > Settings > API Credentials & Keys`

## Braintree
The information Asperato needs can be obtained from the Braintree Dashboard.

For test/sandbox this is at <a href="https://sandbox.braintreegateway.com/login">https://sandbox.braintreegateway.com/login</a>

For live/production this is at <a href="https://www.braintreegateway.com/login">https://www.braintreegateway.com/login</a>

On the top of the dashboard screen there is an Account option, and under that appears a `My User` option when you hover over it.

In the My Account screen, towards the bottom, is a section entitled "API Keys, Tokenization Keys, Encryption Keys".  Click on "View Authorizations".

You need to create a new API Key.  Click on the button marked "Generate New API Key".  This will create a new key.  In the line that appears on the screen there is a View link under the heading "Private Key". Click on that.

Asperato then needs the values of the fields marked:<br/>
- Public Key<br/>
- Private Key<br/>
- Merchant ID

## CyberSource
The information that Asperato needs can be obtained from the CyberSource dashboard.

The login page for this is at <a href="https://ebc.cybersource.com/ebc/login/Login.do">https://ebc.cybersource.com/ebc/login/Login.do</a>

Make sure you select either the live or test business center as appropriate.

On the left of the dashboard is a menu.  Select the `Account Management` option and within that `Transaction Security Keys`.

On the panel that displays click the `Security Keys for the SOAP Toolkit API` link.  Press the `Generate Key` button and a box will appear that contains the new key.  You must make a copy of the content of this box because it is the only time it will get displayed.

The information that Asperato then needs are:

- CyberSource Merchant ID<br/>
- Security Key (from the process above)

There is a further element of configuration that you might need to apply to the Cybersource Desktop before the connection is usable.

In the `Account Management` option there is a `Configure IP Settings` section.

If you have restricted the IP ranges that you can log in with then you will need to add the Asperato server addresses to the White List as well.  The IP range restriction is in force if the box marked `Enable IP verification` is checked.

In here you need to add the following IP addresses:
 - For live running - `162.13.56.213`
 - For testing - `77.68.42.36`

## GoCardless
Asperato will redirect you to the GoCardless sign up page to complete your details to obtain a GoCardless account. If you already have a GoCardless Account click the Sign in link at the bottom of the form and enter your details as required. Once complete you will see a message from Asperato confirming the connection.

## Moneris
For testing you will need a username, a store ID and an API key.

1. Sign in at https://developer.moneris.com/ with your username and password (or create an account if you don't have one.)

2. Under "My Profile" on the right hand side, scroll down until you see the "Credentials" section.

3. This should contain the store ID and the API key.  (The other value, your username, is the same that you use to login.)

For the live keys you need to log into your live merchant account at https://esqa.moneris.com/mpg/index.php

Once you are logged in there is an Admin menu option and within that a section called Store Settings.  The API key is displayed at the top of the page.

Asperato require the live store ID and the live API key.

## PayPal
Asperato will need your Client ID and Secret Key.  You can find these in the PayPal developer dashboard.

Go to <a href="https://developer.paypal.com" target="_blank" title="Link to developer dashboard">https://developer.paypal.com</a> and use your PayPal business credentials to log in.

In the options shown on the top right select `Dashboard`.  In the `My Apps & Credentials` menu option there is a section called `REST API apps`.  If no App already exists then click on the `Create App` button and give your new app a suitable name.

Once an App exist you can click on its name in the `REST API apps` section and the keys we need are displayed.  The two keys are Client ID and Secret.  Make sure you select either Sandbox or Live in the box on the top right of the screen to get either the test or live keys as appropriate.

Although not directly related to keys there are some other considerations for using PayPal as a payment route.  The main issue is that PayPal will not let you run any of their screens in an iframe or overlay, and outside of this the whole process is managed by re-direction.  This means that you will need to use the Asperato PostMessage event `asp--redir` to determine where the redirection should go to when using iframe techniques.  The documentation about the Asperato PostMessage events can be found <a href="https://asperato.github.io/docs/templates/#postmessage-events" target="_blank" >here</a>.<br/>
The other set-up issue you need to consider is that because the PayPal payment is managed by re-direction you need to set the Cancel, Success and Fail endpoints on the payment record before you launch the Asperato paypage so that you can control what happens when the payment transaction completes.  The description of these fields can be found <a href="https://asperato.github.io/docs/sf/#payment" target="_blank">here</a>.

## Sage Pay
Asperato will ask you for your Vendor name to connect to Sage Pay. This is the same as your Sage Pay account credentials. If you do not know these, contact your Sage Pay Administrator.

There is an additional configuration task you will need to perform in order to allow Asperato to talk to the Sage Pay gateway (for both the test and live environments) because Sage Pay perform valid IP checks:

- Log into the Sage Pay desktop
- Under the Settings tab there is a Valid IPs option, select that
- Press the Add button
- For testing set the IP address to 077.068.042.036, the Subnet mask to 255.255.255.255 and the Description to Asperato test
- For live running set the IP address to 162.013.056.213, the Subnet mask to 255.255.255.255 and the Description to Asperato live

## Stripe
You will need your API key to connect Stripe to Asperato.
Your API keys are located in your account settings (there is a menu option on the left called `API`).  The key that we need is called the Secret key and you might need to press a button to reveal the value)

If you do not see your API keys, this means that you are not an administrator for the account.

You will need to get in touch with the administrator of your account for the API keys or to request that they make you an administrator in the account’s team settings.

Stripe have implemented a new set of security rules to discourage merchants who might not have implemented appropriate security measures from processing raw card data.  The knock-on effect is that Asperato, who are Level 1 PCI-DSS compliant, will get blocked from processing transactions on your behalf unless this new feature is disabled.  By checking this box you do lot lessen the security of your transactions processed via the Asperato solution (despite Stripe's statements). We are investigating possible solutions with Stripe that do not negatively impact our customers on price or service.

To enable Asperato to take payments on your behalf you will need to make an update to your Stripe configuration.

Go to the URL: <a href="https://dashboard.stripe.com/account/integration/settings">https://dashboard.stripe.com/account/integration/settings</a>

 - Log into Stripe, and on the page that displays click the 'Show advance options' link.<br/>
 - Enable the 'Process payments unsafely' link.<br/>
 - This will open a box with three questions that you have to agree to.<br/>
 - The last question will expect you to key in the name of the company that built the integration.  For this please enter 'Asperato Payment System Ltd'.<br/>
 - Finally, press the 'Process payments unsafely' button:

![Stripe direct API dialog](assets/stripe_config.png "Stripe direct API dialog")

Stripe might then ask you to verify you phone number, but once that is complete then you'll be able to process transactions.

## Vanco
We need four pieces of information:
 - Username
 - Password
 - Client ID
 - Encryption key
 
 This information can be obtained from the setup emails sent by your integrations specialist. If you do not have an integrations specialist or have mislaid the original emails, then you'll need to <a href="http://connect.vancopayments.com/contact-vanco">contact Vanco</a> and ask them for this information.

## Worldpay Online
You need to log onto the <a href="https://online.worldpay.com/login">Worldpay Online Dashboard</a>.
- Ensure you are in TEST mode.
- On the top right of the screen click on `SETTINGS`.
- Select the tab entitled `API Keys`.
- We need the Service key & Client key.
