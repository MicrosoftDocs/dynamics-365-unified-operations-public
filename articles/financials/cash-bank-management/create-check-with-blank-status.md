---
# required metadata

title: Create checks with a blank status 
description: You can create blank status checks for a bank account from the Checks page. 
author: Annette Bruer
manager: AnnBe
ms.date: 10/26/2017
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: BankChequeTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 21941
ms.assetid: d7e22bd8-fd0d-47e1-843f-45ab0193ff8d
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2019-09-17
ms.dyn365.ops.version: AX 10.0.5

---

# Create checks with a blank status
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the capability to create blank checks. For example, you might create blank check to reocord a check that has been damaged and can't be used for payment. 

The **Checks** page is where you perform maintenance tasks on checks, such as creating new check numbers and deleting checks. Blank status checks can also be created from this page. After a check has been created with a Blank status, it cannot be deleted or reused in the system. This feature is available from the **Checks** page if the **Create checks with a blank status on the Checks page** parameter on the **Feature management** page is enabled. If the feature is not enabled, then Blank status checks can be created from the **Payment by check** dialog during the Accounts payable payment generation process.

To navigate to the **Checks** page, click **Cash and bank management > Bank accounts > Bank accounts > Manage payments > Checks** or **Cash and Bank management > Inquiries and Reports > Checks**.

Click **Create blank checks** to complete the process. While the system is creating checks with a blank status, the associated bank account will be inactivated temporarily. This reduces the risk of generating payments at the same time that blank status checks are created. When the processing is finished, the associated bank account is reactivated.
