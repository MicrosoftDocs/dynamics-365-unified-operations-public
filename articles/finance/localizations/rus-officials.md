---
# required metadata

title: Set up officials (Russia)
description: This topic explains how to set up officials in Microsoft Dynamics 365 Finance in Russia.
author: ShylaThompson
ms.date: 07/11/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: OfficialsTable_RU  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up officials (Russia)
[!include [banner](../includes/banner.md)]

This topic explains how to set up officials in Russia who generate transportation invoices and job tickets and who are involved in various reports.

## Set up officials who generate transportation invoices and job tickets

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up the officials who are involved in the transportation of cargo. You can select the officials who are responsible for intercompany and intracompany transactions.

You must set up records for the officials who are responsible for transportation on both sides of the transactions. Therefore, you must set up records for the officials both on the customer or vendor side, and on the company side. This information is required when you generate and print a transportation invoice and a job ticket that are based on a bill of lading.

1. Select **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2. To set up records for the officials who are responsible for transportation on outgoing documents for customers, on the **Sales orders** tab, select either **Invoice** or **Invoice - credit-note**, and then follow these steps:

    1. Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    2. In the **Name** field, select the customer contact who is responsible for transportation.
    3. Create a record for an official. In the **Position** field, select **Transportation responsible**.
    4. In the **Name** field, select the company contact who is responsible for transportation.

3. To set up records for the officials who are responsible for transportation on incoming documents for vendors, on the **Purchase orders** tab, select either **Invoice** or **Invoice - credit-note**, and then follow these steps:

    1. Create a record for an official. In the **Position** field, select **Vendor transportation responsible**.
    2. In the **Name** field, select the vendor contact who is responsible for transportation.
    3. Create a record for an official. In the **Position** field, select **Transportation responsible**.
    4. In the **Name** field, select the company contact who is responsible for transportation.

4. To set up records for the officials who are responsible for transportation on incoming or outgoing warehouse documents, on the **Inventory item management** tab, select either **Issue slip for sales order (M-15)** or **Issue slip for transfer order (M-15)**, and then follow these steps:

    1. Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    2. In the **Name** field, select the customer contact who is responsible for transportation.
    3. Create a record for an official. In the **Position** field, select **Transportation responsible**.

        > [!NOTE]
        > You can set up a record for a **Transportation responsible** official only if you selected **Issue slip for transfer order (M-15)**.

    4. In the **Name** field, select the company contact who is responsible for transportation.

## Set up officials for the counting list (INV-5) report

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up the officials who are involved in the item counting process for the **Counting list (INV-5)** report.

1. Select **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2. On the **Inventory** tab, in the left pane, select **Counting list (INV-5)**.
3. In the right pane, press Ctrl+N to create an official.
4. In the **Position** field, select the designation for the official.

    > [!NOTE]
    > You can set up a maximum of one chair and one person who is in charge.

5. In the **Name** field, enter the name of the official.
6. In the **Job title** field, select the alias for the job title of the official.

## Set up officials for the Counting act INV-6 report

This procedure applies to features in the **Inventory management** module. It doesn't apply to features in [Warehouse management overview](../../supply-chain/warehousing/warehouse-management-overview.md).

Use the **Officials** page to set up officials for the **Counting act (INV-6)** report. You can identify the company officials who are involved in the item counting process for the report.

1. Select **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2. On the **Inventory** tab, in the left pane, select **Counting act (INV-6)**.
3. Select **Add** to create an official for the **Counting act (INV-6)** report.
4. In the **Position** field, select the designation for the official.
5. In the **Name** field, enter the name of the official.
6. In the **Job title** field, select the job title of the official.

## Set up officials for the NVFA statement of writing-off (No. MB-8) report

Use the **Officials** page to set up the members and chair of the commission that is responsible for the NVFA Statement of writing-off (No. MB-8) report.

1. Select **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2. On the **Fixed assets** tab, select **NVFA Statement of writing-off (No. MB-8)**.
3. Select **Add** to create a record.
4. In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chair. You can select only one employee as the chair.
5. In the **Name** field, select the name of the employee.

## Set up officials for the Issue slip (M-15) report

Use the **Shipment** page to set up officials for the **Issue slip (M-15)** report that is generated for bailment.

1. Select **Inventory management** \> **Periodic** \> **Transfer orders**.
2. On the **Transfer orders** form, select a transfer order for bailment.
3. Select **Posting** \> **Ship transfer order**.
4. On the **Shipment** page, on the **Officials** tab, select the job title of the contact official.
5. Select **OK** to post the transfer order shipments that include information about officials.

## Additional resources

- [Set up signers for print forms](emea-set-up-signers-for-printing-forms.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]