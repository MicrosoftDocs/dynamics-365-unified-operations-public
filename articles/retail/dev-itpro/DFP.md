---
# required metadata

title: Dynamics 365 Fraud Protection integration
description: This topic describes out of box integrations available for Dynamics 365 Fraud Protection   
author: rubendel
manager: AnnBe
ms.date: 11/27/2019 
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Operations, Retail, Commerce
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Fraud Protection integration for Commerce

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes out of box integrations between Dynamics 365 Commerce and Dynamics 365 Fraud Protection

## Key terms

| Term | Description |
|---|---|
| DFP | Abbreviation for Dynamics 365 Fraud Protection. |
| Purchase protection | The DFP module that analyzes purchases for fraud based on risk levels determined by the merchant. |
| Commerce | Microsoft Dynamics 365 Commerce. May also be referred to as Dynamics 365 for Retail or Retail.|
| Storefront | The e-commerce storefront provided out of box with Dynamics 365 Commerce. |

## Overview

Microsoft Dynamics 365 Fraud Protection is a service dedicated to offering fraud protection solutions to help retailers prevent fraudulent activity and identify where fraud may be going unnoticed. This article describes out of box integrations between Dynamics 365 Commerce and DFP. It will be updated as new integrations between the two services are shipped in future releases. For more information about DFP, including modules that aren't yet supported by an out of box integration with Commerce, please visit the Dynamics 365 Fraud Protection [landing page](https://dynamics.microsoft.com/en-us/ai/fraud-protection/). You many also [request a call back](https://dynamics.microsoft.com/en-us/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative to discuss how DFP can help boost profitability, reduce operational expenses, and improve customer experiences; 

## Purchase protection in Dynamics 365 Commerce

### Purchase protection overview

The first generally available offering from DFP is a purchase protection service. This offering allows merchants to log into the DFP dashboard for their organization and configure risk tolerance for online purchases. Using the risk profile created by the merchant, e-commerce transactions can then be checked against the merchant-generated profile. In addition, DFP provides a consortium based approach that uses AI-driven insights to constantly update e-commerce fraud metrics. When online orders are sent to the DFP purchase protection module for assessment, it analyzes the purchase based on the previous mentioned factors and returns a result. If a an order is deemed fraudlent, DFP will instruct the storefront to terminate the order. If an order is not rejected, DFP will send a fraud score that can be used by the storefront to determine the next steps in order fulfillment. Those steps might include placing the order on hold for manual review or follow-up with the customer who placed the order.

### Purchase protection integration supported capabilities

#### Purchase Event
Upon general availability of Commerce, the purchase protection integration will support receiving a DFP risk assessment and terminating the order in the online Storefront. 

The flow for such an event is as follows:

1. Storefront customer adds items to the basket and proceeds to checkout.
2. Customer fills in shipping and payment details.
3. Upon completion of prerequisites, customer clicks 'Place order'.
4. Order details are sent to DFP for purchase protection assessment. 
5. If DFP determines the order should be rejected, a response is sent to the Storefront and the order is terminated.

When an order is terminated as a result of DFP purchase protection, the user simply sees an error stating: 

"The order cannot be processed at this time. Please try again later"


![Rejected order sample from a reference storefront](../dev-itpro/media/payments/SampleDFPReject.png)

Alternatively, if the order is deemed to be within the risk threshold configured by the merchant in the DFP portal, then the response from DFP to the Storefront includes the risk level determined by DFP. For the initial integration, that risk level is not used in any way and the response from DFP for both "Reject" and "Non-Reject" scenarios is not saved in any way. 

Rejected orders are not sent to payment processors for authorization and do not go through the order creation process in the back office. 

#### Bank Event

If an online order is allowed to proceed after DFP assessment the next step is to authorize payments for that order, if applicable. The result of those payment authorizations are referenced back to  Dynamics Fraud protection with a corretion ID for the Purchase Event previously assessed. By updating DFP with the results for prior Purchase vents, the data-driven AI insights can always be learning and improving its threat assessments. 

#### Purchase Status Event

