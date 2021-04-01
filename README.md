multipassify
============

Shopify Multipass module for Node.js



[Shopify](http://shopify.com) provides a mechanism for single sign-on known as Multipass.  Multipass uses an AES encrypted JSON hash and multipassify provides functions for generating tokens

More details on Multipass with Shopify can be found [here](http://docs.shopify.com/api/tutorials/multipass-login).

## Installation
<pre>
    npm install brijcodeclouds/multipassify
</pre>

## Usage

To use Multipass an Enterprise / Plus plan is required. The Multipass secret can be found in your shop Admin (Settings > Checkout > Customer Accounts).
Make sure "Accounts are required" or "Accounts are optional" is selected and Multipass is enabled.

``` js
  var Multipassify = require('multipassify');

  // Construct the Multipassify encoder
  const multipassify = new Multipassify("SHOPIFY MULTIPASS SECRET");

  // Create your customer data hash
  const customerData = { email: 'test@example.com'}

  // Encode a Multipass token
  multipassify.encode(customerData);

// Generate a Shopify multipass token, returns the multipasstoken which can be used with Shopify's storefront Graph QL to generate the customer access token https://shopify.dev/docs/storefront-api/reference/customers/customeraccesstokencreatewithmultipass
const multiPasstoken = multipassify.generateMultipassToken(customerData); 
