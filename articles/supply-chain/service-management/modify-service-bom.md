---
title: Modify a Service BOM 
description: Learn how to modify service BOMs, including step-by-step processes for updating service BOM elements and deleting service BOM lines.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAAgreementTable
ms.topic: how-to
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---


# Modify a Service BOM

[!include [banner](../includes/banner.md)]

You can record the history of an element in a service bill of materials (BOM). Every time that you update a BOM line, a history line is created in the **History** pane. The history line shows the current state of the BOM line.

## Update a service BOM element

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.

2. Select **Edit** to open the **Service agreements** details page.

3. On the Action Pane, select **Service objects** to open the **Service objects** page.

4. Select the object to update a BOM line for, and then select **Designer**.

5. On the **Designer** page, select the BOM line to update, and then select **Edit BOM line**.

    > [!NOTE]
    > On the **Setup** tab, select the **Edit when adding** check box if you want the **Edit BOM line** page to open when you drag a line into the service BOM.

6. In the **Quantity** field, enter the quantity.

7. If you want to create a service order line for the replacement item, which can then be invoiced, select the **Create service order line** check box.

8. Select **OK** to close the page.

## Delete a service BOM line

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.

2. Select **Edit** to open the **Service agreements** details page.

3. On the Action Pane, select **Service objects** to open the **Service objects** page.

4. Select the object to delete a service BOM line from, and then select **Designer**.

5. On the **Designer** page, select the BOM line to delete, and then select **Delete BOM line**.

## Related information

- [Template BOMs](template-boms.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