Similar to Bank events, once an order is created in the Commerce back office, a signal is sent to DFP incidating that the order was created successfully. Both the Bank event and Purchase status event are "Fire and forget" events meaning there is no response expected from DFP. 

### Availability
As of 10.0.8, Dynamics for Retail includes the DFP integration back office setup. However, the full out of box integration requires requires the Storefront included in Dynamics 365 Commerce, which is currently in preview. After the 10.0.8 release, Dynamics 365 for Retail will be rebranded, thenceforth it will be known as Dynamics 365 Commerce. The key difference in the rebranding is that Commerce includes an out of box e-commerce storefront. Use of the storefront will be optional. For more details about Microsoft Dynamics 365 Commerce, visit the [landing page](https://dynamics.microsoft.com/en-us/commerce/overview/). 


#### Setup

Enabling the out of box purchase protection integration requires a DFP environment. To get set up with DFP, [request a call back](https://dynamics.microsoft.com/en-us/get-started/?appname=fraudprotection) from a Dynamics 365 sales representative.

Once the merchant's DFP environment is available and purchase protection risk tolerance has been configured, the setup can continue in the Commerce back office.

##### Key vault setup

Part of the integration setup requires that a secret is used when Commerce communicates with DFP to get a purchase protection result. That secret must be stored using an Azure Key Vault client. Details around setting up and Key Vault client can be found by visiting [this support topic](https://support.microsoft.com/en-us/help/4040305/setting-up-azure-key-vault-client). 

To reference the DFP certificate stored in Key Vault, that certificate must be referenced by key vault parameters in the Commerce back office.  To do so, navigate to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Key Vault parameters** in the Commerce back office.

Next, select the Key Vault URL used to store the DFP secret and click **Add**. Then specify the name, description, and path for Key Vault secret that is used to authenticate Commerce when it sends orders for purchase protection assessment. 

##### Retail parameters setup

Next navigate to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Retail parameters**. Then select the **Dynamics Fraud Protection** tab.

Set **Enable Dynamics Fraud Protection integration** to **Yes**. 

Next, expand the **Configuration** fasttab and add the Azure Active Directory (AAD) Client ID, then select the **Key Vault secret name** that was set up during Key Vault configuration. 

By default, the **Assessment type** will be set to **Evaluate**. When the integration is configured with assessment type in evaluate mode, DFP will passively check orders for fraud without actively rejecting those orders. This mode is provided for merchants to be able to compare DFP fraud assessments with third party fraud tools or to see if fraudlent transactions that are currently getting created would be prevented by using DFP. 

Alternatively, the **Protect** assessment type can be enabled. When **Protect** is enabled, DFP will return "Reject" assessments and fraudlent orders will be stopped before being sent for authorization or created in the back office. 

Finally, the **Dynamics Fraud Protection endpoint URL** must be specified. This URL is provided by DFP and will be different across UAT and Production environments. 

![DFP setup in Retail parameters](../media/DFPSetupParams.png)

> [!NOTE]
> The Key Vault and Dynamics Fraud Protection settings are company specific. When enabling DFP for production environments, the AAD Client ID is not entered through the user interface. Instead, enabling DFP for production environments requires a [serivce request](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team). When creating a support request to enable DFP for Production, clearly indicate in the title that the request is to configure DFP purchase protection for a production Commerce or Retail environment. 

## Privacy and Data

Enabling this integration results in sharing data, including personally identifiable information, with another Microsoft service. 

Customer instances of Dynamics 365 for Retail / Dynamics 365 Commerce and Dynamics 365 Fraud Protection may not be in the same data center. To learn more about where Microsoft stores data, visit the [Microsoft Privacy - Where is Your Data Located](https://www.microsoft.com/en-us/trust-center/privacy/data-location).

All data shared between DFP and Commerce is subject to the [Microsoft Privacy Policy](https://privacy.microsoft.com/en-US/). 

Microsoft Dynamics 365 Fraud Protection purchase protection assessments are not saved by Microsoft Dynamics 365 for Retail or Microsoft Dynamics 365 Commerce in any way and are only used to determine whether an online order should be allowed to proceed through checkout flows. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 payment data use](https://docs.microsoft.com/en-us/dynamics365/retail/payment-connector-data-fields)
