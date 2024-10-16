---
title: Contract lifecycle management integration overview (preview)
description: Contract lifecycle management integration overview.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Contract lifecycle management integration overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

*Contract lifecycle management* (CLM) is an important aspect of the source-to-pay process. It helps organizations manage their contracts with suppliers. CLM can help streamline contract creation, negotiation, execution, and renewal processes, reducing the time and resources required to manage contracts. CLM can help ensure that contracts are in compliance with organizational policies and regulations, reducing the risk of penalties or other negative consequences. CLM can also help improve visibility into contract performance, enabling organizations to make more informed decisions about their supplier relationships. By integrating CLM into the source-to-pay process, organizations can improve their overall supply chain performance and deliver greater value to their customers.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Microsoft Dynamics 365 Supply Chain Management provides built-in capabilities that help you operationalize contracts through purchase agreements, rebate agreements, brokerage agreements, and regular purchase orders. For organizations that would like to add more comprehensive contract lifecycle management, Supply Chain Management also provides a common integration framework that lets you integrate with an external CLM system. Integrating with an external CLM system lets you add support for many more advanced CLM processes, including contract creation, authoring, red lining, negotiating, signing, amending, and termination.

The CLM integration framework enables you to integrate CLM with Supply Chain Management, but isn't a CLM solution in itself. To take advantage of this feature, you must integrate it with an external CLM solution.

When you enabled and configured the integration with an external CLM solution, the following contract flows are enhanced in Supply Chain Management:

- **Purchase agreements** – The purchase agreement lifecycle can be managed seamlessly between the external CLM system and Supply Chain Management.
- **Non-disclosure agreements (NDAs)** – The NDA lifecycle is managed in the external CLM system and is accessible from within Supply Chain Management.

These two contract types (purchase agreement and NDA) represent two different kinds of integration. While purchase agreement contracts are deeply integrated with the purchase agreement source document and process in Supply Chain Management, NDA contracts represents a more light-weight and loosely coupled integration. In Supply Chain Management, NDA contracts only exist as records in **All contracts**. The NDA represents a supplier contract from an external CLM that doesn't directly impact any processes in Supply Chain Management.

The feature is extensible to allow for additional contract flows and types to be integrated if required.

## Next steps

- [Enable and configure CLM integration (preview)](developer/clm-enable.md)
- [Work with integrated CLM features (preview)](clm-use.md)
