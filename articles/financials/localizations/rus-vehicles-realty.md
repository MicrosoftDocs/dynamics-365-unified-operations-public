---
# required metadata

title: Vehicles and realty as fixed assets (Russia)
description: This topic provides information about setting up and using vehicles and realty as fixed assets for Russia.
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

# Vehicles and realty as fixed assets (Russia)

[!include [banner](../includes/banner.md)]

## Set up fixed asset parameters for vehicles and realty 

Use the **Fixed asset parameters** form to set up parameters for fixed assets of type **Realty** or **Vehicle**. You can also select the method to be used to determine the starting date used to calculate depreciation.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.

2.  Click the **Tax reporting** tab.

3.  In the **Date of including in the tax base** field, specify the date to enter the fixed asset in the assessed register tax base from the following options:
    
      - **Putting into operation date** – The date when the fixed asset is put to use.
    
      - **Date of the registration** – The registration date for the fixed asset.
      
## Register realty as a fixed asset 

Before you put a realty fixed asset into use and calculate depreciation, you need to register the fixed asset in the assessed tax registers. Use the **Fixed assets** form to register a fixed asset of the **Realty** type.

1.  Click **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.

2.  Click **Fixed asset** to create a fixed asset, and then enter the required details. For more information, see [(RUS) Create fixed assets](rus-create-fixed-assets.md).

3.  On the **General** FastTab, in the **Type** field, select **Realty**.

4.  Click the **Technical information** FastTab, and then, in the **Date of the registration** field, select the registration date for the fixed asset.
    

    > [!NOTE]
    > <P>If you selected <STRONG>Date of the registration</STRONG> in the <STRONG>Depreciation start date</STRONG> field in the <STRONG>Depreciation groups</STRONG> form, you must specify the registration date for the fixed asset. Otherwise, the depreciation transactions are not created. If you modify the registration date, the starting date for depreciation is updated.</P>



5.  In the **Removal from the register date** field, select the date when the asset is scheduled for removal from the tax register.
    

    > [!NOTE]
    > <P>The <STRONG>Date of the registration</STRONG> and <STRONG>Removal from the register date</STRONG> fields are available only if you selected <STRONG>Realty</STRONG> or <STRONG>Vehicle</STRONG> in the <STRONG>Type</STRONG> field on the <STRONG>General</STRONG> tab.</P>



6.  Click the **Tax reporting** FastTab.

7.  In the **Assessed tax** field group, in the **Asset kind** field, select the type of asset.
    

    > [!NOTE]
    > <P>The <STRONG>Assessed tax</STRONG> field group is not available if you selected <STRONG>Vehicle</STRONG> or <STRONG>Ground area</STRONG> in the <STRONG>Type</STRONG> field on the <STRONG>General</STRONG> FastTab.</P>



8.  In the **Sales tax code** and **Exemption from tax** fields, select the sales tax code for the assessed tax and the tax benefit code for the transport tax.
    

    > [!NOTE]
    > <P>The <STRONG>Sales tax code</STRONG> field is available only if you selected <STRONG>1</STRONG> or <STRONG>3</STRONG> in the <STRONG>Asset kind</STRONG> field.</P>

## Set up the depreciation starting date for vehicles and realty 

Use the **Depreciation groups** form to set up the depreciation starting date for fixed assets of type **Realty** or **Vehicle**. Depreciation is calculated based on the registration date for the asset. If an asset is registered after it is put to use, depreciation is calculated from the first day of the month of registration. If an asset is registered before it is put to use, depreciation is calculated from the first day of the month after the asset is put to use.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.

2.  Create a depreciation group, and then enter the required details.

3.  Click the **General** tab.

4.  In the **Depreciation start date** field, select **Date of the registration** to specify the registration date for a fixed asset as the depreciation starting date.

## Depreciate a fixed asset by using a fixed asset journal 

After you put a fixed asset of the **Vehicle** or **Realty** type into operation, you can use the **FA journal** form to start depreciating the asset from the date of registration.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.

2.  Click **New** to create a fixed asset journal. For more information, see

3.  In the **Name** and **Description** fields, select a journal name and enter a description for the journal.

4.  Click **Lines** to open the **Journal voucher** form.

5.  Create a journal voucher.

6.  In the **Add to journal** form, in the **Transaction date** field, select the transaction date.

7.  In the **Transaction type** field, select **Depreciation**.

8.  In the **FA inventory number** field, select the inventory number of the fixed asset.

9.  In the **Value model** and **Reason code** fields, select the value model for the fixed asset and the reason code.

10. Click **OK**. The depreciation line for the value model that is registered in the fixed asset account is displayed in the **Journal voucher** form.

11. Click **Validate** \> **Validate** to validate the depreciation transaction.

12. Click **Post** \> **Post** to post the transaction.

## Set up a division for a company and associate it with a vendor 

Use the **Separate divisions** form to create a company division, and then associate the division with a vendor. If your company has several divisions, you must associate each division with a vendor.

1.  Click **Organization administration** \> **Setup** \> **Separate divisions**.

2.  Create a company division.

3.  In the **Separate division ID** field, enter the identification code for the division.

4.  In the **Name** field, enter the name of the division.

5.  In the **Vendor account** field, select the vendor account number that is associated with the division.

6.  Select the **Independent** check box to indicate that the selected division can report the tax declarations independently of the head office.

