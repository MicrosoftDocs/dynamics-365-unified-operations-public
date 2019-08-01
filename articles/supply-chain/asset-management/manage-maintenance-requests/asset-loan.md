---
# required metadata

title: Object loan
description: This topic describes how to register loan objects in Enterprise Asset Management.
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

# Object loan



This topic describes how to register loan objects in Enterprise Asset Management. If your company receives objects for repair or maintenance jobs from other locations, internally or from customers, and you loan objects temporarily to the locations or customers that send objects to you to be repaired, **Enterprise Asset Management** can keep track of your object loans.

## Register loan object on a request

1. Click **Enterprise asset management** > **Common** > **Requests** > **All requests** or **Active requests**.
2. Select the request on which you want to register a loan, and click **Edit**.
3. In the **Request** form, click **Send loan object**.
4. Select the object and insert an expected return date.
5. Click **OK**.

>[!NOTE]
>It is only possible to send a loan object if an object of the same object type is available. The loan object must have an object stage that allows it to be used as a loan object, for example, "InStorage". When the loan object has been registered, the object stage of that object is automatically updated, for example, to "OnLoan".

Click **Enterprise asset management** > **Common** > **Object loan** > **All object loans** to see a complete list of all the objects you have loaned to other locations or customers. If the **Ended** check box is selected on an object, it means that the object has been registered as returned to your company. The figure below shows a screenshot of the interface.

![Figure 1](media/05-manage-requests.png)

In **Active object loans**, you see a list of all the loan objects that have not
yet been returned to your company.

>[!NOTE]
>In **All object loans**, if you select a loan and click **Transfer to customer**, the loan object is transferred to the customer as an active object.

## Register loan object as returned

1. Click **Enterprise asset management** > **Common** > **Object loan** > **Active object loans**.
2. Select the object loan that you want to register as returned and click **Return object loan**.
3. Insert date and time in the **Returned** field and click **OK**.
4. Update the **Active object loans** list by pressing **F5**. You will notice that the loan is no longer on the active list.
