---
# required metadata

title: Set up service order stages 
description: Set up service order stages. 
author: sorenva
ms.date: 05/07/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Set up service order stages 

[!include [banner](../includes/banner.md)]


1.  Go to **Service management** \> **Setup** \> **Service orders** \> **Service stages**.

2.  Select **New** to create a new record.

3.  In the **Service stage** and **Description** fields, specify a service stage ID and description.

4.  Select the appropriate parameters for the stage.

5.  Select the parent stage for the current stage or leave the **Parent** field blank if the stage is the initial stage in the stage setup.


> [!NOTE]
> <P>You cannot modify the <STRONG>Parent</STRONG> field after you save the stage. Instead, you can delete the record and create the record again with a different selection in the <STRONG>Parent</STRONG> field.</P>
> <P>Also, you can only create one stage with a blank <STRONG>Parent</STRONG> field. That is, only one initial stage is permitted.</P>


  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]