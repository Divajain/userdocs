---
id: paypage
title: Payment page
sidebar_label: Payment page
---

The standard payment template is provided by Asperato and will look similar to the following:

![Asperato standard payment template](/userdocs/img/asperato_template.png "Asperato standard template")

## Template features

Out of the box, the template is highly dynamic and responds to a number of different parameters:

 - Amount
 - Frequency (including one off payments)
 - Payment types (including combinations of payment types, such as Card & Direct Debit, Paypal & Direct Debit, Card, Paypal & eCheck, etc.)
 - Address data (can be pre-populated)
 - URL to navigate to on completion of the payment
 
The template also has the following dynamic elements built in:
 
  - Notification if the Salesforce webservice cannot be contacted
  - UK postcode checker & lookup
  - Display of card type based on card number
  - Validation of card number using Luhn algorithm
  - Display of issue number & start date fields only if the card requires it
  - Validation of security code as 3 or 4 digits depending on the card type
  - Ability to switch between Card, Direct debit, eCheck or Paypal on the fly
  - Ability to enter IBAN or distinct local bank details for all BACS / SEPA European Direct Debit countries
  - Automatic hiding / showing and labelling of local bank detail fields based on selected country
  - Compliant to BACS and SEPA scheme rules, correct compliance labelling is determined by scheme rules in the selected country
  - Choice of payment type to show by default
  
The template is fully responsive, works on all the latest versions of major browsers, and is routinely updated by Asperato to work with new card ranges and payment types.

## Minor stylistic changes

Minor stylistic changes, such as the fonts, colours and logo used can be made by Asperato. The full list of these changes includes:

- Changing page font
- Changing button colours (text and background in both normal and hover mode, and border)
- Changing link colour
- Changing the logo (ideal size is 400px wide and 80px high, though the height is the key factor.  Any bigger and you risk truncation)
- Changing the page title
- Hide / show "pay as company" link
- Hide / show postcode lookup
- Hide / show billing address
- Switch between IBAN and local details for Direct Debits
- Change the 'processing' gif from the default gears

If you would like any customised changes in this regard, contact support@asperato.com with details of the changes required.

## Using the template as an overlay

The simplest way of using the template is as an overlay - this can be achieved by inserting minimal Javascript into an existing web page.

Please note that this overlay library is intended to be used as a simple mechanism to show a payment page overlay that then returns back to the place it started from.  If you want to do anything more sophisticated then you should look at the source of the library and create your own version of it.

The parameters that are used for setting up the overlay are equivalent to the parameters specified in the "eCommerce URL" (which can be found on any payment record, or in the case of the NPSP extension, on the campaign record):

 - The "pid" parameter on the URL is the "paymentRef" parameter on the overlay;
 - The "pmRef" parameter on the URL is the "customerRef" parameter on the overlay.

For example, if the URL on a payment record is `https://demo.protectedpayments.net/PMWeb1?pmRef=121&pid=a031n00000XGkm5`, then the `customerRef` parameter would be `121`, and the `paymentRef` parameter would be `a031n00000XGkm5`.

To use the template as an overlay, just three bits of Javascript are needed:

 - The following should be inserted in the `<head>` tag of the document:

```html
<script src="https://live.protectedpayments.net/asperato-form-1.0.js"></script>
```
    
 - The following also needs to be inserted somewhere in the initialisation of the page (eg. in `<head>` or `window.onload`):

```javascript
let form = new PaymentFormDisplay(
    {
        customerRef: 9797 //Replace with your customer reference
    }
);
```
    
As per the comment, the customer reference `9797` is an example and will need to be changed to your unique reference (obtained when you sign up for an Asperato account.)
    
 - The following code will need to be called to show the form (such as in the `onclick` attribute of a button):

```javascript
form.showForm(
    {
        paymentRef: "a030Y008393c4E4"
    }
);
```

The above example will show the form for a particular payment reference in Salesforce, and will be pre-populated with the relevant details (amount, frequency, and so on.)

If using the NPSP extension with Asperato, a campaign reference can also be supplied in the same way:

```javascript
form.showForm(
    {
        campaignRef: "7020Y000012RFJQ"
    }
);
```

You may also set the default payment type shown on the payment page:

```javascript
form.showForm(
    {
        paymentRef: "a030Y008393c4E4",
        defaultPayType: "dd" //"card", "dd", "paypal" or "echeck"
    }
);
```

The above will allow the user to select the frequency, amount, and billing address - if necessary these details may be pre-populated as in the following example:

