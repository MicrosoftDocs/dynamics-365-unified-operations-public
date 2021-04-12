---
# required metadata

title: Flushing principle not respected
description: Flushing principle not respected
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable,ProdParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: johanho@microsoft.com

---

# Flushing principle not respected

KB Number: 4612725

When the Automatic BOM consumption parameter in Receive Purchase order section of the Automatic update tab is set to Flushing principle, all BOM lines are auto consumed when the PO is received, including those BOM lines set to Manual. BOM lines set to Manual should not be auto consumed by definition.


## Resolution
Please check the setting of Automatic BOM consumption in the production control parameters by site. In standard demo data it is set to Always which means that the flushing principles on the BOM lines will be disregarded and always flushed. Try set it to Flushing principle instead.


