---
# required metadata

title: Checkout Module Error Codes
description: This article references the checkout module error code references provided in the user-facing error messages.
author: BrianShook
ms.date: 10/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2022-09-20

---

# Checkout Module Error Codes

Dynamics 365 Commerce is introducing standardized error references to be included in online channel checkout errors presented to online shoppers. Available in 10.0.31 and higher, error messages in the checkout module will now include an error reference that will be detailed in this article. These error references allow for referencing conditions of the error through this article without displaying unnecessary information to the online shopper. Depending upon the error encountered, the table below will:

- Describe the condition that caused the error or provide additional details
- Provide information for consideration in the environment or payment connector configurations
- Include information that can be referenced in a Support Case if needed for additional assistance

## Checkout Module Error Reference codes

Use the following table to reference an error code reference provided by a customer or experienced on the online store for additional details of the code.

| Error Code | Dynamics Correlated Error Code                               | Error Description                                            |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| CCR001     | Microsoft_Dynamics_Commerce_Runtime_UnableToAuthorizePaymentCardTypeMissingOrNotSupported | The payment couldn't be authorized. Card Type Id in 'TokenizedPaymentCard' is missing or provided Card Type Id is not supported. |
| CCR002     | Microsoft_Dynamics_Commerce_Runtime_UnableToAuthorizePayment | Declined. The payment couldn't be authorized.                |
| CCR003     | Microsoft_Dynamics_Commerce_Runtime_UnableToAuthorizePaymentCardAdditionalContextRequired | The payment couldn't be authorized. Additional information required from the customer. |
| CCR004     | Microsoft_Dynamics_Commerce_Runtime_UnableToRetrieveCardPaymentAcceptResult | Sorry, something went wrong. We were unable to obtain the card payment accept result. Try again or contact your system administrator. |
| CCR005     | Microsoft_Dynamics_Commerce_Runtime_PaymentRequiresMerchantProperties | Unable to make payment because of missing merchant payment properties. Contact your system administrator. |
| CCR006     | Microsoft_Dynamics_Commerce_Runtime_InvalidPaymentRequest    | Unable to retrieve tender service for the operation. Check your payment method setup for the tender type selected. |
| CCR007     | Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountPaymentsNotAllowed | A customer account payment has already been applied and only one is allowed per transaction. |
| CCR008     | Microsoft_Dynamics_Commerce_Runtime_CustomerAccountLimitSignDifferentFromAmountDue | The Customer Account limit differs from the amount due. Try a different payment method or contact Customer Support for additional assistance. |
| CCR009     | Microsoft_Dynamics_Commerce_Runtime_CustomerAccountPaymentExceedsTotalAmountForCarryOutAndReturnItems | The Customer Account payment exceeds the total due for the listed items. Try again later or contact Customer Support for additional assistance. |
| CCR010     | Microsoft_Dynamics_Commerce_Runtime_PaymentUsingUnauthorizedAccount | Customer account payment requires its own account or matching invoice account on a tender line. |
| CCR011     | Microsoft_Dynamics_Commerce_Runtime_CustomerAccountPaymentExceedsCustomerAccountFloorLimit | Unable to process a customer account payment at this time – floor limit value exceeded. |
| CCR012     | Microsoft_Dynamics_Commerce_Runtime_CustomerAccountPaymentForCustomerWithoutAllowOnAccount | This customer is not allowed to pay on account.              |
| CCR013     | Microsoft_Dynamics_Commerce_Runtime_UnableToCancelPayment    | Sorry, something went wrong. The payment could not be canceled. Try again. |
| CCR014     | Microsoft_Dynamics_Commerce_Runtime_UnableToReadCardTokenInfo | An error occurred when processing the payment. Try again later. |
| CCR015     | Microsoft_Dynamics_Commerce_Runtime_NotEnoughRewardPoints    | The loyalty payment amount exceeds what is allowed for this loyalty card in this transaction. |
| CCR016     | Microsoft_Dynamics_Commerce_Runtime_RefundAmountMoreThanAllowed | The loyalty refund amount exceeds what is allowed for this loyalty card in this transaction. |
| CCR017     | Microsoft_Dynamics_Commerce_Runtime_InvalidLoyaltyCardNumber | The loyalty card number wasn't found. Either activate the loyalty card number or enter a different card number, and then try again. |
| CCR018     | Microsoft_Dynamics_Commerce_Runtime_BlockedLoyaltyCard       | The loyalty card number is not available. Enter a different card number, and then try again. |
| CCR019     | Microsoft_Dynamics_Commerce_Runtime_NoTenderLoyaltyCard      | This loyalty card is not eligible to redeem loyalty points for this transaction. |
| CCR020     | Microsoft_Dynamics_Commerce_Runtime_GiftCardCurrencyMismatch | The gift card number encountered an error. Try a different gift card or contact Customer Support for additional assistance. |
| CCR021     | Microsoft_Dynamics_Commerce_Runtime_PaymentAmountExceedsGiftBalance | The amount exceeds the balance on the gift card. Enter a different amount and then try again. |
| CCR022     | Microsoft_Dynamics_Commerce_Runtime_NoMoreThanOneLoyaltyTender | The transaction cannot contain more than one loyalty payment line. |
| CCR023     | Microsoft_Dynamics_Commerce_Runtime_PaymentAlreadyVoided     | The payment information is either missing information or it is incorrect. Verify the payment information and then try again. |
| CCR024     | Microsoft_Dynamics_Commerce_Runtime_FraudRisk                | The order cannot be processed at this time. Try again later. |
| CCR025     | Front End Timeout for Checkout API                           | The front end operation has timed out. Confirm if the order has processed in Dynamics 365 Commerce Headquarters. |
| CCR026     | Original Authorized Amount Changed                           | The order amount has changed from the original authorization amount processed with the payment gateway. This may be due to a timed expiry of a coupon, promotion, or sale. |
| CCR027     | Microsoft_Dynamics_Commerce_Runtime_InvalidCartVersion       | An error occurred when processing a payment. The reference provided to the Cart API has a different reference than expected (noting potential inconsistency during the checkout process). |
| CCR028     | Microsoft_Dynamics_Commerce_Runtime_MissingRequiredCartTenderLines | The payment method  attempted has encountered an error. Contact support to review your account settings or try again with a different payment method. |

## Additional resources

[Payments FAQ](dev-itpro/payments-retail.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)
