# Customer loyalty cards and reward points
[!include banner]
[!include banner]

Businesses classify customers and provide sophisticated services based on their shopping and spending patterns. Among Dynamics 365
suite of applications, Commerce application has the infrastructure and functions to facilitate and handle customer loyalty cards,
reward points, loyalty-based pricing, rewards-based shopping experience, etc. When customer loyalty and reward points data from
Commerce application is exposed to Common Data service, other apps based on Common Data Service can use them. For example, Customer Service application users can use the data to provide the same sophisticated service through the help desk.

## Templates

Finance and Operations | Other Dynamics 365 apps | Description
-----------------------|--------------------------------|---
LoyaltyCard | msdyn_loyaltycards |
LoyaltyRewardPoints | msdyn_loyaltyrewardpoints |

## FO.LoyaltyCard--CDS.msdyn_loyaltycards

Source field | Map type | Destination field
---|---|---
CARDNUMBER | = | msdyn_cardnumber
CARDTENDERTYPE | >< | msdyn_cardtendertype
PARTYNUMBER | = | msdyn_partynumber
REPLACEMENTCARDNUMBER | > | msdyn_replacementcardnumber
OMOPERATINGUNITNUMBER | = | msdyn_operatingunitnumber
LOYALTYENROLLMENTDATE | = | msdyn_enrollmentdate

## FO.LoyaltyRewardPoints--CDS.msdyn_loyaltyrewardpoints

Source field | Map type | Destination field
---|---|---
EXPIRATIONTIMEUNIT | >< | msdyn_expirationtimeunit
EXPIRATIONTIMEVALUE | = | msdyn_expirationtimevalue
REDEEMABLE | >< | msdyn_redeemable
REDEEMRANKING | = | msdyn_redeemranking
REWARDPOINTCURRENCY | = | msdyn_rewardpointcurrency.isocurrencycode
REWARDPOINTID | = | msdyn_rewardpointid
REWARDPOINTTYPE | >< | msdyn_rewardpointtype
MAXIMUMLOYALTYREWARDPOINTS | = | msdyn_maximumloyaltyrewardpoints
VESTINGTIMEUNIT | >< | msdyn_vestingtimeunit
VESTINGTIMEVALUE | = | msdyn_vestingtimevalue
