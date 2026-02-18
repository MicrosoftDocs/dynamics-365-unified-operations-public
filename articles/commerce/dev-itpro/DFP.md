---
title: Dynamics 365 Fraud Protection integration with Dynamics 365 Commerce
description: Learn about out-of-box integrations that are available between Microsoft Dynamics 365 Fraud Protection and Microsoft Dynamics 365 Commerce. 
author: BrianShook
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-01-01
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Dynamics 365 Fraud Protection integration with Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This article describes out-of-box integrations that are available between Microsoft Dynamics 365 Commerce and Microsoft Dynamics 365 Fraud Protection.

Fraud Protection is a service that offers fraud protection solutions to help retailers prevent fraudulent activity and identify places where fraud might go unnoticed. This article describes out-of-box integrations between Fraud Protection and Commerce. It is updated as new integrations between the two services are released. For more information about Fraud Protection, including information about modules that aren't yet supported by an out-of-box integration with Commerce, visit the [Fraud Protection landing page](https://dynamics.microsoft.com/ai/fraud-protection/). You can also [request a callback](https://dynamics.microsoft.com/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative to discuss how Fraud Protection can help boost profitability, reduce operational expenses, and improve customer experiences.

Starting October 2020, a limited capacity of Fraud Protection is included in the Microsoft Dynamics 365 Commerce license. Commerce customers can now use Fraud Protection at no extra charge, up to the following limits:

- **Purchase protection** - Up to 2,000 assessments per month.
- **Account protection** - Up to 20,000 assessments per month.
- **Loss prevention** - Up to 8,000 transactions per month.

You can purchase more Fraud Protection add-ons if your usage requires higher limits.

