---
title: Electronic reporting (ER) destination failure handling
description: Learn about failure handling of Electronic reporting destinations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/01/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
---

# Electronic reporting destination failure handling

[!include [banner](../includes/banner.md)]


Usually, you run an ER format within the scope of a specific business process. However, sometimes you need to consider the delivery of an outbound document that the ER format generates during execution as part of that business process. In this case, if delivery of a generated outbound document to a configured destination isn't successful, you must cancel execution of the business process. To configure the appropriate ER destination, select the **Stop processing on failure** option.

For example, you configure vendor payment processing so that the **ISO20022 Credit Transfer** ER format runs to generate the payment file and supplementary documents (such as the covering letter and control report). If a payment should be considered successfully processed only if the covering letter is successfully delivered by email, you must select the **Stop processing on failure** checkbox for the **CoveringLetter** component in the appropriate file destination, as shown in the following illustration. In this case, the status of the payment that you select for processing changes from **None** to **Sent** only when the covering letter that's generated is successfully accepted for delivery by an email provider that's configured in the Finance instance.

:::image type="content" source="./media/ER_Destinations-StopProcessingAtDestinationFailure.png" alt-text="Screenshot of configuring process handling for file destination failure.":::

If you clear the **Stop processing on failure** checkbox for the **CoveringLetter** component in the destination, a payment is considered successfully processed even if the covering letter isn't successfully delivered by email. The status of the payment changes from **None** to **Sent** even if the covering letter can't be sent because, for example, the email address of the recipient or sender is missing or incorrect.
