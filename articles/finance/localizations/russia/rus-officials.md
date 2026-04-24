---
title: Set up officials (Russia)
description: Learn how to set up officials in Russia who generate transportation invoices and job tickets and who are involved in various reports with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.search.form: OfficialsTable_RU
---

# Set up officials (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to set up officials in Russia who generate transportation invoices and job tickets and who are involved in various reports with Microsoft Dynamics 365 Finance.

## Set up officials who generate transportation invoices and job tickets

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up the officials who are involved in the transportation of cargo. You can select the officials who are responsible for intercompany and intracompany transactions.

You must set up records for the officials who are responsible for transportation on both sides of the transactions. Therefore, you must set up records for the officials both on the customer or vendor side, and on the company side. This information is required when you generate and print a transportation invoice and a job ticket that are based on a bill of lading.

To set up officials who generate transportation invoices and job tickets, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
1. To set up records for the officials who are responsible for transportation on outgoing documents for customers, on the **Sales orders** tab, select either **Invoice** or **Invoice - credit-note**, and then follow these steps:
    1. Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    1. In the **Name** field, select the customer contact who is responsible for transportation.
    1. Create a record for an official. In the **Position** field, select **Transportation responsible**.
    1. In the **Name** field, select the company contact who is responsible for transportation.
1. To set up records for the officials who are responsible for transportation on incoming documents for vendors, on the **Purchase orders** tab, select either **Invoice** or **Invoice - credit-note**, and then follow these steps:
    1. Create a record for an official. In the **Position** field, select **Vendor transportation responsible**.
    1. In the **Name** field, select the vendor contact who is responsible for transportation.
    1. Create a record for an official. In the **Position** field, select **Transportation responsible**.
    1. In the **Name** field, select the company contact who is responsible for transportation.
1. To set up records for the officials who are responsible for transportation on incoming or outgoing warehouse documents, on the **Inventory item management** tab, select either **Issue slip for sales order (M-15)** or **Issue slip for transfer order (M-15)**, and then follow these steps:
    1. Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    1. In the **Name** field, select the customer contact who is responsible for transportation.
    1. Create a record for an official. In the **Position** field, select **Transportation responsible**.

        > [!NOTE]
        > You can set up a record for a **Transportation responsible** official only if you selected **Issue slip for transfer order (M-15)**.

    1. In the **Name** field, select the company contact who is responsible for transportation.

## Set up officials for the counting list (INV-5) report

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up the officials who are involved in the item counting process for the **Counting list (INV-5)** report.

To set up officials for the counting list (INV-5) report, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
1. On the **Inventory** tab, in the left pane, select **Counting list (INV-5)**.
1. In the right pane, press Ctrl+N to create an official.
1. In the **Position** field, select the designation for the official.

    > [!NOTE]
    > You can set up a maximum of one chair and one person who is in charge.

1. In the **Name** field, enter the name of the official.
1. In the **Job title** field, select the alias for the job title of the official.

## Set up officials for the Counting act INV-6 report

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up officials for the **Counting act (INV-6)** report. You can identify the company officials who are involved in the item counting process for the report.

To set up officials for the Counting act INV-6 report, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
1. On the **Inventory** tab, in the left pane, select **Counting act (INV-6)**.
1. Select **Add** to create an official for the **Counting act (INV-6)** report.
1. In the **Position** field, select the designation for the official.
1. In the **Name** field, enter the name of the official.
1. In the **Job title** field, select the job title of the official.

## Set up officials for the NVFA statement of writing-off (No. MB-8) report

Use the **Officials** page to set up the members and chair of the commission that is responsible for the NVFA Statement of writing-off (No. MB-8) report.

To set up officials for the NVFA statement of writing-off (No. MB-8) report, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
1. On the **Fixed assets** tab, select **NVFA Statement of writing-off (No. MB-8)**.
1. Select **Add** to create a record.
1. In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chair. You can select only one employee as the chair.
1. In the **Name** field, select the name of the employee.

## Set up officials for the Issue slip (M-15) report

Use the **Shipment** page to set up officials for the **Issue slip (M-15)** report that is generated for bailment.

To set up officials for the Issue slip (M-15) report, follow these steps:

1. In Dynamics 365 Finance, go to **Inventory management** \> **Periodic** \> **Transfer orders**.
1. On the **Transfer orders** form, select a transfer order for bailment.
1. Select **Posting** \> **Ship transfer order**.
1. On the **Shipment** page, on the **Officials** tab, select the job title of the contact official.
1. Select **OK** to post the transfer order shipments that include information about officials.

## Additional resources

- [Set up signers for print forms](../europe/emea-set-up-signers-for-printing-forms.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
