---
title: Dimension data validation
description: Learn how to validate the data integrity of ledger account combinations and default dimension sets in Dynamics 365 Finance.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 03/02/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-10-01
ms.search.form: DimensionDataValidation
ms.dyn365.ops.version: 10.0.39
---

# Dimension data validation

[!include [banner](../includes/banner.md)]

Starting in version 10.0.39, you can validate whether a ledger account or default dimension combination is structurally valid using the **Dimension data validation** page at **General ledger** > **Chart of accounts** > **Dimensions** > **Dimension data validation**.

## Run a validation

Enter the following information and select **Run**:

- **Dimension type** – Select **Ledger dimension** to validate a ledger account combination, or **Default dimension** to validate a default dimension set.
- **Reference record ID** – The record ID of the record to validate. Ledger dimension IDs reference the **DimensionAttributeValueCombination** table; default dimension IDs reference the **DimensionAttributeValueSet** table. Record IDs can be found in dimension validation errors or by inspecting the backing data record.
- **Date** – The date to validate against, since dimension validity can vary based on active from/to dates and other setup.
- **Company** – The legal entity to use for validation, since some dimension combinations are only valid in a specific company.

[![Dimension data validation page.](./media/dimension-data-validation.png)](./media/dimension-data-validation.png)

The **Is valid** field shows whether the combination or set is valid. Select **Detailed results** to see the individual checks that were performed.

[![Dimension data validation detailed results.](./media/dimension-data-validation-detailed-results.png)](./media/dimension-data-validation-detailed-results.png)

## Validate from the UI

You can also trigger validation directly from any account or dimension field in the UI without navigating to the **Dimension data validation** page.

On a segmented entry control, right-click the account field and select **Validate data integrity**.

[![Validate data integrity option on a segmented entry control.](./media/dimension-data-validation-sec.png)](./media/dimension-data-validation-sec.png)

On a dimension entry control, select **Options** > **Validate data integrity**.

[![Validate data integrity option on a dimension entry control.](./media/dimension-data-validation-dec.png)](./media/dimension-data-validation-dec.png)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
