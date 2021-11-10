---
# required metadata

title: Testing for memory leaks
description: This topic describes how to test custom e-commerce code for memory leaks in Microsoft Dynamics 365 Commerce. 
author: samjarawan
ms.date: 09/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Testing for memory leaks

[!include [banner](../includes/banner.md)]

This topic describes how to test custom e-commerce code for memory leaks in Microsoft Dynamics 365 Commerce. 

Memory leak tests can be done on pages to ensure custom e-commerce module and data action code is not leaking any memory. Page mocks will be used to test memory usage on a page.  See details in the
The following steps can be used to generat heap snapshots of an e-commerce page with custom code.

* Create a [page mock](test-page-mock.md) that represents the e-commerce page you want to test.  This can be a custom page mock or see the [page mocks](test-page-mock.md) documentation to save a live production page into a page mock using the **?item=nodeserviceproxy:true** query string parameter.
* 


 
