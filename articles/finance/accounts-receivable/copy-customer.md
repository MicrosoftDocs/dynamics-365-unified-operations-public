---
title: Copy customers by using shared number sequences
description: Learn how to use shared number sequences to copy a customer to another legal entity but keep the same customer ID.
author: twheeloc
ms.author: twheeloc
ms.topic: conceptual
ms.date: 08/31/2018
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: CustTable
ms.dyn365.ops.version: 8.1
---

# Copy customers by using shared number sequences

[!include [banner](../includes/banner.md)]

You can use shared number sequences to assign customer IDs. Shared number sequences also let you copy customers from one legal entity to another legal entity but use the same customer IDs in both legal entities.

## Setup

The feature is activated when you use a shared number sequence to assign customer IDs. You must use the same number sequence in every legal entity that you want to copy a customer to. You change the customer number sequence on the **Accounts receivable parameters** page for each legal entity. Select **Accounts receivable** \> **Parameters**, and then select the **Number sequences** tab.

You can also set up customer number sequences for each customer group. These number sequences must also be shared. The number sequence for a customer group is used first. If no number sequence is specified for a customer group, the number sequence that is specified on the **Accounts receivable parameters** page is used.

You can also copy customers between legal entities if you use manual customer IDs. However, if you try to copy a customer to a legal entity where the customer ID already exists, the copy process won't be started.

## Copy a customer

To copy a customer, select **New** on the **All customers** list page to open the **Create customer** dialog box. Notice that the new customer ID isn't assigned immediately. This behavior differs from the behavior in previous versions. Because you haven't yet selected the customer group, the system can't determine the correct number sequence to use. Additionally, it can't determine whether you're trying to create a new customer or copy a customer. Therefore, the customer ID isn't assigned until you select **Save** at the bottom of the dialog box.

If you're creating a new customer, you can continue to fill in all the fields as you usually do. When you've finished, and you select **Save**, you will see that the customer ID was assigned automatically. Alternatively, for manual number sequences, you will see that your manual customer ID was used.

To copy a customer, in the **Name** field, enter one or more characters that represent the customer that you're looking for. A search dialog box shows a list of parties that might represent the customer that you're looking for. When you select one of the parties, additional information appears on the right side of the dialog box:

- The **General** tab shows the party's phone number and address.
- The **Roles** tab shows the roles that the selected party can have and the legal entity where it has each role.
- **Tax registration ID** tab shows the tax registration IDs that are assigned to the party.

You can copy a party only if it has a customer role, and if it has that role in a legal entity that isn't the current legal entity. When you find a party that meets these criteria, follow these steps.

1. A **Copy customer** option appears. By default, this option is set to **No**. To copy the customer to the current legal entity, set the option to **Yes**. 
2. A **Legal entity** field appears. Select the legal entity to copy the customer from. If the customer exists in only one legal entity, the field is set to that legal entity by default.
3. Select **Select**. The new customer is created.

## Validation

When you copy a customer, the system tries to save the new customer information. Validations are run to verify that the data that was copied is good. You receive an error message for every validation that fails. The error messages explain what information must be updated. The copy of the customer can't be saved until you fix all the validation errors.

## Copy a customer by using tax exempt number search feature

You can also copy customers by using the Tax exempt number search feature that is in the **Registration** group on the **Customer** tab on the Action Pane of the **All customers** page. The **Tax exempt number search** dialog box that appears shows tax exempt numbers, the customer ID, the customer name, and the legal entity where the tax exempt ID is used. You can copy a customer only if it's in a legal entity that isn't the current legal entity. After you select a customer that meets this criterion, follow these steps.

1. A **Copy customer** option appears. By default, this option is set to **No**. To copy the customer to the current legal entity, set the option to **Yes**. 
2. Select **Select**. The new customer is created.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
