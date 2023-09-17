---
# required metadata

title: Custom service development
description: This article describes how to create a custom service.
author: peakerbl
ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Custom service development

[!include [banner](../includes/banner.md)]

You can develop custom services for finance and operations. When a developer writes a custom service under a service group, the service group is always deployed on two endpoints:

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

- [Using Custom Services \[AX 2012\] (TechNet)](/dynamicsax-2012/appuser-itpro/using-custom-services)
- [Walkthrough: Exposing an X++ Class as a Data Contract (TechNet)](/dynamicsax-2012/appuser-itpro/walkthrough-exposing-an-x-class-as-a-data-contract)

### JSON-based custom service

This feature enables X++ classes to be consumed as JSON services. In other words, the return data set is in JSON format. JSON, which stands for JavaScript Object Notation, is a compact, lightweight format that is commonly used communicate data between the client and the server.

The JSON Endpoint is at `https://host_uri/api/services/service_group_name/service_group_service_name/operation_name`.

**Example**

`https://usnconeboxax1aos.cloud.onebox.dynamics.com/api/services/UserSessionService/AifUserSessionService/GetUserSessionInfo`

Code examples for consuming JSON services are available in the [Microsoft Dynamics AX Integration GitHub repository](https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/ServiceSamples/JsonConsoleApplication).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

