# LoyalShopper Customer Side Testing
A LoyalShopper solution can be tested in two ways: as a merchant (the Shopify store owner) or as a customer (the Shopify store buyer). 
This document describes the **customer side testing scenario**. The merchant side testing scenario will be described in a separate document as it is more complex because it requires creating a new Shopify development store.  
## Testing Environment
LoyalShopper customer testing environment consists of three major parts:

### [Shopify Store](https://loyalshopper-dev-store-local.myshopify.com/)
This is a demo Shopify store created by the team for the public testing of reward transactions. Note that you cannot make a real purchase in this store - the payment can be done only using a special test card number (see below). 

### [LoyalShopper App](https://loyalshopper-testnet.lyra.live/)
This is the merchant reporting UI and reward program configuration tool. 
In production environments, this application will be available through Shopify app marketplace for any Shopify store owner to install in their store.
It is already installed in the demo store by the team. 
In this testing scenario, the configuration of Loyal Shopper Demo Store is only accessible for the team (as a “merchant”).

### [Lyra Wallet App](https://github.com/LYRA-Block-Lattice/LYRA-Docs/blob/master/How%20to%20run%20Lyra%20CLI%20Wallet%20on%20testnet.md)
This is the customer (buyer) wallet app that allows the customers (testers during the testing) to check their accumulated reward tokens
and redeem those rewards to actual discount codes that can be used during LoyalShopper Demo Store checkout. 
Currently, only CLI (command line interface) wallet is integrated with LoyalShopper, 
but in the near future wallet apps for Android, iOS, and Windows will be available as well.

## Testing Steps
In order to test LoyalShopper rewards solution, perform the following steps:

1. Make a purchase in LoyalShopper Demo Store.
* Go to [LoyalShopper Demo Store](https://loyalshopper-dev-store-local.myshopify.com/).
* Click on one of the items (for example, “Dark Roast”), and click `ADD TO CART` button.
* Click the `View Cart` button and then `Checkout` button.
* Enter your email address and shipping address (any address will work). 

**Note** that the shipping address can be fake because this is not a real purchase, 
but the email address must be your real email address because the reward points will be sent to you using this email address.
* To make a payment, use one of the test credit card numbers, for example: 

`4242 4242 4242 4242`

Name: `X X` 

Expiration date: `12/21`

Security Code: `123`

* Click the `Pay now` button.

2. Check your email - you should receive two emails: 
* First email from `LoyalShopper Demo Store <info@lyra.live> via shopify.com` confirming the order, and 
* Second email from `shopify@lyra.live` with the subject `You've earned X reward tokens!`.

![reward email sample](https://i.imgur.com/WTVO2NM.png)

Open the second email and follow the instructions (see details below).

3. Download and install *Lyra CLI wallet* - follow instructions in [this document](https://github.com/LYRA-Block-Lattice/LYRA-Docs/blob/master/How%20to%20run%20Lyra%20CLI%20Wallet%20on%20testnet.md)

4. After you created a new account, enter `import` command. When prompted to enter the private key, copy/paste the private key from the email, and press `Enter`. 
Enter `sync` command to receive the rewards. You should see the balance of reward tokens on your account.
	 
**Note:** you need to import the private key from the email only once. All further rewards will be automatically sent to your account.  

5. To use your rewards, enter `redeem` command, then enter the name of the reward token: `loyalshopper-dev-store-local/Rewards11`, 
and then enter a discount amount (for example, 1).

Enter `sync` command - you should see something like this:

`Shopify Discount: $1.00 Redemption Code: E7NH-HQTC-FUJG-NMSR`

6. Go back to the Shopify store and run a new transaction (purchase another item). 
Go through the checkout process as described above. On the payment screen (where you prompted to enter credit card information), 
enter the redemption code into the `Discount Code` field and click `Apply` button. You should see a $1 discount applied to your total. 
Finish the transaction by clicking the `Pay now` button. You successfully used your LoyalShopper rewards!
