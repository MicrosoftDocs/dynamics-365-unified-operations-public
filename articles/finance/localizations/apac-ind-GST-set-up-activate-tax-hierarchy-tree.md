---
# required metadata

title: Set up a sales tax hierarchy and the setoff rules
description: This topic explains how to set up a sale tax hierarchy and the setoff rules.
author: EricWangChen
ms.date: 06/05/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Set up a sales tax hierarchy and the setoff rules

[!include [banner](../includes/banner.md)]

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax hierarchies**.
2. Select **New**.
3. In the **Name** field, enter a value.
4. In the **Structure** field, select **GTE hierarchy**.

    ![Create a sales tax hierarchy dialog box.](media/Annotation-2019-05-15-145825.png)

5. Select **OK**.
6. On the **Versions** FastTab, select **Synchronize**.
7. Close the message that you receive.
8. Select **View**.

    ![Versions FastTab.](media/Annotation-2019-05-15-150106.png)

    The **Sales tax hierarchy designer** page shows the tax type and tax components, based on the configuration.

    ![Sales tax hierarchy designer page.](media/Annotation-2019-05-15-150259.png)

9. Select **Setoff rules for sales tax hierarchy**, and then select **New**.
10. In the **Name** field, enter a value, and then save the record.
11. On the **Recoverable** and **Payable** FastTabs, select the tax components, and adjust the priority values.
12. Define the setoff rules according to the legal requirement.

    ![Setoff rules for sales tax hierarchies page.](media/Annotation-2019-05-15-150432.png)

13. Select **Save**, and then select **Close**.
14. Close the **Sales tax hierarchy designer** page.
15. Select **Activate**, and then select **Close**.

## Maintain setoff hierarchy profiles

1. Go to **Tax** \> **Setup** \> **Sales Tax** \> **Maintain setoff hierarchy profiles**.
2. Select **New**.
3. In the **Effective date** field, enter a value.
4. In the **Hierarchy** field, select a value.

    ![Create a setoff hierarchy profile dialog box.](media/Annotation-2019-05-15-150613.png)

5. Select **OK**, and then select **Activate**.
6. Select **Yes**.
7. Close the message that you receive, and then close the page.

## GST minor codes

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **GST minor codes**.
2. Select **New** to create a record.
3. In the **Tax component** field, select a value.
4. In the **Minor code** field, enter a value.
5. In the **Description** field, enter a value.
6. Select **Save**, and then select **Close**.

![GST minor code page.](media/Annotation-2019-05-15-151254.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
