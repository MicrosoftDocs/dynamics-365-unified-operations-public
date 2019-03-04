## BUSINESS VALUE
Returns are an integral operation for a Retailer. The ability to accept returns for sales and refund the payments to the customer allows the Retailer an option to service their customers’ needs and issues. Return policies and Refund guidelines are generally set at a company level and enforced at a store level with certain privileges for Cashiers and a few over-ride permissions for the managers/senior staff.  
 
 
## FEATURE DESCRIPTION
Dynamics 365 for Retail has returns capabilities which allow Retailers to currently process returns & their refunds. However, the functionality is not fully capable to assist Retailers to set restrictions on requirements for receipts, ability to process funds to multiple tender types. 

With the current set of capability, Retailers can process refunds to Cards, but these must be manually specified by the cashier. Cashiers are not able to process the funds to the original mode of payment(s) unless provided by the customer. Call center orders do not have any traceability to the mode of payment made – Dynamics 365 does not store any information on the type of payment made from call centers and there is no way to validate what the customer specified as a mode of payment is valid as the one used for purchase. 

This new feature outlines the improvements that needs to be made to the ‘Returns’ function in Dynamics 365 for Retail application to have a better functionality and flexibility for the Retailers to use the original payment as the return payment mode. 
 
### In scope :
Cashiers can now process refund to card used during original transaction without the card being present for return.
- Linked refunds for cash and carry using credit/debit cards.
- Linked refunds for customer orders using credit/debit cards.
 
### Out of scope :
Linked refunds with gift cards.
Linked refunds with loyalty cards.
Exchange orders support.
Multiple return orders in the same transaction.
 
 
## Who uses this feature
This feature will be used by the customer developer or partner/ISV to use linked refunds via POS, center or e-Commerce channels.
 
### License Required
No
 
### Setup Required
If the customer is not using Adeyn Connector out of box implementation, they will have to set up the connector that supports tokenization of credit cards.

