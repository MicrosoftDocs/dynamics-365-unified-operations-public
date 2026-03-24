---
title: Dimension data validation
description: Learn how to validate journal entries and dimension data in Dynamics 365 Finance, including how to use the Validate and Simulate posting options on journal lines.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 03/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-10-01
ms.search.form: DimensionDataValidation
ms.dyn365.ops.version: 10.0.39
---

# Dimension data validation

[!include [banner](../includes/banner.md)]

Before you post a journal, you can check your entries for errors. There are two ways to validate dimension data: directly from journal lines in the user interface, or by using the **Dimension data validation** page.

## Validate journal lines

You can validate entries directly from any journal. From the journal, select **Lines** on the Action Pane to open the journal lines. Then, on the Action Pane, select the **Validate** dropdown to access the following options:

- **Validate** – Checks all journal lines for errors such as missing accounts, invalid dimension combinations, or amounts that don't balance. Any issues are displayed as messages so you can correct them before posting.
- **Validate voucher only** – Checks only the voucher-level rules, such as whether the voucher balances by currency, without running the full set of line-level checks.
- **Simulate posting** – Runs the full posting process without actually creating any accounting entries. Use this option to see exactly what would be posted, including generated distributions, so you can verify the results before committing.

[![Validate dropdown on journal lines showing Validate, Validate voucher only, and Simulate posting options.](./media/validate-transaction-journal-ui.png)](./media/validate-transaction-journal-ui.png)

## Validate from dimension fields

You can also trigger validation directly from any account or dimension field without navigating away from your current page.

On a segmented entry control, right-click the account field and select **Validate data integrity**.

[![Validate data integrity option on a segmented entry control.](./media/dimension-data-validation-sec.png)](./media/dimension-data-validation-sec.png)

On a dimension entry control, select **Options** > **Validate data integrity**.

[![Validate data integrity option on a dimension entry control.](./media/dimension-data-validation-dec.png)](./media/dimension-data-validation-dec.png)

## Validate by record ID

For advanced troubleshooting, you can validate whether a specific ledger account or default dimension combination is structurally valid by using the **Dimension data validation** page at **General ledger** > **Chart of accounts** > **Dimensions** > **Dimension data validation**.

Enter the following information and select **Run**:

- **Dimension type** – Select **Ledger dimension** to validate a ledger account combination, or **Default dimension** to validate a default dimension set.
- **Reference record ID** – The record ID of the record to validate. Ledger dimension IDs reference the **DimensionAttributeValueCombination** table; default dimension IDs reference the **DimensionAttributeValueSet** table. Record IDs can be found in dimension validation errors or by inspecting the backing data record.
- **Date** – The date to validate against, since dimension validity can vary based on active from/to dates and other setup.
- **Company** – The legal entity to use for validation, since some dimension combinations are only valid in a specific company.

[![Dimension data validation page.](./media/dimension-data-validation.png)](./media/dimension-data-validation.png)

The **Is valid** field shows whether the combination or set is valid. Select **Detailed results** to see the individual checks that were performed.

[![Dimension data validation detailed results.](./media/dimension-data-validation-detailed-results.png)](./media/dimension-data-validation-detailed-results.png)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
