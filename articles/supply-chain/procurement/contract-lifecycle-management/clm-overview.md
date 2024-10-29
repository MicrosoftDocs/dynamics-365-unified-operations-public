---
title: Contract lifecycle management integration overview (preview)
description: Get an overview of contract lifecycle management (CLM) integration.
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
<!-- KFM: Preview until 10.0.43 GA -->

*Contract lifecycle management* (CLM) helps organizations manage their contracts with suppliers. It's an important aspect of the source-to-pay process.

CLM helps streamline contract creation, negotiation, execution, and renewal processes. In this way, it reduces the time and resources that are required to manage contracts. In addition, CLM helps ensure that contracts comply with organizational policies and regulations. In this way, it reduces the risk of penalties and other negative consequences. CLM also helps improve visibility into contract performance. Therefore, organizations can make more informed decisions about their supplier relationships.

By integrating CLM into the source-to-pay process, organizations can improve their overall supply chain performance and deliver greater value to their customers.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Microsoft Dynamics 365 Supply Chain Management provides built-in capabilities that help you operationalize contracts through purchase agreements, rebate agreements, brokerage agreements, and regular purchase orders. However, to meet the needs of organizations that want more comprehensive CLM, Supply Chain Management also provides a common integration framework that lets you integrate with an external CLM system. By integrating with an external CLM system, you can add support for more advanced CLM processes, such as contract creation, authoring, redlining, negotiation, signing, amendment, and termination.

Although the CLM integration framework lets you integrate CLM with Supply Chain Management, it isn't a CLM solution. To take advantage of this feature, you must integrate it with an external CLM solution.

When you enable and configure the integration with an external CLM solution, the following contract flows are enhanced in Supply Chain Management:

- **Purchase agreements** – The purchase agreement lifecycle can be seamlessly managed between the external CLM system and Supply Chain Management.
- **Non-disclosure agreements (NDAs)** – The NDA lifecycle is managed in the external CLM system and accessible from Supply Chain Management.

The purchase agreement and NDA contract types represent two different types of integration. Purchase agreement contracts are deeply integrated with the purchase agreement source document and process in Supply Chain Management. By contrast, the integration of NDA contracts is looser and more lightweight. An NDA contract represents a supplier contract from an external CLM system that doesn't directly affect any processes in Supply Chain Management. In Supply Chain Management, NDA contracts exist only as records on the **All contracts** page.

The feature is extensible. Therefore, you can integrate more contract flows and types as you require.

## Next steps

- [Enable and configure CLM integration](developer/clm-enable.md)
- [Work with integrated CLM features](clm-use.md)
