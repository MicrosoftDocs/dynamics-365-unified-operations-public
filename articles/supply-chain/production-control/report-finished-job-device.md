---
# required metadata

title: Report as finished to a license plate controlled location from the Job card device
description: This topic decribes the process for completing finished products on a production order to inventory when a license plate controls the location.
author: johanhoffmann
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgRegistration, ProdJournalTransJob, ProdJournalTransRoute, ProdParmReportFinished
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 19351
ms.assetid: bcc9e242-b4b8-4144-b14d-c3c106fb40ec
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2019-09-06
ms.dyn365.ops.version: AX 10.0.6

---

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

# Report as finished to a license plate controlled location from the Job card device 

The process called Reporting as finished completes finished products on a production order to the inventory. If the finished product is enabled for the advanced warehouse processes, the product is reported as finished to a location called the production output location. For information about setting up the production output location, see [Production output location](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/production-control/production-output-location).

You must select an existing license plate number to complete this task. If the production output location is set up to be tracked by license plate, then a license plate number must be included when reporting the production output location as finished. The **License plate** field is visible on the **Report progress** prompt on the **Job card device** page. The field is only visible on the **Report progress** prompt when reporting on the last operation of the production order. The field is only shown if the item for the production order is enabled for the warehouse management processes. 
