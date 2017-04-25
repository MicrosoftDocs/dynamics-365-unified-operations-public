---
# required metadata

title: Install a financial reporting binary hotfix
description: Use this tutorial to install a financial reporting binary hotfix from Microsoft Dynamics Lifecycle Services (LCS). 
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 6734
ms.assetid: 23e47c55-7bac-4a2b-91bd-66562016a16a
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Install a financial reporting binary hotfix

[!include[banner](../includes/banner.md)]


Use this tutorial to install a financial reporting binary hotfix from Microsoft Dynamics Lifecycle Services (LCS). 

### Update a one-box environment

1.  Download the patch.zip file from Microsoft Dynamics Lifecycle Services (LCS).
2.  Click **Administrator Tools** &gt; **Services**, and** **stop the Management Reporter 2012 Process Service. [![Services\_MRHotfix](./media/services_mrhotfix.png)](./media/services_mrhotfix.png)
3.  Run the following commands:
    -   'MROneBox\\Instructions\\MRHotfix.ps1' PowerShell script

4.  Restart the Management Reporter 2012 Process Service.

### Updating a multi-box environment

#### Update each BI or MR machine

1.  On each BI or MR machine.
    -   Click **Administrator Tools** &gt; **Services**, and** **stop the Management Reporter 2012 Process Service. [![Services\_MRHotfix](./media/services_mrhotfix.png)](./media/services_mrhotfix.png)
    -   Once the Process service has been stopped on each BI or MR machine, proceed with step 2 below.

2.  Download the patch.zip file from LCS.
3.  Run the following commands:
    -   'MRProcessService\\Instructions\\MRHotfix.ps1' PowerShell script

4.  Start the Management Reporter 2012 Process Service on each BI or MR machine.

#### Update each AOS machine

1.  Download the patch.zip file from LCS.
2.  Run the following commands:
    -   'MRApplicationService\\Instructions\\MRHotfix.ps1' PowerShell script



See also
--------

[Download hotfixes from Lifecycle Services](download-hotfix-lcs.md)


