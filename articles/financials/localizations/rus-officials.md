---
# required metadata

title: Set up officials who generate a transportation invoice and a job ticket
description: This topic provides information about setting up officials who generate transportation invoives and job tickets in Microsoft Dynamics 365 for Finance and Operations in Russia. 
author: ShylaThompson
manager: AnnBe
ms.date: 7/9/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up officials who generate a transportation invoice and a job ticket
[!include [banner](../includes/banner.md)]

This topic applies to features in the **Inventory management** module. It does not apply to features in the [Warehouse management](warehouse-management.md) module.

Use the **Officials** form to specify the officials who are involved in the transportation of cargo. You can select the officials who are responsible for intercompany and intracompany transactions.

You must set up records for the officials who are responsible for transportation on both sides of the transactions, so you must set up records for the officials both on the customer or vendor side, and on the company side. This information is required when you generate and print a transportation invoice and a job ticket that are based on a bill of lading.

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.

2.  To set up records for the officials who are responsible for transportation on outgoing documents for customers, click the **Sales orders** tab, and then select **Invoice** or **Invoice - credit-note**.
    
    1.  Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    
    2.  In the **Name** field, select the customer contact who is responsible for transportation.
    
    3.  Create a record for an official. In the **Position** field, select **Transportation responsible**.
    
    4.  In the **Name** field, select the company contact who is responsible for transportation.

3.  To set up records for the officials who are responsible for transportation on incoming documents for vendors, click the **Purchase orders** tab, and then select **Invoice** or **Invoice - credit-note**.
    
    1.  Create a record for an official. In the **Position** field, select **Vendor transportation responsible**.
    
    2.  In the **Name** field, select the vendor contact who is responsible for transportation.
    
    3.  Create a record for an official. In the **Position** field, select **Transportation responsible**.
    
    4.  In the **Name** field, select the company contact who is responsible for transportation.

4.  To set up records for the officials who are responsible for transportation on incoming or outgoing warehouse documents, click the **Inventory item management** tab, and then select **Issue slip for sales order (M-15)** or **Issue slip for transfer order (M-15)**.
    
    1.  Create a record for an official. In the **Position** field, select **Customer transportation responsible**.
    
    2.  In the **Name** field, select the customer contact who is responsible for transportation.
    
    3.  Create a record for an official. In the **Position** field, select **Transportation responsible**.
    
    4.  In the **Name** field, select the company contact who is responsible for transportation.
        

        > [!NOTE]
        > You can set up a record for a <STRONG>Transportation responsible</STRONG> official only if you selected <STRONG>Issue slip for transfer order (M-15)</STRONG>.

## Set up officials for the counting list (INV-5) 

This topic applies to features in the **Inventory management** module. It does not apply to features in the [Warehouse management](warehouse-management.md) module.

Use the **Officials** form to set up officials that are involved with the item counting process for the Counting list (INV-5) report.

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.

2.  On the **Inventory** tab, in the left pane, click **Counting list (INV-5)**.

3.  In the right pane, press CTRL+N to create a new official.

4.  In the **Position** field, select the designation of the official.
    
    > [!NOTE]
    > You can set up a maximum of one chair and one person who is in charge.

5.  In the **Name** field, enter the name of the official.

6.  In the **Job title** field, select the alias for the job title of the official.

## Set up officials for the Counting act INV-6 report 

This topic applies to features in the **Inventory management** module. It does not apply to features in the [Warehouse management](warehouse-management.md) module.

Use this form to set up officials for the **Counting act (INV-6)** report. You can identify the company officials who are involved in the item counting process for the **Counting act (INV-6)** report.

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.

2.  Click the **Inventory** tab, and then, in the left pane, select **Counting act (INV-6)**.

3.  Click **Add** to create an official for the **Counting act (INV-6)** report.

4.  In the **Position** field, select the designation of the official.

5.  In the **Name** field, enter the name of the official.

6.  In the **Job title** field, select the job title of the official.

## Set up officials for the NVFA statement of writing-off (No. MB-8) 

Use this procedure to set up the members and chairman of the commission that is responsible for the NVFA Statement of writing off (No. MB-8).

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.

2.  On the **Fixed assets** tab, click **NVFA Statement of writing-off (No. MB-8)**.

3.  Click **Add** to create a new record.

4.  In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chairman. You can only select one employee as the chairman.

5.  In the **Name** field, select the name of the employee.

## Set up officials for the Issue slip (M-15) 

Use the **Shipment** form to set up officials for the Issue slip (M-15) report that is generated for bailment.

1.  Click **Inventory management** \> **Periodic** \> **Transfer orders**.

2.  In the **Transfer orders** form, select a transfer order for bailment.

3.  Click **Posting** \> **Ship transfer order** to open the **Shipment** form.

4.  Click the **Officials** tab, and then select the job title of the contact official.

5.  Click **OK** to post the transfer order shipments that includes information about officials.