```javascript
form.showForm(
	{
		campaignRef: "7020Y000012RFJQ",
		amount: 50.58,
		frequency: "Annual",
		firstName: "Frank",
		lastName: "Tomlin",
		email: "frank.tomlin@asperato.com",
		address1: "94 Milky Way",
		address2: "Mars Court",
		city: "Winchester",
		county: "Wessex",
		country: "GB",
		postcode: "WE1 3QX"
	}
);
```

This is the full list of showForm parameters that are supported by the sample Asperato overlay library:
<table>
  <tr>
    <th>Parameter name</th>
    <th>Usage</th>
  </tr>
  <tr>
   <td>address1</td>
   <td>First line of the billing address</td>
  </tr>
  <tr>
   <td>address2</td>
   <td>Second line of the billing address</td>
  </tr>
  <tr>
   <td>amount</td>
   <td>The payment amount (can be either an integer or a decimal)</td>
  </tr>
  <tr>
   <td>city</td>
   <td>The city value in the billing address</td>
  </tr>
  <tr>
   <td>country</td>
   <td>The country of the billing address</td>
  </tr>
  <tr>
   <td>county</td>
   <td>The county or state of the billing address</td>
  </tr>
  <tr>
   <td>currency</td>
   <td>An ISO 4217 currency code</td>
  </tr>
  <tr>
   <td>defaultPayType</td>
   <td>Where several payment routes are allowed this will set the default condition. When used must be one of: card, dd, paypal or echeck</td>
  </tr>
  <tr>
   <td>email</td>
   <td>The email address</td>
  </tr>
  <tr>
   <td>firstName</td>
   <td>The first name in the billing name details</td>
  </tr>
  <tr>
   <td>frequency</td>
   <td>The payment frequency allowed.  Can be one of Annual, Monthly, Quarterly or Single</td>
  </tr>
  <tr>
   <td>lastName</td>
   <td>The last name in the billing name details</td>
  </tr>
  <tr>
   <td>paymentRef</td>
   <td>The Salesforce ID of a Payment record and is the pid parameter of the URL shown in the "eCommerce URL" field</td>
  </tr>
  <tr>
   <td>postcode</td>
   <td>The postcode or zip code of the billing address</td>
  </tr>
</table>

### Warnings & Errors
If you run into problems then we would advise keeping an eye on your browser's console - many common issues (unknown fields, required fields not specified, field vales in the wrong format, etc.) are printed there as warnings or errors.

## Using the template in an iframe

Many customers wish to use the template in an iframe as part of their existing site, rather than displaying it as a standalone page - this is supported by Asperato, as long as the containing site is served over TLS1.2 or newer. Please make sure your iframe element is large enough to contain the payment form without any scrollbars. We recommend a size of at least 500px width and 1000px height.

Non-secure pages may not iframe the Asperato payment page in this way, as customers have no easy way of determining that the iframe itself is secure if the surrounding page is not.

### PostMessage events
There are a number of standard postmessage events that occur when the template is operating in iframe mode.  The postmessage content is a simple string.  The values and their related events are documented in the table below.

<table>
  <tr>
    <th>Text string</th>
    <th>Event</th>
  </tr>
  <tr>
    <td>asp--redir:REDIR URL</td>
    <td>On redirect to an external authorisation page (such as in the case of Paypal.) This message contains the value of that URL, so on receiving this message the parent page may choose to close the iframe and launch the new in a new tab / window.</td>
  </tr>
  <tr>
    <td>asp--exit-screen</td>
    <td>On load of the payment success screen</td>
  </tr>
  <tr>
    <td>asp--error--value:ERROR MESSAGE</td>
    <td>On load of the payment error screen, this message contains the value of the error message displayed to the user.</td>
  </tr>
  <tr>
    <td>asp--error-screen</td>
    <td>On load of the payment error screen</td>
  </tr>
  <tr>
    <td>asp--error</td>
    <td>When the Close Without Retry button is pressed on the error page</td>
  </tr>
  <tr>
    <td>asp--complete</td>
    <td>When the Finish button is pressed on the exit page</td>
  </tr>
  <tr>
    <td>asp--cancel</td>
    <td>When the cancel link is pressed on the main pay page</td>
  </tr>
  <tr>
    <td>asp--dddialog</td>
    <td>When the DD confirmation dialog box is displayed (allows the parent frame to refocus the iframe using "window.scrollTo(0,0)")</td>
  </tr>
</table>

By implementing an appropriate listener in the parent HTML you can make decisions based on these postmessage events.<br/>
For example if you want to suppress the display of the success screen then you can close the iframe when the listener detects the text content "asp--exit-screen" in the body of the postmessage.

Please note that we may add additional postmessage events from time to time - you must make sure that your integration won't cause an error if it receives a postmessage that it doesn't know about (ignoring it is fine.)