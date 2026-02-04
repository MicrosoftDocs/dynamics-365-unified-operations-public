---
title: Delete Globalization features
description: Learn how to delete a Globalization feature.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 02/04/2026
ms.custom: 
ms.reviewer: 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2026-01-29
ms.search.form:
ms.dyn365.ops.version: 10.0.39
---

# Delete Globalization features

[!INCLUDE[banner](../../includes/banner.md)]

You can delete an Electronic invoicing feature. 

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
2. Select the feature you want to delete from the feature list.
3. Click the **Delete** button. The **Delete** button is located in the workspace toolbar and is only enabled when deletion is allowed for the selected feature.
4. Confirm the deletion when prompted.

> [!NOTE]
> If you attempt to delete a feature with deployed versions, you will receive the following error: `Feature cannot be deleted as it has deployed version. Undeploy version and retry`.
 
## Additional Considerations
 
### Feature Relationships
 
Consider the following before deleting a feature:
 
**Derived Features**: If other features are derived from (inherit from) the feature you want to delete, check if those relationships will be affected.
   - Features can have a base feature relationship tracked in the `Base` field.
 
**Active Provider**: You can only delete features owned by the active configuration provider.
   - The active provider is set in the ER parameters.
 
**Draft Versions**: Features with only draft versions (not deployed) can be deleted freely.
 
### Best Practices
 
1. **Check Dependencies**: Before deleting, verify that no other features depend on this feature as a base
2. **Export Configuration**: Consider exporting the feature configuration to JSON as a backup before deletion
3. **Verify Deployments**: Always double-check that all deployments have been properly removed
