---
# required metadata

title: Vehicles and realty as fixed assets (Russia)
description: This topic explains how to set up and use vehicles and realty as fixed assets for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
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

Use the **Fixed asset parameters** page to set up parameters for fixed assets of the **Realty** and **Vehicle** types. You can also select the method that is used to determine the start date for the calculation of depreciation.

1. Select **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2. On the **Tax reporting** tab, in the **Date of including in the tax base** field, specify when the fixed asset should be entered in tax base of the assessed register:

    - **Putting into operation date** – The date when the fixed asset is put to use.
    - **Date of the registration** – The registration date of the fixed asset.

## Register realty as a fixed asset

Before you put a realty fixed asset into operation and calculate depreciation, you must register the fixed asset in the assessed tax registers. Use the **Fixed assets** page to register a fixed asset of the **Realty** type.

1. Select **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select **New** to create a fixed asset, and enter the required details.
3. On the **General** FastTab, in the **Type** field, select **Realty**.
4. On the **Technical information** FastTab, in the **Date of the registration** field, select the registration date of the fixed asset.
   
5. In the **Removal from the register date** field, select the date when the asset should be removed from the tax register.

    > [!NOTE]
    > The **Date of the registration** and **Removal from the register date** fields are available only if you selected **Realty** or **Vehicle** in the **Type** field on the **General** FastTab.

6. On the **Tax reporting** FastTab, in the **Assessed tax** section, in the **Asset kind** field, select the type of asset.

    > [!NOTE]
    > The **Assessed tax** section isn't available if you selected **Vehicle** or **Ground area** in the **Type** field on the **General** FastTab.

7. In the **Sales tax code** field, select the sales tax code for the assessed tax.

    > [!NOTE]
    > The **Sales tax code** field is available only if you selected **1** or **3** in the **Asset kind** field.

8. In the **Exemption from tax** field, select the tax benefit code for the transport tax.

## Set up the depreciation start date for vehicles and realty

Use the **Depreciation groups** page to set up the start date for depreciation of fixed assets of the **Realty** and **Vehicle** types. Depreciation is calculated based on the registration date of the asset. If an asset is registered after it's put into operation, depreciation is calculated from the first day of the month of registration. If an asset is registered before it's put into operation, depreciation is calculated from the first day of the month after the asset is put into operation.

1. Select **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2. Create a depreciation group, and enter the required details.
3. On the **General** FastTab, in the **Depreciation start date** field, select **Date of the registration** to specify that the registration date of a fixed asset should be used as the depreciation start date.

## Depreciate a fixed asset by using a fixed asset journal

After you put a fixed asset of the **Vehicle** or **Realty** type into operation, you can use the **FA journal** page to start to depreciate the asset from the registration date.

1. Select **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2. Select **New** to create a fixed asset journal.
3. In the **Name** field, select a journal name.
4. In the **Description** field, enter a description of the journal.
5. Select **Lines** to open the **Journal voucher** page.
6. Select **New** to create a journal line.
7. Select **OK**. The depreciation line for the value model that is registered in the fixed asset account is shown on the **Journal voucher** page.
8. Select **Validate** \> **Validate** to validate the depreciation transaction.
9. Select **Post** \> **Post** to post the transaction.
