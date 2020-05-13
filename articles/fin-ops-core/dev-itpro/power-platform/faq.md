---
# required metadata

title: FAQ
description: Description goes here.
author: Sunil-Garg
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# FAQ

[!include[banner](../includes/banner.md)]

**Do Tier 1 F&O environments or DEMO topologies work?**

Yes, Tier 1 and DEVTEST and DEMO topologies should work.

**What version of F&O do I need?**

10.0.12 is the minimum version required.

**Can an ISV solution take dependencies on virtual entities? What does the ALM look like?**

Yes. The Virtual Entities are all generated in the MicrosoftOperationsERPVE solution which is "API Managed". That means the items in the solution change as you make entities visible/hidden, but it is still a "managed" solution that you can take dependency upon. The standard ALM flow would be to just take a standard reference to a Virtual Entity from this solution with the "add existing" option
in the ISV solution. It will then show as a missing dependency of the solution and be checked at solution import time. During import if a specified Virtual Entity does not yet exist, it would automatically be made visible without needing additional work.

**Which entities does the user see in the catalog in CDS from F&O?**

Generally, it is all entities marked as IsPublic=Yes. These are the same entities that are visible in OData today.
**Do all users in Power Platform need to be users in F&O?**

Any user of Power Platform attempting to access F&O data through Virtual Entity must also exist as a user in F&O. So technically not *all* users, only those users who access F&O data through Virtual Entity.

**Where do I find the catalog entity?**

It is named "Available Finance and Operations Entities" in the advanced find window.

**Is there a way to specify company when performing data operations on a VE?**

Yes. Unlike F&O where the company is implicit, in CDS it is an explicit field on each company-striped entity. You can use either the "Company Code" field (the four-character string), or the "Company" field (a lookup to cdm_Company). Both will provide the same information.

**Can we change the prefix for the virtual entities?**

No. In the case of Finance and Operations virtual entities, they should all be generated in the MicrosoftOperationsERPVE solution, and should all have the mserp\_ prefix. This should not be changed. If you have a scenario where you believe the prefix should be changed, please share that scenario with us.

**How can I filter data in a Power App based on the current user or any other
dynamic criteria like today-10?**

You could write a pre-operation plugin on the RetrieveMultiple message of the entity, and in it change the criteria on the query. Or alternatively a post-operation plugin to filter the results before returning them.

**Can we pin a model driven app into F&O?**

Currently it is not possible.

**How can we show data from multiple VE's joined to a physical entity record in CDS in the same grid?**

This is not possible in CDS today.

**How do we do 'add subcomponents' in the new power app experience?**

Like the classic UI, you would re-do the "Add Existing" operation. With the solution selected and Customer Groups already added as an entity, do this:

1.  Add existing \> Entity

2.  Select customer group \> Next

3.  Under "components", pick "Select components"

4.  Select the fields/relationships/forms/etc you want and hit Add

**If we want to default a value on a field during pre-create, will doing an initValue on the data entity work?**

Yes. The order of calls is:

1.  CDS sends a create or update.

2.  This invokes all the existing logic on the F&O entity and backing tables,
    including defaulting that may change values.

3.  Once complete, CDS sends another Retrieve(single) message to get the latest
    copy of the data, including any fields that were defaulted.

 **Is it possible to hit the debug on F&O when we do a CRUD from CDS? If yes, which process do I need to attach?**

Yes, to debug in F&O, start Visual Studio as administrator. Normally the F&O one box runs under "w3wp.exe" as a process, but the act of starting VS as an administrator will automatically start IISExpress.exe and host F&O there. Attach to IISExpress.exe (or w3wp.exe if not running as administrator). To set breakpoints in the virtual entity code, find the CDSVirtualEntityAdapter and CDSVirtualEntityController classes. The adapter class is the first one called and just does serialization/deserialization. It then delegates to the controller to do the actual queries. So usually the controller class is the easiest place to put breakpoints.

**Does the forms business logic gets called in F&O through virtual entity?**

F&O business logic that lives on forms would not be invoked through Virtual Entity. Rather, you should expect the same behavior you would get through OData access to the same entities. It is expected that when an entity is exposed to Odata (IsPublic=Yes) that it has appropriate protections to ensure data cannot be corrupted. If there are entities without this protection, that is a bug on the entity. If you see differences in entity behavior between Odata and Virtual Entity, then that's a bug on the Virtual Entity feature.

**When I develop a new F&O entity and want to see it in CDS.  Do I need to click "Refresh entity list" in F&O? Then is there anything to do in CDS?**

In theory, no, you don't need to refresh anything. If anything, you would need to do an IISReset (or restart iisexpress, depending on where your AOS is running). We cache the fact that the list of entities is "accurate" in SysGlobalObjectCache, which is a per-process cache. Any time we can't find a thing there saying it's accurate, we rebuild the list, which takes around 5 seconds. So any time you restart your AOS process (w3wp.exe or iisexpress.exe), the next time you query the list from CDS it will be accurate. Recompile
*should* also flush the SGOC, but if it doesn't then the AOS restart will.