To start using Fraud Protection as an existing Commerce customer, visit the [Fraud Protection portal](https://dfp.microsoft.com/), sign in with tenant administrator credentials, and complete a one-time setup for your environment.

## Key terms

| Term | Description |
|---|---|
| Purchase protection | The Fraud Protection module that analyzes purchases for fraud, based on risk levels that the merchant determines. |
| Storefront | The out-of-box e-commerce storefront that is provided with Commerce. |
| Azure Data Lake Storage Gen2 | Data Lake Storage Gen2 is used to make Commerce data available for processing by the **Loss prevention** module. |

## Purchase protection in Commerce

### Purchase protection overview

The first generally available offering from Fraud Protection is a purchase protection module. Merchants use this module to sign in to the Fraud Protection dashboard for their organization and define fraud rules for online purchases. Based on the settings that a merchant configures in Fraud Protection, e-commerce transactions can be validated by using Fraud Protection before sending them for payment authorization.

When you send an order to the Fraud Protection purchase protection module, Fraud Protection analyzes the purchase and provides a risk assessment. It bases this assessment on merchant-defined fraud rules, insights that are driven by artificial intelligence (AI), and consortium-based fraud analytics. If the fraud score that Fraud Protection returns for the order exceeds the merchant's risk tolerance, Fraud Protection instructs the storefront to reject the order. If an order isn't rejected, Fraud Protection returns a fraud score that the storefront can use to determine the next steps in the order fulfillment process. Those steps might include putting the order on hold for manual review or follow-up with the customer who placed the order.


### Supported capabilities in the purchase protection integration

#### Purchase events

Purchase protection integration with Dynamics 365 Commerce supports the receipt of Fraud Protection risk assessments and termination of orders in the online storefront.

Here's the flow for purchase events:

1. A storefront customer adds items to the basket and proceeds to checkout.
1. The customer enters shipping and payment details.
1. After the prerequisites are completed, the customer selects **Place order**.
1. Order details are sent to Fraud Protection for purchase protection assessment.
1. If the merchant rules that are defined in Fraud Protection determine that the order should be rejected, a response is sent to the storefront, and the order is terminated.

If Fraud Protection purchase protection causes an order to be terminated, the user receives the following error message: "The order can't be processed at this time. Please try again later."

:::image type="content" source="../media/Payments/SampleDFPReject.png" alt-text="Screenshot of a rejected order example from a reference storefront.":::

Alternatively, if the merchant rules determine that the order should be approved, the response that is sent to the storefront includes the fraud score and the reason code that Fraud Protection determined. For the initial integration, the Fraud Protection assessment isn't used in any way, and the response for both approval and rejection scenarios isn't saved.

Rejected orders aren't sent to payment processors for authorization, and they don't go through the order creation process in the headquarters.

#### Bank events

If an online order is approved based on the Fraud Protection assessment, the next step is to authorize payments for that order, if payment authorizations are applicable. Once the order is authorized by using the payment processor, Fraud Protection is notified of the authorization result. Sending these results to Fraud Protection trains the advanced AI to better predict future authorization results, and boosts the quality of future Fraud Protection assessments.

#### Purchase status events

Purchase status events resemble bank events. After an order is created in the Commerce headquarters, a signal is sent to Fraud Protection to indicate that the order was successfully created. Both bank events and purchase status events are informational events. Therefore, no response is expected from Fraud Protection.

### Setup

After the merchant's Fraud Protection environment is available and purchase protection settings are configured, continue the setup in Commerce headquarters. If the environment isn't configured yet, sign in to the [Fraud Protection portal](https://dfp.microsoft.com/) with tenant administrator credentials to complete the configuration.

#### Key Vault setup

The integration setup requires a secret when Commerce communicates with Fraud Protection to get a purchase protection result. Store that secret by using an Azure Key Vault client. For information about how to set up a Key Vault client, see [Setting up Azure Key Vault Client](https://support.microsoft.com/help/4040305/setting-up-azure-key-vault-client).

The Fraud Protection certificate that you store in Key Vault can be referenced only if you reference it by using Key Vault parameters in the Commerce headquarters. To set up Key Vault parameters, go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Key Vault parameters** in Commerce.

Next, select the Key Vault URL that you use to store the Fraud Protection secret, and select **Add**. Then specify the name, description, and path of the Key Vault secret that authenticates Commerce when it sends orders for purchase protection assessment.

#### Commerce parameters setup

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**.
1. On the **Dynamics Fraud Protection** tab, set the **Enable Dynamics Fraud Protection integration** option to **Yes**.
1. On the **Configuration** FastTab, add the Microsoft Entra client ID, and then select the name of the Key Vault secret that you configured earlier.

    By default, the **Assessment type** field is set to **Evaluate**. In this case, Fraud Protection passively checks orders for fraud but doesn't actively reject orders. Therefore, merchants can compare Fraud Protection risk assessments with their current fraud tools to understand the impact of Fraud Protection on acceptance rates.

    Alternatively, set the **Assessment type** field to **Protect**. In this case, Fraud Protection returns "Reject" assessments, and fraudulent orders are terminated before they're sent for authorization or created in Commerce headquarters.

1. Set the **Dynamics Fraud Protection endpoint URL** field. Fraud Protection provides this URL, and it varies across user acceptance testing (UAT) and production environments.

## Loss prevention in Commerce

The **Loss prevention** capability in Fraud Protection is generally available in the third quarter (Q3) of 2020. The out-of-box integration for loss prevention is available in Commerce version 10.0.12.

### Loss prevention overview

Fraud that arises from abuse of return and discount policies is a top source of shrinkage for retailers. Existing physical deterrents are easy to work around. Therefore, to catch the most sophisticated forms of abuse, it's critical that retailers use artificial intelligence (AI) to identify loss.

The **Loss prevention** module in Fraud Protection analyzes in-store returns and discounts to identify anomalies that might be caused by abuse of return and discount policies. By using AI, the **Loss prevention** module can identify patterns and anomalies that indicate potential fraud, and can uncover hard-to-detect sources of shrinkage.

The **Loss prevention** module analyzes Commerce data that's available through Data Lake Storage Gen2. This integration is an opt-in integration and isn't turned on by default.

After **Loss prevention** finishes analyzing the data, the results are displayed on a [Fraud Protection](https://go.microsoft.com/fwlink/?linkid=2131023) dashboard. From there, users can evaluate the results and observe trends that might indicate potential fraud.

### Turning on the Loss prevention integration with Commerce

#### Set up Fraud Protection

To set up Fraud Protection, [request a callback](https://dynamics.microsoft.com/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative. When the merchant's Fraud Protection environment is available, and Loss prevention settings are configured, you can continue the setup by turning on Data Lake Storage Gen2 for the Commerce environment.  

#### Turn on Data Lake Storage Gen2 for your Commerce environment

Before the data can be available in Data Lake Storage Gen2, you must turn on the service for the Commerce environment. For information about how to turn on Data Lake Storage Gen2 for your Commerce environment, see [Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](../enable-adls-environment.md).

#### Turn on Loss prevention

Turn on the Loss prevention integration through the **Feature management** workspace in Commerce. The feature is named "Dynamics 365 Fraud Protection (DFP) Loss prevention." No other setup in Commerce is required to turn on the integration.

#### Configure Loss prevention to connect to Data Lake Storage Gen2

Connect Loss prevention to the Data Lake Storage Gen2 pool that is associated with the Commerce account.

## Privacy notice

When you turn on the feature, it shares some of your data with other Microsoft online services. This data includes information about payments, credit, returns, and transaction status, or personal data. Retail or Commerce online services don't store Fraud Protection purchase protection assessments.

Your privacy is important to Microsoft. For more information, see the [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Additional resources

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[Dynamics 365 payment data use](../payment-connector-data-fields.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
