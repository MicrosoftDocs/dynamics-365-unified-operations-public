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
| Card Present | When a payment terminal is implemented using the `INamedRequestHandler` interface, it is typically referred to as a "Card present" payment connector. The term card present is a way to describe such a payment connector due to the fact that is supports transactions where a physcical card is presented. |
| Card Not Present | Payment connectors implemented for use in the back office, call center, or used in e-Commerce integrations are implemented using the `IPaymentProcessor` interface and typically referred to as "Card not present" payment connectors. |

## Overview
This article covers the following sections to assist you to evaluate and setup the Dynamics 365 Payment Connector for Adyen: 

- **[Supported Features and Functionalities](#Supported-Features-and-Functionalities)** – This section describes the set of features and functionalities that the Dynamics 365 Payment Connector for Adyen supports).
- **[Sign Up with Adyen](#Sign-Up-with-Adyen)** – This section describes how to sign up for a merchant account with Adyen.
- **[Setup and Configuration](#Setup-and-Configuration)** – This section explains in detail how to setup and configure the Dynamics 365 Payment Connector for Adyen across the POS, Call Center, and E-Commerce channels.

## Supported Features, Functionalities, and Payment Terminals
The out of box payment connector uses the standard payments SDK. As such, the payment connector for Adyen does not have special capabilites which are not available for other payment connectors to utilize. 

### Dynamics Versions
The first party out of box Dynamics 365 Payment Connector for Adyen is supported in Microsoft Dynamics 365 for Finance and Operations or Retail 8.1.3 and above. However, other third party developed payment connectors for Adyen can still be developed for earlier versions of Dynamics 365. 

### Payment Terminals
The Dynamics 365 Payment Connector for Adyen leverages the [Adyen Payment Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api), which is device agnostic and supports all payment terminals supported by this API. Visit the [Adyen POS Terminals](https://www.adyen.com/pos-payments/terminals) page for a complete list of supported payment terminals.

### Input Methods

| Connector type | Dip | Swipe | Tap | Manual entry | 
| --- | --- | --- | --- | --- |
| Card present | ✔ | ✔ | ✔ | - |
| Card not present | - | - | - | ✔ |

### Payment Instruments

#### Debit and Credit Cards

| Brand | Variants | Supported | Card present | Card not present |
| --- | --- | --- | ---| --- |
| MasterCard | Credit | ✔ | ✔ | ✔ |
| MasterCard | Debit | ✔ | ✔ | ✔ |
| MasterCard | Alpha Bank Bonus | ✔ | ✔ | ✔ |
| MasterCard | Apple Pay | ✔ | ✔ | - |
| MasterCard | Samsung Pay | ✔ | ✔ | - |
| MasterCard | Maestro | ✔ | ✔ | ✔ |
| MasterCard | Maestro Samsung Pay | ✔ | - |
| MasterCard | Maestro UK | ✔ | ✔ | ✔ |
| VISA | Credit | ✔ | ✔ | ✔ |
| VISA | Debit | ✔ | ✔ | ✔ |
| VISA | Alpha Bank Bonus | ✔ | ✔ | ✔ |
| VISA | Android Pay | ✔ | ✔ | - |
| VISA | Apple Pay | ✔ | ✔ | - |
| VISA | Samsung Pay | ✔ | ✔ | - |
| VISA | VISA Checkout | ✔ | ✔ | ✔ |
| VISA | VISA Dankort | ✔ | ✔ | ✔ |
| VISA | VISA Hipotecario | ✔ | ✔ | ✔ |
| VISA | VISA Aravia Card | ✔ | ✔ | ✔ |
| AMEX | Credit | ✔ | ✔ | ✔ |
| AMEX | Debit | ✔ | ✔ | ✔ |
| AMEX | Android Pay | ✔ | ✔ | - |
| AMEX | Apple Pay | ✔ | ✔ | - |
| AMEX | Samsung Pay | ✔ | ✔ | - |
| AMEX | AMEX Commercial | ✔ | ✔ | ✔ |
| AMEX | AMEX Consumer | ✔ | ✔ | ✔ |
| AMEX | AMEX Corporate | ✔ | ✔ | ✔ |
| AMEX | AMEX Small Business | ✔ | ✔ | ✔ |
| Discover | Standard | ✔ | ✔ | ✔ |
| Discover | Android Pay | ✔ | ✔ | - |
| Discover | Apple Pay | ✔ | ✔ | - |
| Discover | Samsung Pay | ✔ | ✔ | - |
| Diners | Standard | ✔ | ✔ | ✔ |
| Dineromail | Standard | ✔ | ✔ | ✔ |
| JCB | Standard | ✔ | ✔ | ✔ |

#### Gift Cards

| Scheme | Card present | Card not present |
| --- | --- | --- |
| Givex | ✔ (8.1.3) | Future release |
| SVS | ✔ (8.1.3) | Future release |

To support these external gift card schemes through the payment connector, additional steps must be followed. Please refer to [external gift card setup documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/gift-card) for more information. 

#### Wallets

| Scheme | Card present | Card not present |
| --- | --- | --- |
| Alipay | Future release | - |
| WeChat | Future release | - |

#### Dynamics 365 Payment Features
The following list describes the set of Dynamics 365 payment features supported by the Dynamics 365 Payment Connector for Adyen. These capabilities utilize enhancements introduced in December of 2018 to the payment SDK, and some retail components, and are not exclusive to the Adyen connector. For more information about how to uptake these enhancements with a different payment connector, please refer to [payment connector extensiblity documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension)

| Scheme | Card present | Card not present |
| --- | --- | --- |
| Duplicate Payment Protection | ✔ (8.1.3) | - |
| Omni Channel Tokenization | ✔ (8.1.3) | ✔ (8.1.3) |
| Linked Refunds | Future release | Future release |

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

#### Setup Processor for New Credit Cards
In order to process any payments across POS terminals, Call Center, or E-Commerce a new default payment procesor has to be configured for new credit cards. The default payment prceossor can be configured using the following steps:

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
| **Gateway environment** | Adyen gateway environment to map to. Possible values are `Test` and `Live`. `Live` should only be used for production devices and transactions. | ✔ | ✔ | Live |
| **Optional Domain** | The domain to use when making payment requests to Adyen. | | | https://terminal-api-live.adyen.com/sync |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Password phrase** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Identifier** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Version** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | ✔ | 1 |
| **Cloud API Key** | Adyen cloud API key. This can be retrieved by following the instructions provided on the Adyen page on [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key). | ✔ | | *Long String* |
| **Supported Currencies** | The currencies that should be processed by the connector. Please note- in card present scnearios, additional currencies can supported by Adyen through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) once the transaction request is sent to the payment terminal. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. | | | SVS |

### POS Payment Terminal

#### Board and Configure Adyen Payment Terminal
> [!NOTE]
> These instructions assume that you have access to an Adyen Payment Terminal.

Navigate to the Adyen [Point of sale](https://docs.adyen.com/developers/point-of-sale) page and follow the instructions to board your specific Adyen terminal. Skip any steps that instruct you to download Adyen specific apps. As part of the onboarding note down the following details for each payment terminal (these are required for the [Configure Payment Terminal IP Address and EFT POS Register Number](#Configure-Payment-Terminal-IP-Address-and-EFT-POS-Register-Number) step below:

- Terminal's IP Address
- POIID

Once onboarded, navigate to the terminal you would like to configure on the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml) and retrieve the following details for each payment terminal (these are required to setup the [EFT Service](#EFT-Service) described below):

- Key identifier
- Key passphrase
- Key version

#### Setup Dynammics 365 POS Hardware Profile
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > POS profiles > Hardware profiles**.
2. Select the hardware profile for which you would like to add the Dynamics 365 Payment Connector for Adyen.

##### EFT Service
1. Under the **EFT Service** tab set the value for **EFT Service** to `Payment Connector`.
2. Under the **Connectors** sub-tab click the `+ New` button and select the **Dynamics 365 Payment Connector for Adyen** from the drop down and make sure the **Sequence Number** is lower than all other connectors.
3. Under the **Connector Properties** section set the following values and click the `Save` button in the top left corner once done:

| Field | Description | Required | Auto-Populated | Sample Value | 
| --- | --- | :-: | :-: | --- |
| **Assembly Name** | Name of the Dynamics 365 Payment Connector for Adyen assembly | ✔ | ✔ | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
| **Service Account ID** | Unique identifier for the setup of the merchant properties. The identifier is stamped on payment transactions and used to identify the merchant properties that should be used by downstream processes (i.e. invoicing). | ✔ | ✔ | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
| **Version** | Version of the Dynamics 365 Payment Connector for Adyen to use. At this point only version `V001` is supported. | ✔ | ✔ | V001 |
| **Gateway environment** | Adyen gateway environment to map to. Possible values are `Test` and `Live`. `Live` should only be used for production devices and transactions. | ✔ | ✔ | Live |
| **Optional Domain** | The domain to use when making payment requests to Adyen. | | | https://terminal-api-live.adyen.com/sync |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | Adyen Terminal API architecture to use. Possible values are `Local` or `Cloud`. In most cases when the Microsoft Dynamics 365 for Retail Modern POS is on the same network as the Adyen Payment Terminal the `Local` setting should be used. For additional information about the different Terminal API architectures please view the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | ✔ | ✔ | Local |
| **Local Password phrase** | Adyen key passphrase for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | keypassphrase123 |
| **Local Key Identifier** | Adyen key identifier for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | mykey |
| **Local Key Version** | Adyen key version for the terminal. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | 0 |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | ✔ | 1 |
| **Cloud API Key** | This field is only used for the Card Not Present Payment integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Supported Currencies** |The currencies that should be processed by the connector. This value should match the currency set up for the store in Dynamics 365 for Retail. Please note- in card present scnearios, additional currencies can supported by Adyen through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) once the transaction request is sent to the payment terminal. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. `SVS` or `GIVEX`. | | | SVS |

##### PIN pad
1. Under the **PIN pad** tab set the value for **PIN pad** to `Network` and the value for the **Device name** to `MicrosoftAdyenDeviceV001`.

#### Setup Dynamics 365 Register
> [!NOTE]
> These instructions assume that there is a dedicated mapping between a Point of Sale register and an Adyen terminal. For IIS based Hardware Station follow the same instructions on the `Hardware Stations` tab of the **Retail > Channels > Retail stores > All retail stores** page corresponding to the specific store you are setting up.

##### Configure Payment Terminal IP Address and EFT POS Register Number 
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > Registers**.
2. Select the register you would like to link to the Adyen terminal.
3. In the newly opened POS Registers form, in the **General** tab under the **EFT** section enter a unique number for the **EFT POS register number**. Note, the number must be exactly 4 digits ling and unique across all POS registers under the same Adyen merchant account ID.
4. In the same POS Registers form, in the **General** tab under the **PROFILES** section set the **Hardware profile** to the hardware profile configured above.
5. Save changes.
6. In the top menu select **REGISTER** and under the **HARDWARE** section click on `Configure IP addresses`.
7. In the newly opened IP address configuration form, under the **PIN pad** section enter the **IP address** for the terminal following this pattern and the values retrieved above when boarding the Adyen Terminal:
    - `https://<IP address>:8443/nexo/<POIID>` (e.g. `https://192.168.1.3:8443/nexo/MX925-123456789`).
  
#### Update Modern POS or IIS Hardware Station config
If you are packaging your own Modern POS using the Retail SDK then these steps have to be performed only once in the SDK code before the installer is packaged. Otherwise, these steps have to be performed after the standard Modern POS or IIS Hardware Station is installed.

1. Open the `dllhost.exe.config` (for Modern POS) or `web.config` (for IIS Hardware Station).
2. Update the `PreloadedConfiguration` section to switch from the legacy to the standard `PaymentDeviceAdapter` as shown below.
``` xml
<PreloadedComposition>
  <composition>
    <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.PaymentDeviceAdapter" />
    <!-- Switch from legacy to standard Payement Device Adapter.
    <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Legacy.PaymentDeviceAdapter" />
    -->
  </composition>
</PreloadedComposition>
```

### Call Center
In order to configure the Dynamics 365 Payment Connector for Adyen for Call Center payments follow the instructions described in the [Setup processor for new credit cards](#Setup-processor-for-new-credit-cards) section. 

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
| **Optional Domain** | The domain to use when making payment requests to Adyen. | | | https://terminal-api-live.adyen.com/sync |
| **Merchand account ID** | Unique Adyen Merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign Up with Adyen](#Sign-Up-with-Adyen). | ✔ | | MerchantIdenfier |
| **Terminal architecture** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Password phrase** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Identifier** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Key Version** | This field is only used for the POS Payment Terminal integration and should be left blank. | | ✔ | *Leave Blank.* |
| **Local Cryptor Version** | Adyen crypto version to use when interacting with the Adyen Gateway. Should be set to `1`. | ✔ | | 1 |
| **Cloud API Key** | Adyen cloud API key. This can be retrieved by following the instructions provided on the Adyen page on [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key). | ✔ | | *Long String* |
| **Supported Currencies** | The currencies that should be processed by the connector. | ✔ | ✔ | USD;EUR |
| **Supported Tender Types** | The tender types that should be processed by the connector. | ✔ | ✔ | Visa;MasterCard;Amex;Discover;Debit |
| **Gift card provider** | The gift card provider that the connector uses to process gift cards. `SVS` or `GIVEX` | | | SVS |

## Frequently Asked Questions

### Can I re-use my existing payment terminal with the Adyen connector?
No. Adyen payment terminals are injected with the Adyen software. As a result, existing payment terminals that are not pre-configured with Adyen cannot be re-used with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen Payment Terminal
Yes. The Dynamics 365 for Retail Modern POS requires a know IP address to communicate with the Adyen Payment Terminal. Although the IP address of the Adyen Payment Terminal can be changed in the Dynamics 365 for Retail client, there is significant overhead and potential business disruption in trying to keep up with changing IP addresses.

### Can I use my merchant bank?
Yes. Adyen can work with any merchant bank.  

## Troubleshooting Steps

### POS Payment Terminals

#### General Issues
For all general issues you should always consult the Modern POS or IIS Hardware Station Event Logs first. These can be found under the nodes in the Windows Event Log:
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-ModernPOS**
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-Hardware Station**

#### Failing Payment Transactions
When payment transactions fail to process through the Adyen Payment Terminal the corresponding error messages in the Dynamics 365 POS will contain a `PSP Reference` number. Provide this reference number when contacting Adyen support to assist with specific transactions.

## Common Issues

### POS Payment Terminals

#### EFT Terminal ID is Not Set
| Title | EFT Terminal ID is not Set |
| :-- | :-- |
| **Symptom** | Payment Authorization calls fail with a Hardware error. The Event log contains an error message that the `EFT Terminal ID` is not set. |
| **Root Cause** | This can happen when the `EFT POS Register Number` is not set on the Register or the IIS Hardware Station. This can also happen if the values are set but not properly synchronized to the POS terminal or when they are cached. |
| **Fix** | Follow the instructions on the [Setup Dynamics 365 Register](#Setup-Dynamics-365-Register) section of this document. Once done, run the `1070` and `1090` distribution schedules. If this does not resolve the issue, consider re-activating the Modern POS as the value for the `EFT POS Register Number` might potentially be cached and needs to be reset. | 

#### Modern POS or IIS Hardware Station config not updated
| Title | Config is not updated |
| :-- | :-- |
| **Symptom** | MPOS error: Sign in Error. The initialization data couldn't be loaded. |
| **Root Cause** | This can occur when the POS is redeployed, but the dllhost.config file has not been updated. |
| **Fix** | Follow the instructions on the [Update Modern POS or IIS Hardware Station config](#### Update Modern POS or IIS Hardware Station config) section of this document. Once complete, close the POS and end the dllhost.exe task through Detail tab in the Task Manager, then relaunch the MPOS. If using IIS hardware station, reset IIS. | 


## Related Articles
- **[Payments FAQ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/payments-retail)**
