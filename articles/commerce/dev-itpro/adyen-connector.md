---
title: Dynamics 365 Payment Connector for Adyen overview
description: This article provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
ms.date: 08/05/2025
ms.topic: overview
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.custom: 
  - bap-template
---

# Dynamics 365 Payment Connector for Adyen overview

[!include [banner](../includes/banner.md)]

This article provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen and includes a comprehensive list of supported features and functionality. Related articles cover Adyen sign up, configuration of the connector, frequently asked questions, and troubleshooting guidance for some common issues.

## Key terms

| Term | Description |
|---|---|
| Payment connector | An extension that facilitates communication between Microsoft Dynamics 365 Commerce (and associated components) and a payment service. The connector that is described in this article was implemented by using the standard payments software development kit (SDK). |
| Card present | Refers to payment transactions where a physical card is presented and used on a payment terminal connector to the Dynamics 365 Point of Sale. |
| Card not present | Refers to payment transactions where a physical card isn't present, such as Commerce or Call Center scenarios. In these scenarios, the payment-related information is entered manually either on a Commerce website, a Call Center flow, or on the point-of-sale or payment terminal. |

## Supported features, functionality, versions, and terminals

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors.

### Supported versions

#### Microsoft Dynamics 365 supported versions
The first-party out-of-box Dynamics 365 Payment Connector for Adyen is supported in Microsoft Dynamics 365 Finance version 8.1.3 (January 2019) or later, and in Microsoft Dynamics 365 Retail version 8.1.3 or later. However, third parties can still develop other payment connectors for Adyen for earlier versions of Microsoft Dynamics 365.

#### Supported Adyen firmware versions

The following list describes the minimum and maximum Adyen firmware versions that are supported for each version of the Microsoft Dynamics 365 Retail point of sale (POS). The same values also represent the Commerce and Adyen firmware versions supported for Dynamics 365 Commerce Store Commerce.

---



# [10.0.39](#tab/10-0-39)
### Dynamics 365 Retail POS version 10.0.39
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_96p0 | adyen_v1_99p6 |

# [10.0.40](#tab/10-0-40)
### Dynamics 365 Retail POS version 10.0.40
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_99p6 | adyen_v1_105p9 |

# [10.0.41](#tab/10-0-41)
### Dynamics 365 Retail POS version 10.0.41
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_105p9 | adyen_v1_109 |

# [10.0.42](#tab/10-0-42)
### Dynamics 365 Retail POS version 10.0.42
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_109 | adyen_v1_109 |

# [10.0.43](#tab/10-0-43)
### Dynamics 365 Retail POS version 10.0.43
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_109 | adyen_v1_115 |

# [10.0.44](#tab/10-0-44)
### Dynamics 365 Retail POS version 10.0.44
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_114 | adyen_v1_117 |

# [10.0.45](#tab/10-0-45)
### Dynamics 365 Retail POS version 10.0.45
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_117 | adyen_v1_120 |

---

> [!NOTE]
> Adyen may release minor version updates after Microsoft tests the major version. As long as a major version is supported, it's acceptable to have minor version updates within the same major version. These updates are normally targeted fixes and don't meet the bar for full retesting as long as the same major firmware version was previously tested. Updates shouldn't exceed the maximum Adyen firmware version listed in the documentation. 

