---
# required metadata

title: Dynamics 365 Payment Connector for Adyen
description: This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
ms.date: 03/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen. It includes a comprehensive list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

## Key terms

| Term | Description |
|---|---|
| Payment connector | An extension that facilitates communication between Microsoft Dynamics 365 Commerce (and associated components) and a payment service. The connector that is described in this topic was implemented by using the standard payments software development kit (SDK). |
| Card present | Refers to payment transactions where a physical card is presented and used on a payment terminal connector to the Dynamics 365 Point of Sale. |
| Card not present | Refers to payment transactions where a physical card is not present, such as e-Commerce or Call Center scenarios. In these scenarios, the payment-related information is entered manually either on an e-Commerce website, a Call Center flow, or on the point-of-sale or payment terminal. |

## Overview

This topic includes the following main sections to help you evaluate and set up the Dynamics 365 Payment Connector for Adyen.

- Supported features, functionality, versions, and terminals – This section describes the set of features and functionalities that the Dynamics 365 Payment Connector for Adyen supports.
- Sign up with Adyen – This section explains how to sign up for a merchant account with Adyen.
- Setup and configuration – This section explains, in detail, how to set up and configure the Dynamics 365 Payment Connector for Adyen across the point of sale (POS), call center, and e-Commerce channels.

## Supported features, functionality, versions, and terminals

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors.

### Supported versions

#### Microsoft Dynamics 365 supported versions
The first-party out-of-box Dynamics 365 Payment Connector for Adyen is supported in Microsoft Dynamics 365 for Finance and Operations version 8.1.3 (January 2019) or later, and in Microsoft Dynamics 365 Retail version 8.1.3 or later. However, third parties can still develop other payment connectors for Adyen for earlier versions of Microsoft Dynamics 365.

#### Supported Adyen Firmware versions
The list below describes the minimum and maximum Adyen firmware versions that are supported for each version of the Microsoft Dynamics 365 Retail POS.

---

# [8.1.3](#tab/8-1-3)
### Dynamics 365 Retail POS version 8.1.3
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_35p15 | adyen_v1_35p15 |

# [10.0.8](#tab/10-0-8)
### Dynamics 365 Retail POS version 10.0.8
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_38p5 | adyen_v1_48p6 |
| | *Note: Validation testing has been performed on adyen_v1_56p5.  See the note below for more details.* |

# [10.0.9](#tab/10-0-9)
### Dynamics 365 Retail POS version 10.0.9
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_45p9 | adyen_v1_48p6 |

# [10.0.10](#tab/10-0-10)
### Dynamics 365 Retail POS version 10.0.10
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_45p9 | adyen_v1_51p7 |

# [10.0.11](#tab/10-0-11)
### Dynamics 365 Retail POS version 10.0.11
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_45p9 | adyen_v1_56p5 |

# [10.0.12](#tab/10-0-12)
### Dynamics 365 Retail POS version 10.0.12
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_48p7 | adyen_v1_56p5 |

# [10.0.13](#tab/10-0-13)
### Dynamics 365 Retail POS version 10.0.13
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_51p7 | adyen_v1_56p5 |

# [10.0.14](#tab/10-0-14)
### Dynamics 365 Retail POS version 10.0.14
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_56p5 | adyen_v1_56p9 |

# [10.0.15](#tab/10-0-15)
### Dynamics 365 Retail POS version 10.0.15
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_56p9 | adyen_v1_56p9 |

# [10.0.16](#tab/10-0-16)
### Dynamics 365 Retail POS version 10.0.16
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_56p9 | adyen_v1_56p9 |

# [10.0.17](#tab/10-0-17)
### Dynamics 365 Retail POS version 10.0.17
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_59p7 | adyen_v1_59p7 |

---

