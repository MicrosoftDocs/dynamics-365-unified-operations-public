---
title: Troubleshoot issues related to solution awareness
description: Learn about how you can fix issues that are related to solution awareness, including issues involving error messages on the dual-write page.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: article
ms.date: 03/16/2020
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-06
---

# Troubleshoot issues related to solution awareness

[!include [banner](../../includes/banner.md)]





This article provides troubleshooting information for dual-write integration between finance and operations apps and Dataverse. Specifically, it provides information that can help you fix issues that are related to solution awareness.

> [!IMPORTANT]
> Some of the issues that this article addresses might require either the system admin role or Microsoft Microsoft Entra tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## Error on the Dual-write page

On the **Dual-write** page, you might receive an error message that resembles the following example:

*The entity with a name 'msdyn\_dualwriteentitymap' with namemapping='Logical' was not found in the MetadataCache.*

To fix the issue, make sure that the dual-write core solution is installed in Dataverse. The dual-write core solution is a prerequisite for solution awareness.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]