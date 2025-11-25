---
title: Matrix planning visual troubleshooting 
description: Learn about some current known issues in the Matrix planning visual in Business performance planning.
author: twheeloc
ms.author: romainpham
ms.topic: overview
ms.date: 11/25/2025
ms.reviewer: twheeloc
ms.collection: get-started

---

# Matrix planning visual troubleshooting

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes some known issues in the Matrix planning visual in Business performance planning.

## The Edit button is unavailable or the visual doesn’t allow write-back
If the **Edit** button isn't available or the visual isn't allowing write-back, check the following common causes.

### Missing fields from one or more cube dimensions
To enable editing, the Matrix visual must include at least one field from every cube dimension. If even one dimension is missing, the **Edit** button remains disabled.

Example:
For example, if your cube includes the dimensions Account, Cost center, Period, and Scenario, but your visual only includes Account and Period, the Matrix renders data but the **Edit** button won’t appear.

**Fix**: Add at least one field (any field) from each dimension to the visual and refresh. Once all dimensions are represented, editing and write-back will be enabled.

### Expired Power BI authentication token
If the Power BI authentication token has expired, the Matrix planning visual can't authenticate to the Business performance planning service.  
When this occurs: the visual may become greyed out, the **Edit** button disappears, and an error message may appear such as **User doesn't have permission to edit data.**

**Fix**:
1. Refresh the browser or Power BI session.  
2. Sign out and sign back in to Power BI to renew your authentication token.  
3. If using Power BI Desktop, close and reopen the file to reauthenticate your session.

If the issue persists:
- Create a new Matrix planning visual from scratch and rebuild the configuration.  
- Or, to preserve your layout and fields:  
  1. Switch the existing visual temporarily to a native Power BI matrix.  
  2. Copy and paste the visual.  
  3. Switch the copied visual back to a Matrix planning visual.  
  This process forces a full metadata refresh and clears any persistent cached references in the visual.
> [!NOTE]
> This issue is often mistaken for missing permissions, but it’s usually caused by an expired token rather than security configuration.

### Format pane options missing
In some cases, when configuring the Matrix planning visual in Power BI, formatting option in the **Format visual your visual**  may disappear or fail to display correctly.  
This can happen if the visual’s local configuration cache becomes outdated after a schema or driver change. 

**Fix**:
- Remove one of the drivers (values) from the visual, then immediately add it back. This forces the visual to refresh its internal cache and repopulate the missing format options.  
- Once the cache refreshes, the full Tab layout configuration options should reappear. If the issue persists after re-adding a driver, save and reopen your report. The visual will rebuild its cached
- schema during initialization.

[!TIP] If the issue persists after re-adding a driver, save and reopen your report. The visual will rebuild its cached schema during initialization.

### Incorrect API URL or cube name
Even if the visual displays data, a typo or misconfiguration in the API URL or cube name can block write-back operations.
Symptoms: 
- The Matrix loads data but can’t enter edit mode.
- Write-back actions return an error or silently fail.
- Logs or pop-up messages may include “An error occurred while executing the operation”, “Cube not found” or “Invalid API endpoint.”

**Fix**:
1. Open the visual’s Advanced settings in Power BI.
2. Verify that the API URL matches your environment’s Business performance planning instance and the Cube name matches exactly the Dataverse cube name (case-sensitive).
3. Correct any typos and refresh the report.
4. If the issue continues: - Recreate the visual or follow the same switch–copy–restore method described above to reset the metadata binding.

### Role or permission mismatch
The users have appropriate Dataverse and Business performance planning security roles to perform write-back but can only view but not edit data.

**Fix**: 
- Ensure the user has the Business performance planning contributor or Business performance planning Admin role.
- Verify the Dataverse table permissions allow Create, Read, Write, and Append for planning tables.
- If using row-level security (RLS), confirm the user’s data slice matches the visual’s filters.

### Comments not available
If the Comment option doesn’t appear in the context menu: 
- The visual might not include the msdyn_name field for all cube dimensions. 
- Comments can only be added at the lowest level of granularity.

**Fix** 
Ensure the Matrix includes the msdyn_name field from each dimension, even if hidden in the visual.

### Performance degradation after large edits
The Matrix visual becomes slow after bulk changes or multi-cell updates.

**Fix**: 
- Use smaller edit batches (for example, update 50–100 cells at a time).
- Reduce the number of subtotals in the visual.
- Refresh the visual after saving to release cached state.






