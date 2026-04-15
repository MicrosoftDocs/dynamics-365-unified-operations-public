---
title: Database Movement API - Versioning and support
description: Learn about an overview of the versioning and breaking change policies for the Database Movement application programming interface (API) about versioning and support.
author: laneswenka
ms.author: laswenka
ms.topic: upgrade-and-migration-article
ms.date: 04/03/2026
ms.custom: 
  - bap-template
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

As Microsoft releases new versions of the REST APIs, it retires earlier versions. Microsoft declares a version deprecated at least six months before it retires an API endpoint.

By incrementing the version number of the API (for example, from v1 to v2), Microsoft announces that the lowest version (in this example, v1) is immediately deprecated and support ends six months after the announcement. However, Microsoft might make exceptions to this policy for service health and security issues.

When Microsoft marks an API as deprecated, it enters a date value in the **VersionEOL** (Version end of life) field. You can proactively monitor this field and plan for upcoming changes.

### Compatible and breaking changes

Microsoft provides details of API changes in the private preview group. If the changes are non-breaking, the API version number stays the same. If the changes are breaking, Microsoft increments the API version number.

Here are some examples of breaking changes:

- The URL or fundamental request or response changes.
- A declared property is removed or renamed, or its type is changed.
- The API or API parameters are removed or renamed.
- A required request parameter is added.

Here are some examples of non-breaking changes:

- Properties are added that are nullable or have a default value.
- A member is added to an enumeration.
- Paging is introduced to existing collections.
- Error codes are changed.
- The order of properties in requests or responses is changed.

### Example of VersionEOL in a response contract

The following example shows a response contract in JavaScript Object Notation (JSON) format. All response contracts contain the **VersionEOL** property, which has a default value of `DateMax()` from the Microsoft .NET Framework. Your applications can monitor the value of this field on responses from Microsoft to get an immediate alert when Microsoft deprecates a specific endpoint or a whole API version.

```json
{
    "IsSuccess": true,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
