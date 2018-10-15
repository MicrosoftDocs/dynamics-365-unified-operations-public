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

## Related Articles

## Overview

## Supported Features and Functionalities

## Sign Up with Adyen

### Terminal Onboard
- key passphrase
- key identifier
- key version

## Setup and Configuration

### Pre-Requisites

### POS

#### POS Hardware Profile
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > PRO profiles > Hardware profiles**.
2. Select the hardware profile for which you would like to add the Dynamics 365 Payment Connector for Adyen.

##### EFT Service
1. Under the **EFT Service** tab set the value for **EFT Service** to `Payment Coonector`.
2. Under the **Connectors** sub-tab click the `+ New` button and select the **Dynamics 365 Payment Connector for Adyen** from the drop down and make sure the **Sequence Number** is lower than all other connectors.
3. Under the **Connector Properties** section set the following values.

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

#### Register
> [!NOTE]
> These instructions assume that there is a dedicated mapping between a Point of Sale register and an Adyen terminal.

##### Board Adyen terminal
Navigate to the Adyen [Point of sale](https://docs.adyen.com/developers/point-of-sale) page and follow the instructions to board your specific Adyen terminal. Skip any steps that instruct you to download Adyen specific apps. For each terminal retrieve the following details:

- Terminal's IP Address
- POIID

##### Configure IP Address
1. Sign in to Retail headquarters and navigate to **Retail > Channel setup > POS setup > Registers**.
2. Select the register you would like to link to the Adyen terminal.
3. In the newly opened POS Registers form, under the **PROFILES** tab **General** section set the **Hardware profile** to the hardware profile configured above.
4. In the top menu select **REGISTER** and under the **HARDWARE** section click on `Configure IP addresses`.
5. In the newly opened IP address configuration form, under the **PIN pad** section enter the **IP address** for the terminal following this pattern and the values retrieved above when boarding the Adyen Terminal:
  - `https://<IP address>:8443/nexo/<POIID>` (e.g. `https://192.168.1.3:8443/nexo/MX925-123456789`).

### Call Center

### E-Commerce

## Troubleshooting

## Common Issues