### Supported payment terminals
The Dynamics 365 Payment Connector for Adyen takes advantage of the device-agnostic [Adyen Terminal API](https://www.adyen.com/knowledge-hub/introducing-the-terminal-api). It supports all payment terminals that this application programming interface (API) supports. For a complete list of Adyen payment terminals, see [Adyen POS terminals](https://www.adyen.com/pos-payments/terminals).

> [!NOTE]
> Microsoft recommends that you use payment card industry (PCI) approved payment terminals that are PIN Transaction Security Point of Interaction (PTS POI) devices. For a list of approved devices for Adyen, see [PCI PTS POI devices](https://listings.pcisecuritystandards.org/assessors_and_solutions/point_to_point_encryption_solutions?agree=true)

The following video describes the capabilities of the Adyen Castles SE1 Android payment terminal.


> [!VIDEO https://learn-video.azurefd.net/vod/player?id=748efff6-7d33-4378-a273-b6f97938f461]

### Supported payment instruments

#### Supported debit and credit cards

| Brand | Variant | Card present | Commerce | Call Center |
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
| Japan Credit Bureau (JCB) | Standard | ✔ | ✔ | ✔ |
| Union Pay\* | Standard | ✔ |  |  |
| Interac Debit\* | Standard | ✔ |  |  |

\*Interac and Union Pay recurring card tokens aren't provided by Adyen, so they can't be supported for card not present transactions.

#### Supported gift cards

| Scheme | Card present | Card not present |
|---|:-:|---|
| Givex | ✔ | ✔ |
| Stored Value Solutions (SVS) | ✔ | ✔ |

To support these external gift card schemes through the Dynamics 365 Payment Connector for Adyen, you must complete more steps. For more information, see [Support for external gift cards](/dynamics365/unified-operations/retail/dev-itpro/gift-card).

#### Digital wallet support status

The following table lists the current Dynamics 365 Commerce Payment Connector for Adyen support status of popular digital wallets. The "Card present support" column is for POS transactions, and the "Card not present support" column is for call center and online channel transactions. 

| Scheme | Card present support | Card not present support |
|---|---|---|
| PayPal (via Adyen Connector) | No | No |
| Google Pay | ✔ | ✔ |
| Apple Pay | ✔ | ✔ |
| Afterpay | No | No |
| Klarna | ✔ | No |
| Affirm | ✔ | No |
| Alipay | ✔ | No |
| WeChat Pay | ✔ | No |

> [!NOTE]
> In Commerce releases before version 10.0.45, to enable using digital wallets to place orders via POS and return those orders in call center, you must contact Microsoft to enable the **RetailPaymentCreateNonRecurringCreditCardFlight** flight. For information on setup and the known limitations for digital wallets, see [Wallet payment support](wallets.md).

#### Supported card present input methods

| Input method | Supported | Notes |
|---|:-:|---|
| Dip | ✔ | |
| Swipe | ✔ | |
| Tap | ✔ | |
| Manual Entry through POS UI. |  | Not supported for Adyen connector |
| Manual Entry through Payment Terminal. | ✔ | Supports manual entry of credit, debit, and gift cards with pin entry. | 


#### Supported card present countries/regions

The following countries/regions have Commerce components available and card present support from Adyen. For current international availability of Commerce, visit the [International availability page](/dynamics365/get-started/availability).

| Country/region | Supported |
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
| Japan | ✔ |
| Latvia | ✔ |
| Lithuania | ✔ |
| Malaysia | ✔ |
| Mexico | ✔ |
| Netherlands | ✔ |
| New Zealand | ✔ |
| Norway | ✔ |
| Poland | ✔ |
| Singapore | ✔ |
| Switzerland | ✔ |
| Spain | ✔ |
| Sweden | ✔ |
| Switzerland | ✔ |
|  United Arab Emirates (UAE) | ✔ |
| United Kingdom | ✔ |
| United States | ✔ |
| Brazil | ✔ |

#### Supported card not present countries/regions

Adyen supports the following countries/regions for card not present transactions. For details about support for a specific country/region, [contact Adyen](https://www.adyen.com/contact/sales). For information on the current international availability of Commerce, see [International availability page](/dynamics365/get-started/availability).

| Country/region | 
| --- |
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
| Türkiye |
| United Arab Emirates (UAE) |
| United Kingdom |
| United States of America including Puerto Rico  |

#### Supported Dynamics 365 payment features

The following table shows the set of features that the Dynamics 365 Payment Connector for Adyen supports. These features use enhancements that were introduced in the payments SDK and some components in December 2018. They aren't exclusive to the Dynamics 365 Payment Connector for Adyen. For more information about how to uptake these enhancements for a different payment connector, see [Create an end-to-end payment integration for a payment terminal](/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension).

| Scheme | Card present | Card not present |
|---|:-:|:-:|
| [Cash Out Gift Card Balance](/dynamics365/unified-operations/retail/dev-itpro/gift-card-cash-out) | ✔ | |
| [Duplicate Payment Protection](/dynamics365/unified-operations/retail/duplicate-payment-protection) | ✔ | |
| Omni Channel Tokenization | ✔ | ✔ |
| Linked Refunds | ✔<br> | ✔<br> |
| [Save online payments](../dev-itpro/adyen-connector-listPI.md) | | ✔<br> | 
| [External gift cards for call center and e-commerce](./gift-card.md) | ✔<br> | 
| [SCA payment redirect](../adyen_redirect.md) | | ✔<br> |
| [Dedicated payment terminals and prompts for a printer and cash drawer](../pos-multi-hws.md) | ✔<br> | |
| [SDK-level tipping support through the Adyen connector](tipping.md) | ✔<br> | |
| [Incremental capture for order invoicing](incremental-capture.md) |  | ✔<br> |
| [Wallet Payments](../wallets.md) |  | ✔<br> |
| [Google Pay with Adyen](google-pay-adyen.md) |  | ✔<br> |
| Adyen risk management for online payments |  | ✔<br>(Starting with 10.0.43) |

## Next steps

For information on signing up for and configuring the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen setup](adyen-connector-setup.md).

## Additional resources

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
