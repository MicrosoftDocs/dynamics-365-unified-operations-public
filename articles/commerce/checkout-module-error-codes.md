---
# required metadata

title: Checkout module error reference codes
description: This article describes the checkout module error reference codes that are shown in user-facing error messages in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 10/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2022-09-20

---

# Checkout module error reference codes

[!include [banner](includes/banner.md)]

This article describes the checkout module error codes that are shown in user-facing error messages in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce has introduced standardized error references that can be included in online channel checkout errors that are presented to online customers. In Commerce version 10.0.31 and later, error messages in the checkout module include error codes and don't show unnecessary information to the online customer. The error codes refer to errors that are detailed in this article.

Depending on the error that is encountered, the table in this article includes the following details:

- A description of the condition that caused the error, or additional details
- Information for consideration in the environment or payment connector configurations
- Information that can be referenced in a support case, if additional assistance is required

## Prerequisites

To enable the checkout module error reference codes listed below, in site builder for your site, go to **Site settings \> Extensions**, and in the **Cart and checkout** section, select **Enable Enhanced Online Channel Error Display Messaging**. 

## Checkout module error reference codes

Use the following table to get more details about error code references that are provided by customers or experienced in the online store. Scroll to the right to view the **Error Description** column.

| Error code | Dynamics-correlated error code | Error description |
| ---------- | ------------------------------ | ----------------- |
| CCR001     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToAuthorizePaymentCardTypeMissingOrNotSupported | The payment couldn't be authorized. Card Type ID in **TokenizedPaymentCard** is missing, or Card Type ID provided isn't supported. |
| CCR002     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToAuthorizePayment | Declined. The payment couldn't be authorized. |
| CCR003     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToAuthorizePaymentCardAdditionalContextRequired | The payment couldn't be authorized. Additional information required from the customer. |
| CCR004     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToRetrieveCardPaymentAcceptResult | Sorry, something went wrong. We were unable to obtain the card payment accept result. Try again or contact your system administrator. |
| CCR005     | Microsoft\_Dynamics\_Commerce\_Runtime\_PaymentRequiresMerchantProperties | Unable to make payment because of missing merchant payment properties. Contact your system administrator. |
| CCR006     | Microsoft\_Dynamics\_Commerce\_Runtime\_InvalidPaymentRequest | Unable to retrieve tender service for the operation. Check your payment method setup for the tender type selected. |
| CCR007     | Microsoft\_Dynamics\_Commerce\_Runtime\_MultipleCustomerAccountPaymentsNotAllowed | A customer account payment has already been applied and only one payment is allowed per transaction. |
| CCR008     | Microsoft\_Dynamics\_Commerce\_Runtime\_CustomerAccountLimitSignDifferentFromAmountDue | The customer account limit differs from the amount due. Try a different payment method or contact customer support for assistance. |
| CCR009     | Microsoft\_Dynamics\_Commerce\_Runtime\_CustomerAccountPaymentExceedsTotalAmountForCarryOutAndReturnItems | The customer account payment exceeds the total due for the listed items. Try again later or contact customer support for assistance. |
| CCR010     | Microsoft\_Dynamics\_Commerce\_Runtime\_PaymentUsingUnauthorizedAccount | The customer account payment requires its own account or matching invoice account on a tender line. |
| CCR011     | Microsoft\_Dynamics\_Commerce\_Runtime\_CustomerAccountPaymentExceedsCustomerAccountFloorLimit | Unable to process a customer account payment at this time – floor limit value exceeded. |
| CCR012     | Microsoft\_Dynamics\_Commerce\_Runtime\_CustomerAccountPaymentForCustomerWithoutAllowOnAccount | This customer isn't allowed to pay on account. |
| CCR013     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToCancelPayment | Sorry, something went wrong. The payment couldn't be canceled. Try again. |
| CCR014     | Microsoft\_Dynamics\_Commerce\_Runtime\_UnableToReadCardTokenInfo | An error occurred when processing the payment. Try again later. |
| CCR015     | Microsoft\_Dynamics\_Commerce\_Runtime\_NotEnoughRewardPoints | The loyalty payment amount exceeds what is allowed for the loyalty card used in this transaction. |
| CCR016     | Microsoft\_Dynamics\_Commerce\_Runtime\_RefundAmountMoreThanAllowed | The loyalty refund amount exceeds what is allowed for the loyalty card used in this transaction. |
| CCR017     | Microsoft\_Dynamics\_Commerce\_Runtime\_InvalidLoyaltyCardNumber | The loyalty card number wasn't found. Either activate the loyalty card number or enter a different card number, and then try again. |
| CCR018     | Microsoft\_Dynamics\_Commerce\_Runtime\_BlockedLoyaltyCard | The loyalty card number isn't available. Enter a different card number, and then try again. |
| CCR019     | Microsoft\_Dynamics\_Commerce\_Runtime\_NoTenderLoyaltyCard | This loyalty card isn't eligible to redeem loyalty points for this transaction. |
| CCR020     | Microsoft\_Dynamics\_Commerce\_Runtime\_GiftCardCurrencyMismatch | The gift card number encountered an error. Try a different gift card or contact customer support for assistance. |
| CCR021     | Microsoft\_Dynamics\_Commerce\_Runtime\_PaymentAmountExceedsGiftBalance | The amount exceeds the balance on the gift card. Enter a different amount and then try again. |
| CCR022     | Microsoft\_Dynamics\_Commerce\_Runtime\_NoMoreThanOneLoyaltyTender | The transaction can't contain more than one loyalty payment line. |
| CCR023     | Microsoft\_Dynamics\_Commerce\_Runtime\_PaymentAlreadyVoided | The payment information is either missing information or incorrect. Verify the payment information and then try again. |
| CCR024     | Microsoft\_Dynamics\_Commerce\_Runtime\_FraudRisk | The order can't be processed at this time. Try again later. |
| CCR025     | Front End Timeout for Checkout API | The front end operation has timed out. Confirm if the order has been processed in Dynamics 365 Commerce headquarters. |
| CCR026     | Original Authorized Amount Changed | The order amount has changed from the original authorization amount processed with the payment gateway. This may be due to a timed expiration of a coupon, promotion, or sale. |
| CCR027     | Microsoft\_Dynamics\_Commerce\_Runtime\_InvalidCartVersion | An error occurred when processing a payment. The reference provided to the Cart API has a different reference than expected (noting potential inconsistency during the checkout process). |
| CCR028     | Microsoft\_Dynamics\_Commerce\_Runtime\_MissingRequiredCartTenderLines | The payment method attempted has encountered an error. Contact support to review your account settings or try again with a different payment method. |

## Additional resources

[Payments FAQ](dev-itpro/payments-retail.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)
