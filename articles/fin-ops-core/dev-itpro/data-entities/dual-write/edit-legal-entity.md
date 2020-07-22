---

title: Edit legal entity after dual-write setup
description: Learn how to add or remove a company or legal entity after dual-write has been initially set up.
author: sabinn-msft
manager: AnnBe
ms.date: 07/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-douklo
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sabinn
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Edit legal entity after dual-write setup 

[!include [banner](../../includes/banner.md)]



With this feature, we now provide you with the ability to add or remove a company or legal entity after dual-write has been set up, without the need to unlink and relink your dual-write environment.  

The dual-write wizard enables you to link your Finance and Operations apps to Common Data Service environments. As part of this wizard, you also get to select one or more legal entities or companies. The company or legal entity list doesn’t remain static and is constantly changing. There may be a need to add new companies, especially as part of a phased rollout or acquisitions. Up until now, you were unable to add a company or legal entity without system down-time wherein you have to unlink and relink your environment, which can be expensive, especially because of pre-existing data. With this feature, you can add a company in a live environment without the need for unlinking your existing dual-write environment. 

## How to add a company after dual-write has been set up 

From the dual-write entity map list page, select the **Environment details** button.

![Select environment details](media/select-environment-details.png)

Under the **Legal entities** tab, you would see the company&mdash;in this example, USMF&mdash;that you selected as part of the dual-write wizard to link environments.

![Displays the selected company](media/legal-entities.png)

Select **Add legal entity** to add one or more companies to dual-write&mdash;in this example, GBSI&mdash;and select **Save**.

![Add new legal entity](media/add-legal-entity.png)

At this point, the legal entities start updating. The entity maps that are currently running or paused go through the initial write process by copying pre-existing data. Until the process is completed, we recommend that you don't perform any actions to modify your entity maps. 

![Update legal entities is in progress](media/update-progress.png)

>[!Note]
> This operation may fail if either of the following conditions are true: 
>
> * You add or remove a new company when one or more entity map is already in the Initial Writes phase where it is copying pre-existing data. 
>
> * You remove a company when one or more entity maps is in the Paused state. 

Once the process is complete, you'll see a banner informing you that the legal entities have been updated successfully and can resume updates to your entity maps. 

![Legal entities update succeeded](media/legal-entities-updated.png)

