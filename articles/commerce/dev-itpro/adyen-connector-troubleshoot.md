---
title: Troubleshoot Dynamics 365 Payment Connector for Adyen
description: This article provides troubleshooting guidance for common issues related to the Microsoft Dynamics 365 Payment Connector for Adyen.
author: Reza-Assadi
ms.date: 01/09/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-01-01
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.custom: 
  - bap-template
---

# Troubleshoot Dynamics 365 Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This article provides troubleshooting guidance for common issues related to the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md).

## POS payment terminals

### General issues

For all general issues, you should always consult the Store Commerce app or Internet Information Services (IIS) Hardware Station event logs first. You can find these logs found under the following nodes in the Microsoft Windows event log:

- **Windows Logs \> Application \> Filter Current Log**</br>
(On the **Event sources** drop-down list, select **Microsoft Dynamics - Store Commerce**.)
- **Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station**

### Failing payment transactions

When payment transactions aren't successfully processed through the Adyen payment terminal, the corresponding error messages in the Dynamics 365 POS contain a payment service provider (PSP) reference ID. The PSP reference ID is provided by Adyen to identify each transaction. Provide this reference ID when you contact Adyen support for help with specific transactions.

### The EFT terminal ID isn't set

For troubleshooting guidance on this issue, see [EFT Terminal ID isn't set](/troubleshoot/dynamics-365/commerce/payments/adyen-connector#eft-terminal-id-isnt-set).

### Invoicing sales orders failed due to stale authorization

For troubleshooting guidance on this issue, see [Invoicing sales orders fails because of stale authorization](/troubleshoot/dynamics-365/commerce/payments/adyen-connector#invoicing-sales-orders-fails-because-of-stale-authorization).

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]


