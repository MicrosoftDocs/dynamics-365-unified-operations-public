---
title: Create fiscal notes for return in Brazil tax reform
description: Learn about how to create fiscal notes for return orders in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 07/13/2026
ms.custom: bap-template
---

# Create fiscal notes for return in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to create a fiscal document for a goods return in Brazil tax reform in Dynamics 365 Finance. It covers two scenarios depending on whether the customer is a registered taxpayer.

> [!IMPORTANT]
>
> - **Taxpayer customer**: The customer issues the Return NFe (finNFe = 4) using a return CFOP. Process this option through a return sales order.
> - **Non-taxpayer customer**: The seller issues an incoming Return NFe on behalf of the customer. Set the **Generate incoming fiscal document** field to **No** on the sales order header, and provide the original document access key manually.

## Fields in the Fiscal information header

The following fields in the **Fiscal information** section of the sales order header control how the return fiscal document is generated. You can find these fields on the **Header** tab of the sales order, under the **Fiscal information** FastTab.

### Full refusal

-The **Full refusal** field is a Yes/No toggle.
-This field is only applicable when **Purpose of return** is set to **5 - Refusal**. When set to **Yes**, it indicates a total refusal or a customer-not-located scenario. When set to **No**, it indicates a partial refusal.
-For **Purpose of return = 4 - return** scenarios, this field doesn't apply and doesn't need to be set.

> [!NOTE]
>
> For the case of Customer not located, select **Full refusal** to be Yes.

### Generate incoming fiscal document

The **Generate incoming fiscal document** field is a Yes/No toggle. When set to **Yes** (default), the system automatically generates an incoming fiscal document for the return on behalf of the customer.
When set to **No**, the system doesn't generate the incoming document automatically, and you must provide the original document access key manually at the time of posting. Set this field to **No** for returns from non-taxpayer customers who can't issue their own NFe.

> [!NOTE]
>
> This field determines whether the value in Fiscal document is **Fiscal establishment** or **Third party**.

### Purpose of return

The **Purpose of return** field is a dropdown that specifies the fiscal purpose of the return. This value maps to the **finNFe** (finalidade da NFe) field in the Brazilian electronic invoice standard. This field is required and must be set before the return invoice can be posted. The available values are:

- **4 - return**: The NFe is issued for return purposes. This value applies to the scenarios covered in this article. It generates a **Return NFe** (issued by the customer) for taxpayer customer returns, or a **Return NFe - incoming** (issued by the seller on behalf of the customer) for non-taxpayer customer returns.
- **5 - Refusal**: The NFe is issued for refusal purposes and generates a **Credit Note**. This value covers three sub-scenarios: customer not located, total refusal of delivered goods, or partial refusal of delivered goods. In all refusal scenarios, the Credit Note is issued by the issuer of the original sales NFe, with CFOP 1.949 (intrastate) or 2.949 (interstate). Use the **Full refusal** toggle to distinguish between total and partial refusal.

---

## Workflow

### Scenario 1: Return from a taxpayer customer

Use this scenario when the customer is a registered taxpayer and the goods were previously accepted and are now being returned.

#### Create a return sales order

To create a return order from an existing sales order, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All return orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Select **Find sales order**.
1. In the list, find and select the original sales order.
1. Select the **Select all** check box.
1. Select **OK**.

#### Register the returned items

To register the returned goods and assign a disposition code, follow these steps:

1. Select **Update line** > **Registration**.
1. In the **Disposition code** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Select **Add registration line**.
1. Select **Confirm registration**.
1. Select **Save**.
1. Close the page.

#### Post the packing slip

To post the packing slip for the return, follow these steps:

1. Select **Post packing slip**.
1. Select **OK**.
1. Select **OK**.
1. Close the page.

#### Configure taxes and post the return invoice

To configure the CFOP and tax groups, and post the return invoice, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. In the list, find and select the return sales order.
1. Select the **Lines** tab.
1. In the **CFOP** field, enter or select a return CFOP value.
1. In the list, select the link in the selected row.
1. Select the **Setup** tab.
1. In the **Item sales tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Invoice** > **Invoice**.
1. In the **Quantity** field, select an option.
1. In the **Purpose of return** field, select an option.
1. Select **OK**.
1. Select **OK**.
1. Close the page.

    > [!NOTE]
    > The CFOP for a return must be a return CFOP code (for example, starting with **5** for intrastate or **6** for interstate returns). Verify the CFOP matrix setup if the expected code doesn't appear.

---

### Scenario 2: Return from a non-taxpayer customer (incoming fiscal document)

Use this scenario when the customer isn't a registered taxpayer and can't issue an NFe. The seller generates the return fiscal document on behalf of the customer.

#### Create a sales order and disable incoming fiscal document generation

To create a sales order for the non-taxpayer return, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. In the list, find and select the original sales order.
1. Select the **Header** tab.
1. Select **Edit**.
1. Set **Generate incoming fiscal document** to **No**.
1. Select **Save**.

#### Post the return invoice with access key

To post the return invoice and provide the original document access key, follow these steps:

1. On the Action Pane, select **Invoice** > **Invoice**.
1. In the **Purpose of return** field, select an option.
1. Select **OK**.
1. In the **Access key** field, type the access key of the original fiscal document.
1. Select **OK**.
1. Select **OK**.
1. Close the page.

    > [!IMPORTANT]
    > The access key of the original sales NFe is required. Without it, the return fiscal document can't be correctly linked to the original transaction for Brazil Tax Reform reporting purposes.

---

### Verify the posted return fiscal document

To verify that the return fiscal document was posted correctly, follow these steps:

1. Go to **Accounts receivable** > **Fiscal documents** > **All fiscal documents**.
1. In the list, find and select the posted return record.
1. Verify that the fiscal reference to the original document is present.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
