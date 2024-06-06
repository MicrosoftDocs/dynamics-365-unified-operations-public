---
title: Database Movement API - Versioning and support
description: Learn about an overview of the versioning and breaking change policies for the Database Movement application programming interface (API) about versioning and support.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 02/20/2020 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form:
ms.dyn365.ops.version: 10.0.0
---

# Versioning and support

[!include [banner](../../includes/banner.md)]

This article provides an overview of the versioning and breaking change policies for the Database Movement application programming interface (API).

## Support and deprecation information

As new versions of the REST APIs are released, earlier versions will be retired. Microsoft will declare a version deprecated at least six months before it retires an API endpoint.

By incrementing the version number of the API (for example, from v1 to v2), Microsoft announces that the lowest version (in this example, v1) is immediately deprecated and will no longer be supported six months after the announcement. However, Microsoft might make exceptions to this policy for service health and security issues.

When an API is marked as deprecated, a date value will be entered in the **VersionEOL** (Version end of life) field. Therefore, you can proactively monitor this field and plan for upcoming changes.

### Compatible and breaking changes

Microsoft will provide details of API changes in the private preview group. If the changes are non-breaking in nature, the API version number will remain the same. If the changes are breaking in nature, Microsoft will increment the API version number.

Here are some examples of breaking changes:

* The URL or fundamental request/response is changed.
* A declared property is removed or renamed, or its type is changed.
* The API or API parameters are removed or renamed.
* A required request parameter is added.

Here are some examples of non-breaking changes:

* Properties are added that are nullable or have a default value.
* A member is added to an enumeration.
* Paging is introduced to existing collections.
* Error codes are changed.
* The order of properties in requests or responses is changed.

### Example of VersionEOL in a response contract

The following example shows a response contract in JavaScript Object Notation (JSON) format. All response contracts contain the **VersionEOL** property of which has a default value of DateMax() from the Microsoft .NET Framework. Your applications can monitor the value of this field on responses from Microsoft to get an immediate alert when Microsoft has deprecated a specific endpoint or a whole API version.

```json
{
    "IsSuccess": true,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]