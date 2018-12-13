---
# required metadata

title: Dynamics 365 Payment Connector for Adyen
description: Dynamics 365 Payment Connector for Adyen
author: rassadi
manager: AnnBe
ms.date: 07/22/2018
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
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2018-11-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for Adyen
This topic provides an overview of the Dynamics 365 Payment Connector for Adyen, including a comprehensive list of features and functionalities that are supported, a guide on how to setup and configure the connector, and common troubleshooting steps and common issues.

## Key terms
| Term | Description | 
| --- | --- |
| Payment Connector | An extension which facilitates communication between Dynamics 365 for Retail (and associated components) and a payment service. The connector described in this article was implemented using the standard payments SDK. 
| Card Present | When a payment terminal is implemented using the `INamedRequestHandler`, it is typically referred to as a "Card present" payment connector. The term card present is a way to describe such a payment connector due to the fact that is supports transactions where a physcical card is presented. |
| Card Not Present | Payment connectors implemented for use in the back office, call center, or used in e-Commerce integrations are implemented using the `IPaymentProcessor`, are typically referred to as "Card not present" payment connectors. |

## Overview
This article covers the following sections to assist you to evaluate and setup the Dynamics 365 Payment Connector for Adyen: 

- **[Supported Features and Functionalities](#Supported-Features-and-Functionalities)** – This section describes the set of features and functionalities that the Dynamics 365 Payment Connector for Adyen supports).
- **[Sign Up with Adyen](#Sign-Up-with-Adyen)** – This section describes how to sign up for a merchant account with Adyen.
- **[Setup and Configuration](#Setup-and-Configuration)** – This section explains in detail how to setup and configure the Dynamics 365 Payment Connector for Adyen across the POS, Call Center, and E-Commerce channels.

## Supported Features and Functionalities
The out of box payment connector uses the standard payments SDK. As such, the payment connector for Adyen does not have special capabilites which are not available for other payment connectors to utilize. 

Supported payment instrument types:
| Brand | Variants | Supported |
| --- | --- | --- |
| MasterCard | Standard | ✔ |
| - | Alpha Bank Bonus | ✔ |
| - | Apple Pay | ✔ |
| - | Samsung Pay | ✔ |
| VISA | Standard | ✔ |
| - | Alpha Bank Bonus | ✔ |
| - | Android Pay | ✔ |
| - | Apple Pay | ✔ |
| - | Samsung Pay | ✔ |
| - | VISA Checkout | ✔ |
| - | VISA Dankort | ✔ |
| - | VISA Hipotecario | ✔ |
| - | VISA Aravia Card | ✔ |
| AMEX | Android Pay | ✔ |
| - | Android Pay | ✔ |
| - | Apple Pay | ✔ |
| - | Samsung Pay | ✔ |
| - | AMEX Commercial | ✔ |
| - | AMEX Consumer | ✔ |
| - | AMEX Corporate | ✔ |
| - | AMEX Small Business | ✔ |


### Dynamics 365 Payment Features- Standard capabilities
 

### Dynamics 365 Payment Features- SDK enhancements
The following list describes the set of Dynamics 365 payment features supported by the Dynamics 365 Payment Connector for Adyen. These capabilities utilize enhancements introduced in December of 2018 to the payment SDK, and some retail components, and are not exclusive to the Adyen connector. For more information about how to uptake these enhancements with a different payment connector, please refer to [payment connector extensiblity documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension)

| Feature | Descrition | Supported | 
| --- | --- | :-: |
| **Duplicate Payment Protection** | Check to prevent duplicate payment scenarios in case the POS crashes and is unable to retrieve the signal from the payment terminal that the payment has been successfully processed. | ✔ |
| **Omni-channel tokenization** | Support for omni-channel payment scenarios, such as buy online and pick up in store using existing authorization and card tokens. | ✔ |
| **Refusal receipt printing** | Ability to print receipts when a payment is refused or cannot otherwise be completed successfully. | ✔ |

## Sign Up with Adyen
Use of the connector requires a separate agreement with Adyen. To learn more about their services or create a test merchant account that can be used for the Dynamics 365 Payment Connector for Adyen, navigate to Adyen's website by clicking [here](https://www.adyen.com/partners/dynamics).

If you would prefer to have Adyen contact you directly, send an email to partnerships@adyen.com. In the subject line of the email, include the term "Microsoft Dynamics connector". 
In the body of the email, be sure to include enough information to help them route the inquiry properly:
- Business name
- Nature of business (i.e. merchant or Microsoft partner)
- Business website
- Business address
- Contact name, title, email and phone
- Annual processing volume(Optional)
- Description of required services (i.e. e-Commerce only, e-Commerce and card present with 'X' number of payment terminals, etc.)


## Setup and Configuration
> [!NOTE]
> These instructions assume that you have already signed up for a Merchant Account with Adyen and have access to the Adyen merchant dashboard.

### Prerequisites
The following prerequisites need to be met for payments to be configured in any channel.

#### Setup processor for new credit cards
In order to process any payments across POS terminals, Call Center, or E-Commerce a newdefault payment procesor has to be configured for new credit cards. The default payment prceossor can be configured using the following steps:

1. Sign in to Retail headquarters and navigate to **Accounts receivable > Payments setup > Payment services**.
2. Click on `+ New` in the top navigate pane and fill out the following values in the **Setup** tab.

| Field | Description | Sample Value | 
| --- | --- | --- |
| **Payment service** | Name of the the payment service to configure. | Adyen Payment Service |
| **Payment connector** | The payment connector to use to for new credit card payments. | Dynamics 365 Payment Connector for Adyen |
| **Test mode** | Determines whether to run the connector in test mode. In production environments this value should be set to `false`. In test environments (e.g. Sandbox, Dev) this value should be set to `true`. | true |
| **Default processor for credit cards** | Determines whether this payment processor will be used as the processor should be used for new credit cards. | ✔ |
| **Bypass payment processor for zero transactions** | Determines whether this payment processor should be skipped for transactions with zero amount. | ✔ |

3. Once the Dynamics 365 Payment Connector for Adyen has been configured the following values must be set under the **Payment service account** tab.

| Field | Description | Required | Auto-Pupulated | Sample Value | 
| --- | --- | :-: | :-: | --- |
| **Assembly Name** | Name of the Dynamics 365 Payment Connector for Adyen assembly | ✔ | ✔ | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
| **Service Account ID** | Unique identifier for the setup of the merchant properties. The identifier is stamped on payment transactions and used to identify the merchant properties that should be used by downstream processes (i.e. invoicing). | ✔ | ✔ | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
| **Version** | Version of the Dynamics 365 Payment Connector for Adyen to use. At this point only version `V001` is supported. | ✔ | ✔ | V001 |
| **Gateway environment** | Adyen gateway environment to map to. Possible values are `Test` and `Live`. | ✔ | ✔ | Live |
| **Optional Domain** | TODO | | | TODO |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Password phrase** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Identifier** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Version** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | TODO | TODO |
| **Cloud API Key** | Adyen cloud API key. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | TODO |
| **Supported Currencies** | The currencies that should be processed by the connector. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. | | | TODO |

### Setup POS Payment Terminal

#### Board and Configure Adyen Payment Terminal
> [!NOTE]
> These instructions assume that you have access to an Adyen Payment Terminal.

Navigate to the Adyen [Point of sale](https://docs.adyen.com/developers/point-of-sale) page and follow the instructions to board your specific Adyen terminal. Skip any steps that instruct you to download Adyen specific apps. As part of the onboarding note down the following details for each payment terminal (these are required for the [Configure Payment Terminal IP Address and EFT POS Register Number](#Configure-Payment-Terminal-IP-Address-and-EFT-POS-Register-Number) step below:

- Terminal's IP Address
- POIID

Once onboarded, navigate to the terminal you would like to configure on the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml) and retrieve the following details for each payment termina (these are required to setup the [EFT Service](#EFT-Service) described below):

- Key identifier
- Key passphrase
- Key version

#### Setup Dynammics 365 POS Hardware Profile
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > PRO profiles > Hardware profiles**.
2. Select the hardware profile for which you would like to add the Dynamics 365 Payment Connector for Adyen.

##### EFT Service
1. Under the **EFT Service** tab set the value for **EFT Service** to `Payment Connector`.
2. Under the **Connectors** sub-tab click the `+ New` button and select the **Dynamics 365 Payment Connector for Adyen** from the drop down and make sure the **Sequence Number** is lower than all other connectors.
3. Under the **Connector Properties** section set the following values and click the `Save` button in the top left corner once done:

| Field | Description | Required | Auto-Pupulated | Sample Value | 
| --- | --- | :-: | :-: | --- |
| **Assembly Name** | Name of the Dynamics 365 Payment Connector for Adyen assembly | ✔ | ✔ | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
| **Service Account ID** | Unique identifier for the setup of the merchant properties. The identifier is stamped on payment transactions and used to identify the merchant properties that should be used by downstream processes (i.e. invoicing). | ✔ | ✔ | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
| **Version** | Version of the Dynamics 365 Payment Connector for Adyen to use. At this point only version `V001` is supported. | ✔ | ✔ | V001 |
| **Gateway environment** | Adyen gateway environment to map to. Possible values are `Test` and `Live`. | ✔ | ✔ | Live |
| **Optional Domain** | TODO | | | TODO |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | Adyen Terminal API architecture to use. Possible values are `Local` or `Cloud`. In most cases when the Microsoft Dynamics 365 for Retail Modern POS is on the same network as the Adyen Payment Terminal the `Local` setting should be used. For additional information about the different Terminal API architectures please view the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | ✔ | ✔ | Local |
| **Local Password phrase** | Adyen key passphrase for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | keypassphrase123 |
| **Local Key Identifier** | Adyen key identifier for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | mykey |
| **Local Key Version** | Adyen key version for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | 0 |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | TODO | TODO |
| **Cloud API Key** | Adyen cloud API key. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | TODO |
| **Supported Currencies** | The currencies that should be processed by the connector. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. | | | TODO |

##### PIN pad
1. Under the **PIN pad** tab set the value for **PIN pad** to `Network` and the value for the **Device name** to `MicrosoftAdyenDeviceV001`.

#### Setup Dynamics 365 Register
> [!NOTE]
> These instructions assume that there is a dedicated mapping between a Point of Sale register and an Adyen terminal.

##### Configure Payment Terminal IP Address and EFT POS Register Number 
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > Registers**.
2. Select the register you would like to link to the Adyen terminal.
3. In the newly opened POS Registers form, in the **General** tab under the **EFT** section enter a unique number for the **EFT POS register number**. Note, the number must be exactly 4 digits ling and unique across all POS registers.
4. In the same POS Registers form, in the **General** tab under the **PROFILES** section set the **Hardware profile** to the hardware profile configured above.
5. In the top menu select **REGISTER** and under the **HARDWARE** section click on `Configure IP addresses`.
6. In the newly opened IP address configuration form, under the **PIN pad** section enter the **IP address** for the terminal following this pattern and the values retrieved above when boarding the Adyen Terminal:
  - `https://<IP address>:8443/nexo/<POIID>` (e.g. `https://192.168.1.3:8443/nexo/MX925-123456789`).

### Call Center
In order to configure the Dynamics 365 Payment Connector for Adyen for Call Center payments follow the instructions desceibed in the [Setup processor for new credit cards](#Setup-processor-for-new-credit-cards) section. 

### E-Commerce
1. Sign in to Retail headquarters and navigate to **Retail > Channels > Online stores**.
2. Select the online store for which you would like to add the Dynamics 365 Payment Connector for Adyen.
3. In the newly opened Online Store form, expand the **Payment accounts** tab, click the `+ New` button and select the **Dynamics 365 Payment Connector for Adyen** from on the **Connector** field.
4. Once the connector is selected, set the following additional values and click the `Save` button in the top left corner once done:

| Field | Description | Required | Auto-Pupulated | Sample Value | 
| --- | --- | :-: | :-: | --- |
| **Assembly Name** | Name of the Dynamics 365 Payment Connector for Adyen assembly | ✔ | ✔ | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
| **Service Account ID** | Unique identifier for the setup of the merchant properties. The identifier is stamped on payment transactions and used to identify the merchant properties that should be used by downstream processes (i.e. invoicing). | ✔ | ✔ | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
| **Version** | Version of the Dynamics 365 Payment Connector for Adyen to use. At this point only version `V001` is supported. | ✔ | ✔ | V001 |
| **Gateway environment** | Adyen gateway environment to map to. Possible values are `Test` and `Live`. | ✔ | ✔ | Live |
| **Optional Domain** | TODO | | | TODO |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Password phrase** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Identifier** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Version** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | TODO | TODO |
| **Cloud API Key** | Adyen cloud API key. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | TODO | TODO |
| **Supported Currencies** | The currencies that should be processed by the connector. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. | | | TODO |

## Troubleshooting Steps

## Common Issues

## Related Articles
- **[Payments FAQ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
