---
# required metadata

title: Asset loan
description: This topic describes how to register loan assets in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset loan


If your company receives assets for repair or maintenance jobs from other locations, internally or from customers, and you loan assets temporarily to the locations or customers that send assets you to be repaired, **Asset Management** can keep track of your asset loans.

## Register loan asset on a maintenance request

1. Click **Asset management** > **Common** > **Maintenance requests** > **All maintenance requests** or **Active maintenance requests**.
2. Select the maintenance request on which you want to register a loan, and click **Edit**.
3. In the **Request** form, click **Send loan asset**.
4. Select the asset and insert an expected return date.
5. Click **OK**.

>[!NOTE]
>
- It is only possible to send a loan asset if an asset of the same asset type is available. 
- The loan asset must have an asset lifecycle state that allows it to be used as a loan asset, for example, "InStorage". When the loan asset has been registered, the asset lifecycle state of that asset is automatically updated to, for example, "OnLoan".

Click **Asset management** > **Common** > **Asset loan** > **All asset loans** to see a complete list of all the assets you have loaned to other locations or customers. If the **Ended** check box is selected on an asset, it means that the asset has been registered as returned to your company.

![Figure 1](media/06-manage-maintenance-requests.png)

In **Active asset loans**, you see a list of all the loan assets that have not yet been returned to your company.


## Register loan asset as returned

1. Click **Asset management** > **Common** > **Asset loan** > **Active asset loans**.
2. Select the asset loan that you want to register as returned and click **Return asset loan**.
3. Insert date and time in the **Returned** field and click **OK**.
4. Update the **Active asset loans** list, and you will notice that the loan is no longer on the active list.
