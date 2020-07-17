---
# required metadata

title: Custom service development
description: This topic describes how to create a custom service.
author: Sunil-Garg
manager: AnnBe
ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Custom service development

[!include [banner](../includes/banner.md)]

You can develop custom services for Finance and Operations. When a developer writes a custom service under a service group, the service group is always deployed on two endpoints:

- SOAP endpoint
- JSON endpoint

### SOAP-based custom service

SOAP-based services remain the same as they were in Dynamics AX 2012.

Code examples for consuming custom services using SOAP are available in the [Microsoft Dynamics AX Integration GitHub repository](https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/ServiceSamples/SoapConsoleApplication).

#### Key changes

- All the service groups under the **AOTService group** node are automatically deployed.
- All services that must be deployed must be part of a service group.

**Example endpoint for a dev environment**

`https://usnconeboxax1aos.cloud.onebox.dynamics.com/soap/services/UserSessionService?wsdl`

**Example endpoint for a non-dev environment**

`https://<baseurl>/soap/services/UserSessionService?wsdl`

For more information about custom services, see:

- [Using Custom Services \[AX 2012\] (TechNet)](https://technet.microsoft.com/library/hh509052.aspx)
- [Walkthrough: Exposing an X++ Class as a Data Contract (TechNet)](https://technet.microsoft.com/library/gg844225.aspx)

<!--
- [Custom services Office Mix presentation](https://mix.office.com/watch/12e4fejbgj429). -->


### JSON-based custom service

This feature enables X++ classes to be consumed as JSON services. In other words, the return data set is in JSON format. JSON, which stands for JavaScript Object Notation, is a compact, lightweight format that is commonly used communicate data between the client and the server.

The JSON Endpoint is at `https://host_uri/api/services/service_group_name/service_group_service_name/operation_name`.

**Example**

`https://usnconeboxax1aos.cloud.onebox.dynamics.com/en/api/services/UserSessionService/AifUserSessionService/GetUserSessionInfo`

Code examples for consuming JSON services are available in the [Microsoft Dynamics AX Integration GitHub repository](https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/ServiceSamples/JsonConsoleApplication).
