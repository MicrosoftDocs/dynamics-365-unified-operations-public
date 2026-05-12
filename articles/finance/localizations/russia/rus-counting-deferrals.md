---
title: Deferrals counting (Russia)
description: Learn how to do deferrals counting for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/12/2026
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-06-28
---

# Deferrals counting (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to do deferrals counting for Russia in Microsoft Dynamics 365 Finance.

The deferrals functionality supports the process of deferrals counting and lets you print the *Inventory act (INV-11)* report.

Before you generate the Inventory act (INV-11) report, you must create deferrals and post writing-off transactions in the deferrals journal.

To prepare and generate the Inventory act (INV-11) report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **Deferrals** \> **Deferrals counting journal**.

    You can use the **Deferrals counting journal** page to create a Deferrals counting journal and print the **Inventory act (INV-11)** report.

    The following table describes the tabs on the **Deferrals counting journal** page.

    | Tab | Description |
|-----|-------------|
| Overview | Create a new Deferrals counting journal. > [!NOTE] > You can't create more than one journal that has the same counting date. |
| Officials | Specify the names, positions, and titles of the officials. |

    The following table describes the buttons on the Action Pane of the **Deferrals counting journal** page.

    | Button | Description |
|--------|-------------|
| Lines | Open the **Deferrals counting journal line** page, where you can create journal lines. |
| Close | Open the **End deferrals counting** dialog. In the **Counting end date** field, you can then enter the date when you want to close the journal. The date that you specify is shown in the **Counting end date** field on the **Deferrals counting journal** page. > [!NOTE] > You can't close the journal if journal lines aren't created. |
| Print | Open the **Deferrals counting** dialog, where you can print the **Inventory act (INV-11)** report by using the Microsoft Excel template for the selected model number. |

    The following table describes the fields on the **Deferrals counting journal** page.

    | Field | Description |
|-------|-------------|
| Show | Select which vouchers or journals are shown on the page, based on the posting status: **All** – Show all journals. **Open** – Show only journals that aren't posted. **Posted** – Show only journals that are posted. |
| Journal batch number | The deferral journal number. |
| Name | Select the journal name that has the **Deferrals** journal type. |
| Resolution number | Enter the resolution number for the counting journal. |
| Resolution date | Select the resolution date for the counting journal. |
| Counting start date | Select the start date of the deferrals counting period. By default, this field is set to the current date. |
| Counting end date | The end date of the deferrals counting period. |
| Closed | This checkbox is automatically selected when the deferral counting is completed and the journal is closed. |
| Position | Select the position title of the official. |
| Employee name | Select the name of the official in the list of company employees. |
| Title | Select the job title of the employee. |

1. To create a new Deferrals counting journal, follow these steps:

    1. On the Action Pane, select **New**.

        > [!NOTE]
        > You can't create more than one Deferrals counting journal that has the same counting date.

    1. In the **Name** field, select the journal name that has the **Deferrals** journal type.
    1. In the **Resolution number** field, enter the resolution number for the counting journal.
    1. In the **Resolution date** field, select the resolution date for the counting journal.
    1. In the **Counting start date** field, select the start date of the deferrals counting period. By default, this field is set to the current date.

        The **Counting end date** field is set to the end date that was set for the deferrals counting period in the **End deferrals counting** dialog.

    1. Select the **Officials** tab to set up the names, positions, and titles of the officials.
    1. In the **Position** field, select the position title of the official.
    1. In the **Employee name** field, select the name of the official in the list of company employees.
    1. In the **Job title** field, select the job title of the employee.

1. On the Action Pane, select **Lines** to open the **Deferrals counting journal line** page.

    You can use the **Deferrals counting journal line** page to view or modify existing journal lines, or to manually create new lines.

    The following table describes the fields on the **Deferrals counting journal line** page.

    | Field               | Description                                                                                                         |
    |---------------------|---------------------------------------------------------------------------------------------------------------------|
    | Model number        | Select the deferral model number.                                                                                   |
    | Counting start date | The start date that is specified for the deferral counting period on the **Deferrals counting journal** page.       |
    | Counting end date   | The end date that is specified for the deferral counting period on the **Deferrals counting journal** page.         |
    | Deferral ID         | Select the identification code that is associated with deferral.                                                    |
    | Name                | Enter the deferral name.                                                                                            |
    | Date attached       | Select the deferral creation date.                                                                                  |
    | Writing off time    | Select the write-off period for the deferral.                                                                       |
    | Writing off amount  | Enter the amount that is written off between the creation of the deferral and the beginning of the counting period. |
    | Remaining amount    | Enter the amount that must be written off in the future.                                                            |
    | Deferrals amount    | Select the deferral amount in the default currency.                                                                 |

1. To modify existing Deferrals counting journal lines, follow these steps:

    1. In the **Model number** field, select the deferral model number of the journal lines.

        > [!NOTE]
        > The **Counting start date** and **Counting end date** fields are set to the start and end dates that were set for the deferrals counting period on the **Deferrals counting journal** page.

    1. In the **Deferral ID** field, modify the deferral code.
    1. In the **Name** field, modify the deferral name.
    1. In the **Date attached** field, select the deferral creation date.
    1. In the **Writing off time** field, select the write-off period for the deferral.
    1. In the **Writing off amount** field, enter the amount that is written off between the creation of the deferral and the beginning of the counting period.
    1. In the **Remaining amount** field, enter the amount that must be written off in the future.
    1. In the **Deferrals amount** field, select the deferral amount in the default currency.
    1. Close the **Deferrals counting journal line** page.

    :::image type="content" source="../media/rus-counting-deferrals-01.jpg" alt-text="Screenshot of the Deferrals counting journal line page.":::

1. To print the **Inventory act (INV-11)** report, follow these steps:

    1. On the Action Pane, select **Close** to open the **End deferrals counting** dialog.
    1. In the **Counting end date** field, enter the date when you want to close the journal.

        > [!NOTE]
        > The date that you specify is shown in the **Counting end date** field on the **Deferrals counting journal** page.

    1. Select **OK** to close the journal.
    1. On the Action Pane, select **Print** to open the **Deferrals counting** dialog.
    1. In the **Model number** field, select the deferral model number.
    1. Select **OK** to print the **Inventory act (INV-11)** by using the Excel template for the selected model number.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
