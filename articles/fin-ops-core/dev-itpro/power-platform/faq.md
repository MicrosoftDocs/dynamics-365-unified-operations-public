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

**Do Tier 1 Finance and Operations environments or demo topologies work?**

Yes, Tier 1 and DEVTEST and DEMO topologies should work.

**What version of Finance and Operations do I need?**

10.0.12 is the minimum version required.

**Can an ISV solution take dependencies on virtual entities? What does the ALM look like?**

Yes. The virtual entities are all generated in the MicrosoftOperationsERPVE solution which is "API Managed". That means the items in the solution change as you make entities visible/hidden, but it is still a "managed" solution that you can take dependency upon. The standard ALM flow would be to just take a standard reference to a virtual entity from this solution with the "add existing" option
in the ISV solution. It will then show as a missing dependency of the solution and be checked at solution import time. During import if a specified virtual entity does not yet exist, it would automatically be made visible without needing additional work.

**Which entities does the user see in the catalog in Common Data Service from Finance and Operations?**

Generally, it is all entities marked as IsPublic=Yes. These are the same entities that are visible in OData today.

**Do all users in Power Platform need to be users in Finance and Operations?**

Any user of Power Platform attempting to access Finance and Operations data through virtual entity must also exist as a user in Finance and Operations. So technically not *all* users, only those users who access Finance and Operations data through virtual entity.

**Where do I find the catalog entity?**

It is named "Available Finance and Operations Entities" in the advanced find window.

**Is there a way to specify company when performing data operations on a virtual entity?**

Yes. Unlike Finance and Operations where the company is implicit, in Common Data Service it is an explicit field on each company-striped entity. You can use either the "Company Code" field (the four-character string), or the "Company" field (a lookup to cdm_Company). Both will provide the same information.

**Can we change the prefix for the virtual entities?**

No. In the case of Finance and Operations virtual entities, they should all be generated in the MicrosoftOperationsERPVE solution, and should all have the mserp\_ prefix. This should not be changed. If you have a scenario where you believe the prefix should be changed, please share that scenario with us.

**How can I filter data in a Power App based on the current user or any other dynamic criteria like today-10?**

You could write a pre-operation plugin on the RetrieveMultiple message of the entity, and in it change the criteria on the query. Or alternatively a post-operation plugin to filter the results before returning them.

**Can we pin a model driven app into Finance and Operations?**

Currently it is not possible.

**How can we show data from multiple virtual entity's joined to a physical entity record in Common Data Service in the same grid?**

This is not possible in Common Data Service today.

**How do we do 'add subcomponents' in the new power app experience?**

Like the classic UI, you would re-do the "Add Existing" operation. With the solution selected and Customer Groups already added as an entity, do this:

1.  Add existing \> Entity

2.  Select customer group \> Next

3.  Under "components", pick "Select components"

4.  Select the fields/relationships/forms/etc you want and hit Add

**If we want to default a value on a field during pre-create, will doing an initValue on the data entity work?**

Yes. The order of calls is:

1.  Common Data Service sends a create or update.

2.  This invokes all the existing logic on the Finance and Operations entity and backing tables, including defaulting that may change values.

3.  Once complete, Common Data Service sends another Retrieve (single) message to get the latest copy of the data, including any fields that were defaulted.

**Is it possible to hit the debug on Finance and Operations when we do a CRUD from Common Data Service? If yes, which process do I need to attach?**

Yes, to debug in Finance and Operations, start Visual Studio as administrator. Normally the Finance and Operations one box runs under "w3wp.exe" as a process, but the act of starting VS as an administrator will automatically start IISExpress.exe and host Finance and Operations there. Attach to IISExpress.exe (or w3wp.exe if not running as administrator). To set breakpoints in the virtual entity code, find the CDSVirtualEntityAdapter and CDSVirtualEntityController classes. The adapter class is the first one called and just does serialization/deserialization. It then delegates to the controller to do the actual queries. So usually the controller class is the easiest place to put breakpoints.

**Does the forms business logic gets called in Finance and Operations through virtual entity?**

Finance and Operations business logic that lives on forms would not be invoked through virtual entity. Rather, you should expect the same behavior you would get through OData access to the same entities. It is expected that when an entity is exposed to Odata (IsPublic=Yes) that it has appropriate protections to ensure data cannot be corrupted. If there are entities without this protection, that is a bug on the entity. If you see differences in entity behavior between Odata and virtual entity, then that's a bug on the virtual entity feature.

**When I develop a new Finance and Operations entity and want to see it in Common Data Service.  Do I need to click "Refresh entity list" in Finance and Operations? Then is there anything to do in Common Data Service?**

In theory, no, you don't need to refresh anything. If anything, you would need to do an IISReset (or restart iisexpress, depending on where your AOS is running). We cache the fact that the list of entities is "accurate" in SysGlobalObjectCache, which is a per-process cache. Any time we can't find a thing there saying it's accurate, we rebuild the list, which takes around 5 seconds. So any time you restart your AOS process (w3wp.exe or iisexpress.exe), the next time you query the list from Common Data Service it will be accurate. Recompile *should* also flush the SGOC, but if it doesn't then the AOS restart will.
