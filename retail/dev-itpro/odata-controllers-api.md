---
# required metadata

title: Web API and OData controllers
description: This article provides code to extend the ApiController class so that you can create a Web API controller for Retail Server.
author: kfend
manager: AnnBe
ms.date: 2016-02-05 00 - 38 - 12
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31481
ms.assetid: 4107b5a0-b4c4-4b83-b5b9-2fd82b26f36f
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Web API and OData controllers

This article provides code to extend the ApiController class so that you can create a Web API controller for Retail Server.

By default, all the Retail Server binaries in Microsoft Dynamics AX use only OData. If you want to use a controller that uses a traditional Web API, you can create your own Web API controller and extend the Web API configuration. The following example shows how to create a Web API controller for Retail Server.

    namespace Microsoft.Dynamics.RetailServer.Samples.Extensions
    {
        using System.Collections.Generic;
        using System.Runtime.InteropServices;
        using System.Web.Http;
        using Commerce.Runtime.DataModel;
        using Retail.StoreServerServiceLibrary;
        [ComVisible(false)]
        [ExtendedController("Values")]
        [CommerceAuthorization(AllowedRetailRoles = new string[] { CommerceRoles.Anonymous }, CheckRetailOperation = false)]
        public class ValuesController : ApiController
        {
            // GET /api/values
            public IEnumerable<string> Get()
            {
                return new string[] { "value1", "value2" };
            }
        }
    }

To create the controller, create a new class that uses the **Export** attribute, and specify that the type is the **IWebApiConfig** interface. The **IWebApiConfig** interface has one method that you can override, the **Register** method. After you override the **Register** method, you can call the base class to get the same mapping as an OData metadata controller. You must derive from the standard Web API controller. You can then customize the controller to meet your business requirements. For more information, see [ASP.NET Web API](http://msdn.microsoft.com/en-us/library/hh833994(v=vs.108).aspx).

