---
# required metadata

title: Dynamics 365 Payment Connector for Adyen FAQ
description: This topic provides answers to frequently asked questions regarding the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
ms.date: 07/29/2021
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

# Dynamics 365 Payment Connector for Adyen FAQ

[!include [banner](../includes/banner.md)]

This topic provides answers to frequently asked questions regarding the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md). 

### Can I share a payment terminal with multiple hardware stations?

No. Payment terminals can only be used by a single hardware station or POS terminal. Attempting to connect multiple hardware stations to a single payment terminal will result in locking issues. If a payment terminal must be shared by multiple POS devices, an IIS hardware station must be deployed to manage the payment terminal. 

### Can I reuse my existing payment terminal with the Adyen connector?

No. Adyen payment terminals are injected with the Adyen software. Therefore, existing payment terminals that aren't preconfigured with Adyen can't be reused with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen payment terminal?

Yes. Modern POS requires a known IP address to communicate with the Adyen payment terminal. Although the IP address of the Adyen payment terminal can be changed in the client, attempts to keep up with changing IP addresses involve significant overhead and could cause business disruption.

### Can I use my merchant bank?

Yes. Adyen can work with any merchant bank.

## Next steps

For guidance on troubleshooting common issues related to the Dynamics 365 Payment Connector for Adyen, see [Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md). 

## Additional resources

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
