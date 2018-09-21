---
# required metadata

title: Set up fixed assets locations and numbering (Russia)
description:
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up fixed assets locations and numbering (Russia)

[!include [banner](../includes/banner.md)]

## Set up a fixed asset location 

You can use the **FA location** page to set up a fixed asset location and specify the company division that the asset belongs to.

Locations are defined for fixed assets to calculate depreciation accrual. Depending on the fixed asset location, the calculated depreciation amount is allocated to the production cost of the product or to a ledger account.

You must define the location of the fixed asset before you acquire the fixed asset. If you are transferring a fixed asset from one location to another, you can create a transfer transaction to register the transfer of the asset..

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Location**.

2.  Click **New** to create a fixed asset location.

3.  In the **Location** and **Name** fields, enter a location code and a description for the location.

4.  In the **Separate division ID** field, select a separate division if the fixed asset is not located at the head office of the company. If you do not specify a separate division, the location of the fixed asset is the head office.

5.  Click the **Fixed asset posting profiles** FastTab.

6.  Create a line.

7.  In the **Groupings** field, select the grouping for the fixed asset posting profile from one of the following options:
    
      - **Table** – The posting profile is grouped by the selected fixed asset.
    
      - **Group** – The posting profile is grouped by the depreciation group.
    
      - **All** – The posting profile is grouped by all fixed assets.
    
      - **Accounting** – The posting profile is grouped by the value model.

8.  In the **Account/Group number** field, select the depreciation group, fixed asset, or value model that the posting profile is used for.

9.  In the **Main account** field, select a ledger account to use to post the fixed asset transactions.

10. In the **Account for depr.bonus** field, select a ledger account to use to post the depreciation bonus for the fixed asset, if a depreciation bonus applies.


## Fixed asset numbering 

Select an option for assigning numbers to fixed assets:

  - Manual selection: This is appropriate for a company with few fixed assets. No setup is required for manual selection. You can simply enter the fixed asset number when you create fixed assets on the **Fixed assets** page.
  - Automatic numbering of all fixed assets from one default number sequence: To use this method, you must set up at least one number series. Specify a default number series when you set up a fixed asset.
  - Automatic numbering of fixed assets based on fixed asset group: This method is appropriate for a company with a large number of fixed assets. You can create many Account/Group numbers for fixed assets, and attach a number series to each group. You must specify a default number series when you set up fixed assets.
    
    > [!NOTE]
    > You can set up numbering for fixed assets only when you set up the journal name for the asset transactions in the **Journal names** form. 


### Automatic numbering of all fixed assets from one default number sequence

1.  Click **Organization administration** \> **Common** \> **Number sequences** \> **Number sequences**.

2.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**. to open the **Fixed Asset Parameters** form.

3.  On the **Number sequences** tab, select a number sequence code for the FA number reference.

4.  Press CTRL+S or close the form.

When you create a fixed asset in the **Fixed assets** form, the next number in the sequence is automatically entered into the fixed asset number field.


> [!NOTE]
> You can assign special number sequences for selected fixed asset groups while applying the default number sequence to fixed assets that do not have group-specific number sequences.

### Automatic numbering of fixed assets based on fixed asset group

1.  Click **Fixed assets** \> **Setup** \> **FA group table** to open the **FA group table** form.

2.  Select the **Autonumeration FA** check box for the selected FA group, and then select the appropriate number sequence in the **FA autonumber sequence** field.

This number sequence is used for all fixed assets that are assigned to the fixed asset group.


> [!NOTE]
> To create a fixed asset group, press CTRL+N, and then enter the required details.

## Create bar codes from fixed asset numbers 

> [!NOTE]
> This topic has not been fully updated for Microsoft Dynamics AX 2012 R2.

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Create barcodes from FA inventory number**.

2.  Click **Select** to open the **Assets** form, and then enter the selection criteria for the fixed asset.

3.  Click **OK** to return to the **Forming barcode from FA number** form.

4.  Click **OK**. If you have not specified a bar code for the fixed asset, the value that you have specified in the **FA number** field will display in the **Bar code** field in the **Fixed assets** form.


