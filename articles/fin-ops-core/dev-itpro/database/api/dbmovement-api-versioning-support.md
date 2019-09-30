---
# required metadata

title: Database movement API - Versioning and support
description: This topic provides an overview of the versioning and breaking change policies for Database Movement API. 
author: laneswenka
manager: AnnBe
ms.date: 09/30/2019
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
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.0

---

# Versioning and support

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

This topic provides an overview of the versioning and breaking change policies for the Database Movement API.

## Support and deprecation information
As new versions of the REST APIs are released, earlier versions will be retired.  Microsoft will declare a version as deprecated at least 6 months in advance of retiring an API endpoint.  

When we increment the version of the API (for example, from v1 to v2), we are announcing that the lowest version (in this example, v1) is immediately deprecated and we will no longer support it 6 months after the announcement.  We may take exceptions to this policy for service health and security issues.

When an API is marked as deprecated, the **VersionEOL** or Version End-of-Life field will have the end date value populated.  This allows you to proactively monitor this field for a non-date-maximum value and to plan for the upcoming changes.  

### Compatible and breaking changes
Microsoft will continue to detail the API changes in the [What's new](something.md) article.  If the changes are non-breaking then we will maintain the same version number.  If the changes are breaking in nature, we will increment the API version.

The following are examples of a breaking change:
* Change to the URL or fundamental request/response 
* Removal, rename, or change of the type of a declared property
* Removal or rename of the API or API parameters
* Addition of a required request parameter

The following are examples of non-breaking changes:
* Addition of properties which are nullable or have a default value
* Addition of a member to an enumeration
* Introduction of paging to existing collections
* Changes to error codes
* Changes to the order of properties in request/response

### Example of VersionEOL in a response contract
Below you will find a response contract in JSON.  All response contracts contain the **VersionEOL** property of which defaults to DateMax() in .NET.  Your applications can monitor the value of this field on our responses to get an immediate alert when we have deprecated a particular endpoint or an entire API version.

```json
{
    "IsSuccess": true,

    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",

    "ErrorMessage": null,

    "VersionEOL": "9999-12-31T23:59:59.9999999"

}
```
