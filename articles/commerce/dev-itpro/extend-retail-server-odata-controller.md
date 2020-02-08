---
# required metadata

title: Extend a Cloud Scale Unit OData controller
description: This topic provides code that extends the CustomController class.
author: kfend
manager: AnnBe
ms.date: 11/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 31681
ms.assetid: c39a34b5-3fce-446f-877b-0aa41817ef25
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Extend a Cloud Scale Unit OData controller

[!include [banner](../includes/banner.md)]

This topic provides code that extends the CustomersController class.

A controller is a mapping for a commerce entity that controls create, read, update, and delete (CRUD) behaviors and actions for a commerce entity type. Each commerce entity must have a corresponding controller. You can extend a controller that is included with Microsoft Dynamics 365 Commerce to add new business actions that meet your business requirement. 

To extend an existing controller, you must define a new class that extends an existing controller class. When you create a new controller that extends an existing controller, the new controller can create new or override existing methods in the controller that is being extended. All methods in the extended controller that have not been overridden will continue to function as before. In this example, the **ExtendedCustomersController** class extends the **CustomersController** class, and the **CustomersController** class is the controller for the **Customers** entity type.  

You will need to update the **extensionComposition** section of the Commerce Scale Unit Web.config file. For more information, see the **How to call the new retail server API from MPOS/Cloud POS** section of [Commerce runtime (CRT) and Retail Server extensibility](commerce-runtime-extensibility.md). You can find the sample code from this topic in the Retail software development kit (SDK). 

```csharp
using System.Web.Http;
using System.Web.OData;
using Microsoft.Dynamics.Commerce.Runtime;
using Microsoft.Dynamics.Commerce.Runtime.DataModel;
using Microsoft.Dynamics.Retail.RetailServerLibrary;
using Microsoft.Dynamics.Retail.RetailServerLibrary.ODataControllers;
	
namespace Microsoft.Dynamics.RetailServer.ExtensionSamples
{
	class ExtendedCustomersController : CustomersController
	{
	    [CommerceAuthorization(new string[] { "Employee", "Application" })]
	    [HttpPost]
	    public override PageResult<GlobalCustomer> Search(ODataActionParameters parameters)
	    {
	        ThrowIf.Null<ODataActionParameters>(parameters, nameof(parameters));
	        parameters["customerSearchCriteria"] += " My custom criteria";
	        return base.Search(parameters);
	    }
	}
}
```
