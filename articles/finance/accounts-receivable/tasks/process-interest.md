--- 
title: Process interest
description: Learn about how to create, print, and post interest notes, including outlines on setting up interest on posting profiles and calculating interest.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 09/28/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustPosting, SysQueryForm, CustInterestNote, SrsReportViewerForm 
ms.dyn365.ops.version: Version 7.0.0 
---

# Process interest

[!include [banner](../../includes/banner.md)]

This procedure shows how to create, print, and post interest notes. This task uses the USMF demo company.


## Set up interest on the posting profile
1. Go to **Credit and collections > Setup > Customer posting profiles**.
2. Click **Edit**.
3. In the **Setup** FastTab, in the **Interest code** field, select an interest code from the drop-down list. If you don't want interest calculated for transactions using this posting profile, leave the field blank. The **Table restriction** FastTab allows you to change the way that interest is processed. If this field is set to **Yes**, then interest will be calculated for this posting profile.  

## Calculate interest
1. Go to **Credit and collections > Interest > Create interest notes**.
2. You must select the transaction types for which you will calculate interest. All of the open transactions for these types will be included in the calculation.  
3. If you set **Interest** to **Yes**, you will calculate interest on interest. You may want to check the laws governing the calculation of interest on interest before including these transactions.  
4. In the **From date** field, enter a date from which the interest will be calculated. If you don't specific a **From date**, then all unposted interest notes will be canceled and interest will be recalculated from the transaction date.
5. In the **To date** field, enter a date to which the interest would be calculated.
6. In the **Use posting profile from** field, select an option. There are three posting profile options:
    - **Account** – Use the posting profile that is assigned to the customer account for each interest note. 
    - **Select** – Use the posting profile that you select in the **Posting profile** field.
    - **Transaction** – Use the individual posting profile from transactions on which interest is calculated for each interest note. Transactions that don't have an assigned posting profile will use the posting profile that is specified in the **Ledger and sales tax** area of the **Accounts receivable parameters** page.  
7. Expand the **Records to include** FastTab.
8. Click **Filter**.
9. In the **Criteria** field, enter a **Customer ID**. For example, enter 'US-001'.
6. Click **OK**.
7. Click **OK**.

## Print interest notes
1. Go to **Credit and collections > Interest > Review and process interest notes**.
2. In the **Status** field, select **Created**.
3. In the **Printed** field, select **Not printed**.
4. Click **Print**.
5. Expand the **Records to include** FastTab.
6. Click **OK**.
7. Close the page.

## Post the interest note
1. Select an interest note that is ready to post (status is **Created**).
2. Click **Post**.
3. Enter the posting date for the interest note. Select **Yes** to create a general ledger transaction for each interest note. If you don't select **Yes**, the interest on all interest notes to the customer is accumulated and posted to the general ledger in one transaction. The **Interest per transaction** option defaults to **Yes** and is disabled when the interest note is created with **Use posting profile from** value set to **Transaction**. The **Interest per transaction** is enabled when interest notes are created using options **Account** or **Select**.
4. Expand the **Records to include** FastTab.
5. Click **OK**.
6. In the **Status** field, select **Posted**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
