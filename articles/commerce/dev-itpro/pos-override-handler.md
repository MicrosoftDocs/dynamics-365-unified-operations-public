---
# required metadata

title: POS Override request handler (SDK)
description: This topic provides general information about the Retail SDK. The Retail SDK includes code, code samples, templates, and tools that you can use to customize retail functionality.
author: RobinARH
manager: AnnBe
ms.date: 09/05/2018
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
ms.custom: 17771
ms.assetid: c54d34a5-32e2-4d0d-a1c2-4a9940d95ade
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2018-05-30
ms.dyn365.ops.version: AX 7.3.5

---

# POS Override request handler (SDK)

[!include [banner](../../includes/banner.md)]

This topic explains how to override POS request handler. We introduced new extension pattern for overriding the POS business logic, if you have any scenario where you want to modify/add some business logic to the core POS business flow then you can follow this pattern.

**Example**

When you sell serial item, POS will show a dialog to enter the serial number for that item after the scan, but if you want to automate the serial number process by entering the serial number through code then you can override this serial number handler and customize. Any business logic in POS is based upon request and response. So, you can override the relevant request and return the response according to your business scenario.

> [!NOTE]
> Not all business request is exposed for customization only few requests are overridable. If you want to customize any business logic and if that request is not overrdiable then create a support ticket or log a request in the LCS extensibility tool. Later in this article we have listed the list of requests available for overriding.
