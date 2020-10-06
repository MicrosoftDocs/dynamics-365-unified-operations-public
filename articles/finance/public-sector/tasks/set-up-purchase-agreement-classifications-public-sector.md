--- 
# required metadata 
 
title: Set up purchase agreement classifications in the public sector
description: The purchase agreement classification allows you to control the administrative information that is available on purchase agreements. 
author: twheeloc
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: AgreementClassification   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up purchase agreement classifications in the public sector

[!include [banner](../../includes/banner.md)]

The purchase agreement classification allows you to control the administrative information that is available on purchase agreements. 

This procedure was created for the French public sector using the PSUS demo company data in the public sector partition.

1. Go to Procurement and sourcing > Setup > .. > Purchase agreement classification.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. Optional: Select the Subcontractors option to include information about subcontractors.
    * A purchase agreement can have a prime contractor, co-contractors, and subcontractors. You can assign the prime contractor to the parent purchase agreement and a co-contractor or subcontractor to specific child agreements.  
6. Optional: Select the Certifications option to include information about certifications for vendors.
    * Certification information can be used to generate a report that lets you monitor vendor compliance with certification requirements.  
7. Optional: Select the Require direct invoicing option to prevent the use of release orders.
8. Optional: Select the Activities option to include information about tasks and milestones.
9. Click Save.

