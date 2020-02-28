---
# required metadata

title: Dynamics 365 Fraud Protection integration with Dynamics 365 Commerce
description: This topic describes out-of-box integrations that are available between Microsoft Dynamics 365 Fraud Protection and Dynamics 365 Commerce. 
author: rubendel
manager: AnnBe
ms.date: 01/06/2020 
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail, Commerce
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: 10.0.8

---

# Dynamics 365 Fraud Protection integration with Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]


This topic describes out-of-box integrations that are available between Microsoft Dynamics 365 Commerce and Dynamics 365 Fraud Protection.

## Key terms

| Term | Description |
|---|---|
| Purchase protection | The Fraud Protection module that analyzes purchases for fraud, based on risk levels that are determined by the merchant. |
| Storefront | The out-of-box e-commerce storefront that is provided with Commerce. |

## Overview

Fraud Protection is a service that offers fraud protection solutions to help retailers prevent fraudulent activity and identify places where fraud might be unnoticed. This topic describes out-of-box integrations between Fraud Protection and Commerce. It will be updated as new integrations between the two services are released in future releases. For more information about Fraud Protection, including information about modules that aren't yet supported by an out-of-box integration with Commerce, visit the [Fraud Protection landing page](https://dynamics.microsoft.com/ai/fraud-protection/). You can also [request a callback](https://dynamics.microsoft.com/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative to discuss how Fraud Protection can help boost profitability, reduce operational expenses, and improve customer experiences.

## Purchase protection in Commerce

### Purchase protection overview

The first generally available offering from Fraud Protection is a purchase protection module that lets merchants sign in to the Fraud Protection dashboard for their organization and define fraud rules for online purchases. Based on the settings that a merchant configures in Fraud Protection, e-commerce transactions can be validated with Fraud Protection before they are sent for payment authorization.

When an order is sent to the Fraud Protection purchase protection module, Fraud Protection analyzes the purchase and provides a risk assessment, based on merchant-defined fraud rules, insights that are driven by artificial intelligence (AI), and consortium-based fraud analytics. If the fraud score that is returned for the order exceeds the merchant's risk tolerance, Fraud Protection instructs the storefront to reject the order. If an order isn't rejected, Fraud Protection returns a fraud score that the storefront can use to determine the next steps in the order fulfillment process. Those steps might include putting the order on hold for manual review or follow-up with the customer who placed the order.

### Supported capabilities in the purchase protection integration

#### Purchase events

Currently, Commerce is in public preview. However, when it becomes generally available, the purchase protection integration will support the receipt of Fraud Protection risk assessments and termination of orders in the online storefront.

Here is the flow for purchase events.

1. A storefront customer adds items to the basket and proceeds to checkout.
2. The customer enters shipping and payment details.
3. After the prerequisites are completed, the customer selects **Place order**.
4. Order details are sent to Fraud Protection for purchase protection assessment.
5. If the merchant rules that are defined in Fraud Protection determine that the order should be rejected, a response is sent to the storefront, and the order is terminated.

If Fraud Protection purchase protection causes an order to be terminated, the user receives the following error message: "The order cannot be processed at this time. Please try again later."

![Example of a rejected order from a reference storefront](../media/Payments/SampleDFPReject.png)

Alternatively, if the merchant rules determine that the order should be approved, the response that is sent to the storefront includes the fraud score and the reason code that were determined by Fraud Protection. For the initial integration, the Fraud Protection assessment isn't used in any way, and the response for both approval and rejection scenarios isn't saved.

Rejected orders aren't sent to payment processors for authorization, and they don't go through the order creation process in the back office.

#### Bank events

If an online order is approved based on the Fraud Protection assessment, the next step is to authorize payments for that order, if payment authorizations are applicable. Once the order is authorized with the payment processor, Fraud Protection is notified of the authorization result. By sending these results to Fraud Protection, the advanced AI can be trained to better predict future authorization results, thereby boosting the quality of future Fraud Protection assessments.

#### Purchase status events

Purchase status events resemble bank events. After an order is created in the Commerce back office, a signal is sent to Fraud Protection to indicate that the order was successfully created. Both bank events and purchase status events are informational events. Therefore, no response is expected from Fraud Protection.

### Availability

As of Dynamics 365 Retail version 10.0.8, Retail includes the back-office setup for Fraud Protection integration. However, the full out-of-box integration requires the storefront that is included in Commerce, and Commerce is currently in public preview. When Commerce becomes generally available, existing Retail customers will be able to update to it. For more information, visit the [Dynamics 365 Commerce landing page](https://dynamics.microsoft.com/commerce/overview/).

#### Setup

The out-of-box purchase protection integration requires a Fraud Protection environment. To set up Fraud Protection, [request a callback](https://dynamics.microsoft.com/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative.

After the merchant's Fraud Protection environment is available, and purchase protection settings have been configured, the setup can continue in the Commerce back office.

##### Key Vault setup

The integration setup requires that a secret be used when Commerce communicates with Fraud Protection to get a purchase protection result. That secret must be stored by using an Azure Key Vault client. For information about how to set up a Key Vault client, see [Setting up Azure Key Vault Client](https://support.microsoft.com/help/4040305/setting-up-azure-key-vault-client).

The Fraud Protection certificate that is stored in Key Vault can be referenced only if it's referenced by Key Vault parameters in the Commerce back office. To set up Key Vault parameters, go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Key Vault parameters** in Commerce.

Next, select the Key Vault URL that is used to store the Fraud Protection secret, and select **Add**. Then specify the name, description, and path of the Key Vault secret that is used to authenticate Commerce when it sends orders for purchase protection assessment.

##### Retail parameters setup

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Retail parameters**.
2. On the **Dynamics Fraud Protection** tab, set the **Enable Dynamics Fraud Protection integration** option to **Yes**.
3. On the **Configuration** FastTab, add the Azure Active Directory (Azure AD) client ID, and then select the name of the Key Vault secret that you configured earlier.

    By default, the **Assessment type** field is set to **Evaluate**. In this case, Fraud Protection will passively check orders for fraud but won't actively reject orders. Therefore, merchants can compare Fraud Protection risk assessments with their current fraud tools to understand the impact of Fraud Protection on acceptance rates.

    Alternatively, the **Assessment type** field can be set to **Protect**. In this case, Fraud Protection will return "Reject" assessments, and fraudulent orders will be terminated before they are sent for authorization or created in the back office.

4. The **Dynamics Fraud Protection endpoint URL** field must be set. This URL is provided by Fraud Protection and will vary across user acceptance testing (UAT) and production environments.

![Fraud Protection setup in Retail parameters](../media/Payments/DFPSetupParams.png)

> [!NOTE]
> The Key Vault and Fraud Protection settings are company-specific. To enable Fraud Protection for production environments, you don't enter the Azure AD client ID through the user interface (UI). Instead, you must create and submit a [service request](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team). In the title of your request, clearly indicate that the request is to configure Fraud Protection purchase protection for a production Commerce or Retail environment.

## Privacy notice

When you enable this feature, some of your data is shared with other Microsoft online services. This data includes information about payments, credit, returns, and transaction status, or personal data. Fraud Protection purchase protection assessments aren't stored by the Retail or Commerce online services.

Your privacy is important to Microsoft. To learn more, read the [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 payment data use](https://docs.microsoft.com/dynamics365/retail/payment-connector-data-fields)
