--- 
# required metadata 
 
title: Set up electronic tax declaration (Germany)
description: This procedure walks you through setting electronic tax declaration. 
author: NickSelin
manager: AnnBe 
ms.date: 02/17/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Germany
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up electronic tax declaration (Germany)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through setting electronic tax declaration.

This procedure was created using the demo data company DEMF. 

This functionality is available for legal entities whose primary address is in Germany.

You should have a valid user certificate (like test-soft-pse.pfx) and a Tax authority certificate (Coala2019.pem.cer) before you can complete this procedure.



1. Go to Tax > Setup > Sales tax > Electronic tax declaration setup.
2. Click Edit.
3. Select Yes in the Authentication field.
4. In the Format mapping field, enter or select a value.
    * As a prerequisite you should upload from LCS Elster configuration (model and format) for Generic electronic reporting.  
5. Click Electronic tax certificates.
6. Click New.
7. In the User ID field, enter or select a value.
    * You should first install certificates through Microsoft Management Console and assign friendly names that will be used in these steps.  In MMC for private certificate go to “Certificates / Personal /Certificates”, right mouse click.  In the context menu click All Tasks > Import....  Grant read permissions to the certificate for the user who is doing the submission.  In MMC Right click on the certificate and use All Tasks/Manage Private Keys – select the user and add read permission.  For Tax authority certificate in MMC right-click “Trusted Root Certificate Authorities”  Import "Coala2019.pem.cer".  
8. In the Certificates reference field, type a value.
9. Click Save.
10. Close the page.
11. Click HTTP servers.
    * HTTP url addresses are provided by the authority and can be changed by the authority. Microsoft provides default addresses that are used by the system randomly.  
12. Click Save.
13. Close the page.
14. Click Save.