> [!NOTE]
> Adyen may release minor version updates after Microsoft has tested the major version. As long as a major version is supported, it's okay to have minor version updates within the same major version. These updates are normally very targeted fixes and don't meet the bar for full retesting, as long as the same major firmare version was previously tested. Updates shouldn't exceed the maximum Adyen firmware version listed in documentation. 
>
> Migrating from a Adyen firmware version earlier than version 53 to version 53 requires POS KB **4577957** for monthly updates of Commerce, versions 10.0.11 through 10.0.14. If one of those versions is in use and doesn't include the hotfix, post-upgrade of the payment terminal will only allow payments via NFC. Applying the hotfix to the POS resolves this issue. If the POS version is older than version 10.0.11, file a support request noting that a fix for KB **4577957** is required for an out of service MPOS.


### Supported payment terminals
The Dynamics 365 Payment Connector for Adyen takes advantage of the device-agnostic [Adyen Payment Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api). It supports all payment terminals that this application programming interface (API) supports. For a complete list of supported payment terminals, visit the [Adyen POS terminals](https://www.adyen.com/pos-payments/terminals) page.

### Supported payment instruments

#### Supported debit and credit cards

| Brand | Variant | Card present | e-Commerce | Call Center |
|---|---|:-:|:-:|:-:|
| MasterCard | Credit | ✔ | ✔ | ✔ |
| MasterCard | Debit | ✔ | ✔ | ✔ |
| MasterCard | Alpha Bank Bonus | ✔ | ✔ | ✔ |
| MasterCard | Apple Pay | ✔ |  |  |
| MasterCard | Samsung Pay | ✔ |  |  |
| MasterCard | Maestro | ✔ | ✔ | ✔ |
| MasterCard | Maestro Samsung Pay | ✔ |  |  |
| MasterCard | Maestro UK | ✔ | ✔ | ✔ |
| VISA | Credit | ✔ | ✔ | ✔ |
| VISA | Debit | ✔ | ✔ | ✔ |
| VISA | Alpha Bank Bonus | ✔ | ✔ | ✔ |
| VISA | Android Pay | ✔ |  |  |
| VISA | Apple Pay | ✔ |  |  |
| VISA | Samsung Pay | ✔ |  |  |
| VISA | VISA Checkout | ✔ | ✔ | ✔ |
| VISA | VISA Dankort | ✔ | ✔ | ✔ |
| VISA | VISA Hipotecario | ✔ | ✔ | ✔ |
| VISA | VISA Aravia Card | ✔ | ✔ | ✔ |
| AMEX | Credit | ✔ | ✔ | ✔ |
| AMEX | Debit | ✔ | ✔ | ✔ |
| AMEX | Android Pay | ✔ |  |  |
| AMEX | Apple Pay | ✔ |  |  |
| AMEX | Samsung Pay | ✔ |  |  |
| AMEX | AMEX Commercial | ✔ | ✔ | ✔ |
| AMEX | AMEX Consumer | ✔ | ✔ | ✔ |
| AMEX | AMEX Corporate | ✔ | ✔ | ✔ |
| AMEX | AMEX Small Business | ✔ | ✔ | ✔ |
| Discover | Standard | ✔ | ✔ | ✔ |
| Discover | Android Pay | ✔ |  |  |
| Discover | Apple Pay | ✔ |  |  |
| Discover | Samsung Pay | ✔ |  |  |
| Diners | Standard | ✔ | ✔ | ✔ |
| Dineromail | Standard | ✔ | ✔ | ✔ |
| JCB | Standard | ✔ | ✔ | ✔ |
| Union Pay\* | Standard | ✔ |  |  |
| Interac Debit\* | Standard | ✔ |  |  |

\*Interac and Union Pay recurring card tokens aren't provided by Adyen, so they can't be supported for card not present transactions.

#### Supported gift cards
| Scheme | Card present | Card not present |
|---|:-:|---|
| Givex | ✔ | ✔ |
| SVS | ✔ | ✔ |

To support these external gift card schemes through the Dynamics 365 Payment Connector for Adyen, you must complete additional steps. For more information, see [Support for external gift cards](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/gift-card).

#### Supported wallets

| Scheme | Card present | Card not present |
|---|---|---|
| Alipay | Support will be added in a future release. | No |
| WeChat | Support will be added in a future release. | No |

#### Supported card present input methods
| Input method | Supported | Notes |
|---|:-:|---|
| Dip | ✔ | |
| Swipe | ✔ | |
| Tap | ✔ | |
| Manual Entry through POS UI. |  | Not supported at this time |
| Manual Entry through Payment Terminal. | ✔ | Supports manual entry of credit, debit, and gift cards with pin entry. | 


#### Supported card present countries

The following countries have Commerce components available and card present support from Adyen. For current international availability of Commerce, visit the [International availability page](https://docs.microsoft.com/dynamics365/get-started/availability).

| Country | Supported |
| --- | :-: |
| Australia | ✔ |
| Austria | ✔ |
| Belgium | ✔ |
| Canada | ✔ |
| Czech Republic | ✔ |
| Denmark | ✔ |
| Estonia | ✔ |
| Finland | ✔ |
| France | ✔ |
| Germany | ✔ |
| Hong Kong SAR | ✔ |
| Hungary | ✔ |
| Iceland | ✔ |
| Ireland | ✔ |
| Italy | ✔ |
| Latvia | ✔ |
| Lithuania | ✔ |
| Malaysia | ✔ |
| Netherlands | ✔ |
| Norway | ✔ |
| Poland | ✔ |
| Singapore | ✔ |
| Switzerland | ✔ |
| Spain | ✔ |
| Sweden | ✔ |
| Switzerland | ✔ |
| United Kingdom | ✔ |
| United States | ✔ |
| Brazil | Future release |

#### Supported card not present countries

The following countries are supported by Adyen for card not present tranactions. [Contact Adyen](https://www.adyen.com/contact/sales) for details about support for a specific country. For current international availability of Commerce, visit the [International availability page](https://docs.microsoft.com/dynamics365/get-started/availability).

| Country | 
| --- | --- |
| Argentina |
| Armenia |
| Australia |
| Austria |
| Bahrain |
| Belgium |
| Brazil |
| Bulgaria |
| Canada |
| Chile |
| China |
| Colombia |
| Croatia |
| Cyprus |
| Czech Republic  |
| Denmark |
| Egypt |
| Estonia |
| Finland |
| France |
| Georgia |
| Germany |
| Gibraltar |
| Greece |
| Guernsey |
| Hong Kong SAR |
| Hungary |
| Iceland |
| India |
| Indonesia |
| Ireland |
| Isle of Man |
| Israel |
| Italy |
| Japan |
| Jersey |
| Korea |
| Kuwait |
| Latvia |
| Lithuania |
| Luxembourg |
| Malaysia |
| Malta |
| Mexico |
| Morocco |
| Netherlands |
| New Zealand |
| Norway |
| Peru |
| Poland |
| Portugal |
| Qatar |
| Romania |
| Saudi Arabia |
| Serbia |
| Singapore |
| Slovakia |
| Slovenia |
| South Africa |
| Spain |
| Sweden |
| Switzerland |
| Taiwan |
| Tanzania |
| Thailand |
| Turkey |
| United Arab Emirates (UAE) |
| United Kingdom |
| United States of America including Puerto Rico  |

#### Supported Dynamics 365 payment features
The following table shows the set of features that the Dynamics 365 Payment Connector for Adyen supports. These features use enhancements that were introduced in the payments SDK and some components in December 2018. They aren't exclusive to the Dynamics 365 Payment Connector for Adyen. For more information about how to uptake these enhancements for a different payment connector, see [Create an end-to-end payment integration for a payment terminal](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension).

| Scheme | Card present | Card not present |
|---|:-:|:-:|
| [Cash Out Gift Card Balance](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/gift-card-cash-out) | ✔ | |
| [Duplicate Payment Protection](https://docs.microsoft.com/dynamics365/unified-operations/retail/duplicate-payment-protection) | ✔ | |
| Omni Channel Tokenization | ✔ | ✔ |
| Linked Refunds | ✔<br>(Starting with 10.0.1) | ✔<br>(Starting with 10.0.1) |
| [Save online payments](../dev-itpro/adyen-connector-listPI.md) | | ✔<br>(Starting with 10.0.2) | 
| [External gift cards for call center and e-commerce](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/gift-card) | ✔<br>(Starting with 10.0.10) | 
| [SCA payment redirect](https://go.microsoft.com/fwlink/?linkid=2131175) | | ✔<br>(Starting with 10.0.12) |
| [Dedicated payment terminals and prompts for a printer and cash drawer](https://docs.microsoft.com/dynamics365/commerce/pos-multi-hws) | ✔<br>(Starting with 10.0.12) | |
| [SDK-level tipping support through the Adyen connector](tipping.md) | ✔<br>(Starting with 10.0.14) | |
| [Incremental capture for order invoicing](incremental-capture.md) |  | ✔<br>(Starting with 10.0.18) |


## Sign up with Adyen

To use the Dynamics 365 Payment Connector for Adyen, you must have a separate agreement with Adyen. To learn more about Adyen's services, or to create a test merchant account, visit the [Adyen website](https://www.adyen.com/signup).

## Setup and configuration

> [!NOTE]
> These instructions assume that you've already signed up for a merchant account with Adyen, and that you have access to the Adyen merchant dashboard.

### Prerequisites

The following prerequisites must be completed before payments can be configured in any channel.

#### Set up a processor for new credit cards

To process payments across point of sale (POS) terminals, a call center, or e-Commerce, you must configure a new default payment processor for new credit cards. Follow these steps to configure a default payment processor.

1. Sign in to Headquarters, and go to **Accounts receivable \> Payments setup \> Payment services**.
2. On the Action Pane, select **New**, and then, on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | Adyen Payment Service |
    | Payment connector | Select the payment connector to use for new credit card payments. | Dynamics 365 Payment Connector for Adyen |
    | Test mode | For the Adyen connector, in production and test environments you should set this field to **false**. | false |
    | Default processor for credit cards | Specify whether this payment processor should be the default processor that's used for new credit cards. | Yes |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a 0 (zero) amount. | Yes |

3. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. "V002" should be used for all new implementations, as it leverages a newer Adyen API for card not present payments and is required for [SCA support](https://go.microsoft.com/fwlink/?linkid=2131175).  | Yes | Yes | "V001"/"V002" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for Live environments and should be obtained by contacting Adyen. This is the unique identifier for your Live environment in the form **[random]-[company name]**. This is present as the prefix inside the API URLs under **Account > API URLs** in your company's Live account on the Adyen Customer Area portal. For additional details, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field must be set to **Cloud** for the `Payment service account`. | Yes | Yes | Cloud |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |
    | Terminal gift card entry | *POS Only* Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | *e-Commerce only* Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | *POS Only* Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | Required when "V002" is designated for the version. You can obtain this key by following the instructions on the [How to get an origin key](https://docs.adyen.com/user-management/how-to-get-an-origin-key) page on the Adyen website. |

4. On the **Card verification value** tab, leave **Prompt for card verification value** and **Allow blank card verification value** set to **No**. 


### POS payment terminal

#### Onboard and configure an Adyen payment terminal

> [!NOTE]
> These instructions assume that you have access to an Adyen payment terminal.

Go to the [Point of sale](https://docs.adyen.com/developers/point-of-sale) page on the Adyen website, and follow the instructions to onboard your Adyen payment terminal. Skip any steps that instruct you to download Adyen-specific apps. During the onboarding process, make a note of the following information for each payment terminal. You will need this information in the [Configure the payment terminal IP address and EFT POS register number](#configure-the-payment-terminal-ip-address-and-eft-pos-register-number) section later in this topic.

- IP address of the payment terminal
- POIID (POIID is comprised of the serial number and model number of the device. It is used to uniquely identify the device.)

After the payment terminal is onboarded, sign in to the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml), go to the terminal that you want to configure, and make a note of the following information for each payment terminal. You will need this information in the [EFT service for local network communication](#eft-service-for-local-network-communication) section later in this topic.

- Key identifier
- Key passphrase
- Key version

#### Set up a Dynamics 365 POS hardware profile

1. Sign in to Headquarters, and go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
2. Select the hardware profile to add the Dynamics 365 Payment Connector for Adyen for.
3. Follow the steps in the [EFT service](#eft-service) and [PIN pad](#pin-pad) sections that follow.

#### EFT service

The Adyen payment connector can be configured to communicate with devices via the local network or through Adyen's cloud backend. For environments with unreliable internet service, or where offline mode is required, the **Local** setup should be used. For environments with strong internet connections, or if a static IP address can't be assigned to the payment terminal, the **Cloud** architecture may work best.

##### EFT service for local network communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
2. On the **Connectors** tab, select **New**, and then, in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Make sure that the value in the **Sequence number** field is lower than the value for all other connectors.
3. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V001** for EFT settings in the hardware profile. **V002** is required for call center and storefront only.  | Yes | Yes | "V001" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for Live environments and should be obtained by contacting Adyen. This is the unique identifier for your Live environment in the form **[random]-[company name]**. This is present as the prefix inside the API URLs under **Account > API URLs** in your company's Live account on the Adyen Customer Area portal. For additional details, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This must be set to **Local** for local communications. For more information about the different Terminal API architectures, see the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | Yes | Yes | Local |
    | Local Password phrase | Enter the Adyen key passphrase for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | keypassphrase123 |
    | Local Key Identifier | Enter the Adyen key identifier for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | mykey |
    | Local Key Version | Enter the Adyen key version for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | 0 |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |    
    | Terminal gift card entry | *POS Only* Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | *e-Commerce only* Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | *POS Only* Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | *Card not present only*  |

4. On the Action Pane, select **Save**.


##### EFT service for cloud communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
2. On the **Connectors** tab, select **New**, and then in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Make sure that the value in the **Sequence number** field is lower than the value for all other connectors.
3. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Autopopulated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V001** for EFT settings in the hardware profile. **V002** is required for call center and storefront only.  | Yes | Yes | "V001" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and should be obtained by contacting Adyen. This is the unique identifier for your live environment in the form **[random]-[company name]**. This is present as the prefix inside the API URLs under **Account > API URLs** in your company's live account on the Adyen Customer Area portal. For additional details, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This must be set to **Cloud** for cloud communication with the payment terminal. For more information about the different terminal API architectures, see the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | Yes | Yes | Cloud |
    | Local Password phrase | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Identifier | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Version | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Cryptor Version | This setting is used for local payment terminal communication only. You can leave the default as-is, set to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |    
    | Terminal gift card entry | *POS Only* Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | *e-Commerce only* Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | *POS Only* Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | *Card not present only* |

4. On the Action Pane, select **Save**.


##### PIN pad

1. On the **PIN pad** FastTab, in the **PIN pad** field, select **Network**.
2. In the **Device name** field, enter **MicrosoftAdyenDeviceV001**.

#### <a id="set-up-a-dynamics-365-register"></a>Set up a Dynamics 365 register

> [!NOTE]
> These instructions assume that there is a dedicated mapping between a POS register and an Adyen payment terminal. For a hardware station that is based on Microsoft Internet Information Services (IIS), go to **Retail and Commerce \> Channels \> Stores \> All stores**, and select the store that you're setting up. Then, on the page for that store, on the **Hardware Stations** FastTab, follow the same instructions.

Payment terminals may not be used by multiple hardware stations. If a payment terminal must be shared by multiple POS devices, an IIS hardware station must be deployed to manage communications with the payment terminal. 

##### Configure the payment terminal IP address and EFT POS register number

1. Sign in to Headquarters, and go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**.
2. Select the register to link to the Adyen payment terminal.
3. On the **POS Registers** page, on the **General** FastTab, in the **EFT** section, in the **EFT POS register number** field, enter a unique number. 
4. In the **Profiles** section, in the **Hardware profile** field, select the hardware profile that you configured earlier.
5. Save your changes.
6. On the Action Pane, on the **Register** tab, in the **Hardware** group, select **Configure IP addresses**.
7a. **If using the "Local" architecture:** On the **IP address configuration** page, on the **PIN pad** FastTab, in the **IP address** field, enter the IP address of the terminal in the following format: `https://<IP address>:8443/nexo/<POIID>`. Here, **\<IP address\>** and **\<POIID\>** are the values that you made a note of when you onboarded the Adyen payment terminal. Here is an example: `https://192.168.1.3:8443/nexo/MX925-123456789`. The values in this URL are case-sensitive.
7b. **If using the "Cloud" architecture:** On the **IP address configuration** page, on the **PIN pad** FastTab, in the **IP address** field, enter the **POIID** value that you made a note of when you onboarded the Adyen payment terminal. Here is an example: `MX925-123456789`. The values in this field are case-sensitive.
8. If the payment terminal includes an onboard printer and you want to print receipts from the processor using that printer, enter **123** in the **Port** field that is separate from the **IP address** field in the **PIN pad** FastTab.


#### <a id="update-the-modern-pos-or-iis-hardware-station-configuration"></a>Update the Modern POS or IIS Hardware Station configuration

If you're packaging your own version of Modern POS by using the Retail SDK, you must follow these steps only one time in the SDK code before the installer is packaged. Otherwise, you must follow these steps after the standard Modern POS or IIS Hardware Station is installed.

1. Open the **dllhost.exe.config** file (for Modern POS) or the **web.config** file (for IIS Hardware Station).
2. Update the **PreloadedComposition** section as shown here, to switch from the legacy payment device adapter to the standard payment device adapter.

    ``` xml
    <PreloadedComposition>
        <composition>
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.PaymentDeviceAdapter" />
            <!-- Switch from legacy to standard Payment Device Adapter.
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Legacy.PaymentDeviceAdapter" />
            -->
        </composition>
    </PreloadedComposition>
    ```
3. Update the **appSettings** variable **"PrintReceiptsOnCardDeclineOrVoid"** value to **True** to print decline or void responses from the processor. 

### Call center

To configure the Dynamics 365 Payment Connector for Adyen for call center payments, follow the instructions in the [Set up a processor for new credit cards](#set-up-a-processor-for-new-credit-cards) section earlier in this topic.

### e-Commerce

1. Sign in to Headquarters, and go to **Retail and Commerce \> Channels \> Online stores**.
2. Select the online store to add the Dynamics 365 Payment Connector for Adyen.
3. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
4. In the **Connectors** field, select **Dynamics 365 Payment Connector for Adyen**.
5. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. "V002" should be used for all new implementations, as it leverages a newer Adyen API for card not present payments and is required for [SCA support](https://go.microsoft.com/fwlink/?linkid=2131175).  | Yes | Yes | "V001"/"V002" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. This is the unique identifier for your Live environment in the form **[random]-[company name]**. This is present as the prefix inside the API URLs under **Account > API URLs** in your company's Live account on the Adyen Customer Area portal. For additional details, see, [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | No | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | *The full cloud API key* |
    | Supported Currencies | Enter the currencies that the connector should process. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. The possible values are **SVS** and **GIVEX**. | No | No | SVS |
    | Terminal gift card entry | *POS Only* Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | *e-Commerce only* Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | *POS Only* Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | *e-Commerce Only* Only required when "V002" is designated for the version. You can obtain this key by following the instructions on the [How to get an origin key](https://docs.adyen.com/user-management/how-to-get-an-origin-key) page on the Adyen website. |

6. On the Action Pane, select **Save**.

## Frequently asked questions

### Can I share a payment terminal with multiple hardware stations?

No. Payment terminals can only be used by a single hardware station or POS terminal. Attempting to connect multiple hardware stations to a single payment terminal will result in locking issues. If a payment terminal must be shared by multiple POS devices, an IIS hardware station must be deployed to manage the payment terminal. 

### Can I reuse my existing payment terminal with the Adyen connector?

No. Adyen payment terminals are injected with the Adyen software. Therefore, existing payment terminals that aren't preconfigured with Adyen can't be reused with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen payment terminal?

Yes. Modern POS requires a known IP address to communicate with the Adyen payment terminal. Although the IP address of the Adyen payment terminal can be changed in the client, attempts to keep up with changing IP addresses involve significant overhead and could cause business disruption.

### Can I use my merchant bank?

Yes. Adyen can work with any merchant bank.

## Troubleshooting

### POS payment terminals

#### General issues

For all general issues, you should always consult the Modern POS or IIS Hardware Station event logs first. You can find these logs found under the following nodes in the Microsoft Windows event log:

- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-ModernPOS
- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station

#### Failing payment transactions

When payment transactions aren't successfully processed through the Adyen payment terminal, the corresponding error messages in the Dynamics 365 POS will contain a PSP reference number(PSP is the reference ID provided by Adyen used to uniquely identify each transaction). Provide this reference number when you contact Adyen support for help with specific transactions.

## Common issues

### POS payment terminals

#### The EFT terminal ID isn't set

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>EFT Terminal ID is not set</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Payment authorization calls fail, and a hardware error occurs. An error message in the event log indicates that the <strong>EFT Terminal ID</strong> value isn't set.</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the <strong>EFT POS Register Number</strong> field isn't set on the register or the IIS Hardware Station. It can also occur if the value is set but isn't correctly synced to the POS terminal. Finally, it can also occur when the value is cached.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in the <a href="#set-up-a-dynamics-365-register">Set up a Dynamics 365 register</a> section earlier in this topic. Then run the <strong>1070</strong> and <strong>1090</strong> distribution schedules. If the issue isn't resolved, consider reactivating Modern POS, because the value of the <strong>EFT POS Register Number</strong> field might be cached and might need to be reset.</td>
</tr>
</tbody>
</table>

#### The Modern POS or IIS Hardware Station configuration isn't updated

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>Config is not updated</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Modern POS error: "Sign in Error. The initialization data couldn't be loaded."</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the POS is redeployed but the dllhost.config file hasn't been updated.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in the <a href="#update-the-modern-pos-or-iis-hardware-station-configuration">Update the Modern POS or IIS Hardware Station configuration</a> section earlier in this topic. Then end the dllhost.exe task on the <strong>Details</strong> tab in Task Manager, and reopen Modern POS. If you're using an IIS Hardware Station, reset IIS.</td>
</tr>
</tbody>
</table>

#### Invoicing sales orders failed due to stale authorization

| Title | Capture failed due to stale authorization |
|---|---|---|
| Symptom | Invoicing sales orders fails with "Exception has been thrown by the target of an invocation. System.ArgumentNullException: Value cannot be null." The underlying error in the logs is "The following error occurred during the capture call - Dynamics 365 Payment Connector for Adyen: Error code Decline message Capture failed due to stale authorization." |
| Root cause | This error happens when an authorization older than the **Authorization stale period (days)** is sent to the payment connector for capture. |
| Fix | Ensure the value of **Number of days before expired** in **Accounts receivable parameters, Credit Card** is set to **1 less day** than the value set in merchant properties for all channels and then retry invoicing. The recommended value for **Authorization stale period (days)** is 14 in Adyen merchant properties and 13 in Accounts receivables parameters. |

## Additional resources

[Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
