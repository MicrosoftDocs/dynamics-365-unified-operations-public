---
title: You can't find the "Workflow" drop-down dialog box for inventory journals
description: You can't find the "Workflow" drop-down dialog box on the journal page, or related workflow operations aren't available
author: sherry-zheng
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.16
---

# You can't find the "Workflow" drop-down dialog box for inventory journals

## Symptoms

You can't find the **Workflow** drop-down dialog box on the journal page, or related workflow operations aren't available.

This issue can occur for three reasons, as described in the following sections.

## Resolution 1

If the issue applies to all users, it might be occurring because the approval workflow hasn't been assigned to the journal name. To fix the issue, follow these steps.

1. Go to **Inventory Management &gt; Setup &gt; Journal names &gt; Inventory**.
1. In the list pane, select a journal name to open its settings.
1. On the **General** FastTab, set the **Approval workflow** option to *Yes*. If you're prompted to confirm the change, select **Yes**.
1. In the **Workflow** field, select the workflow that you want to use for the selected journal name.

## Resolution 2

If your workflow uses customized code, issues might occur after you upgrade the system. For example, in the journal workflow, the **Submit** button might be grayed out so you can't select it to approve a submission.

If the **Submit** button is grayed out, your workflow might have been customized, which means the method of the workflow, `canSubmitToWorkflow()` in `FormDataUtil`, has been extended. To fix this issue, change the way that you extend the method of the `canSubmitToWorkflow()` to use the structure in the following example.

```xpp
[ExtensionOf(formStr(InventJournalMovement))]
public final class InventJournalMovement_extension
{
    public boolean canSubmitToWorkflow()
    {
        boolean ret = YourLogicOfCanSubmitToWorkflow();

        return ret;
    }
}
```

## Resolution 3

If the issue applies only to a few specific users, those users might not have the security privileges that are required to run workflow operations on inventory journals. Verify that each affected user has the *Maintain inventory journal workflow* security privilege. By default, this privilege is assigned to a duty that has same name, and that duty is applied to the *Warehouse worker* and *Warehouse manager* roles.
