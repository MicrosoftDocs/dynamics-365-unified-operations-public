---
# required metadata

title: Dynamics 365 Payment Connector for Adyen overview
description: This article provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
ms.date: 08/01/2023
ms.topic: overview
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2019-01-01

---

# Dynamics 365 Payment Connector for Adyen overview

[!include [banner](../includes/banner.md)]

This article provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen and includes a comprehensive list of supported features and functionality. Related articles cover Adyen sign up, configuration of the connector, frequently asked questions, and troubleshooting guidance for some common issues.

## Key terms

| Term | Description |
|---|---|
| Payment connector | An extension that facilitates communication between Microsoft Dynamics 365 Commerce (and associated components) and a payment service. The connector that is described in this article was implemented by using the standard payments software development kit (SDK). |
| Card present | Refers to payment transactions where a physical card is presented and used on a payment terminal connector to the Dynamics 365 Point of Sale. |
| Card not present | Refers to payment transactions where a physical card isn't present, such as e-Commerce or Call Center scenarios. In these scenarios, the payment-related information is entered manually either on an e-Commerce website, a Call Center flow, or on the point-of-sale or payment terminal. |

## Supported features, functionality, versions, and terminals

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors.

### Supported versions

#### Microsoft Dynamics 365 supported versions
The first-party out-of-box Dynamics 365 Payment Connector for Adyen is supported in Microsoft Dynamics 365 Finance version 8.1.3 (January 2019) or later, and in Microsoft Dynamics 365 Retail version 8.1.3 or later. However, third parties can still develop other payment connectors for Adyen for earlier versions of Microsoft Dynamics 365.

#### Supported Adyen firmware versions

The list below describes the minimum and maximum Adyen firmware versions that are supported for each version of the Microsoft Dynamics 365 Retail POS. The same values below also represent the Commerce and Adyen firmware versions supported for Dynamics 365 Commerce Store Commerce.

---

# [10.0.30](#tab/10-0-30)
### Dynamics 365 Retail POS version 10.0.30
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_71p16 | adyen_v1_78p6 |

# [10.0.31](#tab/10-0-31)
### Dynamics 365 Retail POS version 10.0.31
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_78p6 | adyen_v1_84p1 |

# [10.0.32](#tab/10-0-32)
### Dynamics 365 Retail POS version 10.0.32
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_84p1 | adyen_v1_86p3 |

# [10.0.33](#tab/10-0-33)
### Dynamics 365 Retail POS version 10.0.33
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_86p3 | adyen_v1_88p3 |

# [10.0.34](#tab/10-0-34)
### Dynamics 365 Retail POS version 10.0.34
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_88p3 | adyen_v1_89p6 |

# [10.0.35](#tab/10-0-35)
### Dynamics 365 Retail POS version 10.0.35
| Minimum Adyen Firmware version | Maximum Adyen Firmware version |
| --- | --- |
| adyen_v1_89p6 | adyen_v1_91p2 |

---

> [!NOTE]
> - Adyen may release minor version updates after Microsoft has tested the major version. As long as a major version is supported, it's okay to have minor version updates within the same major version. These updates are normally very targeted fixes and don't meet the bar for full retesting, as long as the same major firmware version was previously tested. Updates shouldn't exceed the maximum Adyen firmware version listed in documentation. 
> - For Adyen firmware versions 59p7 through 62p9, the **gift card cash out** operation requests PIN entry twice in scenarios where the gift card is manually entered. This issue is not reproduced when the gift card is swiped. Adyen is investigating. 

### Supported payment terminals
The Dynamics 365 Payment Connector for Adyen takes advantage of the device-agnostic [Adyen Payment Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api). It supports all payment terminals that this application programming interface (API) supports. For a complete list of supported payment terminals, visit the [Adyen POS terminals](https://www.adyen.com/pos-payments/terminals) page.

The following video describes the capabilities of the Adyen Castles SE1 Android payment terminal.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE5bKeM]

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

To support these external gift card schemes through the Dynamics 365 Payment Connector for Adyen, you must complete additional steps. For more information, see [Support for external gift cards](/dynamics365/unified-operations/retail/dev-itpro/gift-card).

#### Digital Wallet Support Status
The following are popular digital wallets and status of current support for those wallets by the Dynamics 365 Commerce payment connectors for Adyen. **Card present** relates to POS transactions, and **Card not present** relates to Call Center and Online channel transactions. 

| Scheme | Card present | Card not present |
|---|---|---|
| PayPal (via Adyen Connector) | No | No |
| Google Pay | Yes | Yes |
| Apple Pay | Yes | Yes |
| Klarna | No | No |
| Affirm | No | No |
| Afterpay | No | No |
| Alipay | No | No |
| WeChat | No | No |


#### Supported card present input methods
| Input method | Supported | Notes |
|---|:-:|---|
| Dip | ✔ | |
| Swipe | ✔ | |
| Tap | ✔ | |
| Manual Entry through POS UI. |  | Not supported at this time |
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
| Japan | Future release |
| Latvia | ✔ |
| Lithuania | ✔ |
| Malaysia | ✔ |
| Netherlands | ✔ |
| New Zealand | ✔ |
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

#### Supported card not present countries/regions

The following countries/regions are supported by Adyen for card not present transactions. [Contact Adyen](https://www.adyen.com/contact/sales) for details about support for a specific country/region. For current international availability of Commerce, visit the [International availability page](/dynamics365/get-started/availability).

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
| Linked Refunds | ✔<br>(Starting with 10.0.1) | ✔<br>(Starting with 10.0.1) |
| [Save online payments](../dev-itpro/adyen-connector-listPI.md) | | ✔<br>(Starting with 10.0.2) | 
| [External gift cards for call center and e-commerce](./gift-card.md) | ✔<br>(Starting with 10.0.10) | 
| [SCA payment redirect](../adyen_redirect.md) | | ✔<br>(Starting with 10.0.12) |
| [Dedicated payment terminals and prompts for a printer and cash drawer](../pos-multi-hws.md) | ✔<br>(Starting with 10.0.12) | |
| [SDK-level tipping support through the Adyen connector](tipping.md) | ✔<br>(Starting with 10.0.14) | |
| [Incremental capture for order invoicing](incremental-capture.md) |  | ✔<br>(Starting with 10.0.18) |
| [Wallet Payments](../wallets.md) |  | ✔<br>(Starting with 10.0.20) |
| [Google Pay with Adyen](google-pay-adyen.md) |  | ✔<br>(Starting with 10.0.27) |

## Next steps

For information on signing up for and configuring the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen setup](adyen-connector-setup.md).

## Additional resources

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
