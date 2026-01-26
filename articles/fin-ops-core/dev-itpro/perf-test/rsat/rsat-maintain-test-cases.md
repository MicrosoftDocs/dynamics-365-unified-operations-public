---
title: Maintain test cases in Regression suite automation tool (RSAT)
description: Learn about how to maintain test cases and attachments in Regression suite automation tool (RSAT), including an overview on viewing test case information.
author: FrankDahl
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-04-12
ms.dyn365.ops.version: AX 7.0.0
---

# Maintain test cases in Regression suite automation tool (RSAT)

[!include [banner](../../includes/banner.md)]

Regression suite automation tool (RSAT) lets you maintain test cases and attachments in the tool itself. In earlier versions, you had to use Microsoft Azure DevOps to maintain test cases and then switch to RSAT to run tests. Therefore, newer versions offer better usability and help improve productivity. Many operations can be done completely in RSAT, and it's also easier to work with test suites.

You continue to maintain test plans and test suites in Azure DevOps.

To use this feature, enable the **Enable upload to Azure DevOps** option. RSAT automatically uploads changes to Azure DevOps. Therefore, test suites include the updated test cases that other users can access or that a pipeline can run in Azure DevOps.

## View test case information

Follow these steps to view information about a test case.

- In the **Test Cases** grid, find the relevant test case, and select it by selecting the check mark column. Then select the **Edit** action to open the test case information.

    :::image type="content" source="media/test-case-details2.png" alt-text="Screenshot of the Edit button.":::

  The **Test Case information** dialog box appears.

    :::image type="content" source="media/test-case-information.png" alt-text="Screenshot of the Test Case information dialog box.":::

The **Test Case information** dialog box shows the following information about the test case:

+ The name that you assign to the test case in the test suite appears at the top of the dialog box and can be changed.
+ The recording name appears under the test case name. This name comes from the recording XML file that you use when you make the recording in Task Recorder in the finance and operations app or by using the point of sale (POS) client.
+ The **Attachments** grid shows the list of attachment files that are available with the test case. You can also find this list by using the **Directory** action under the attachments subfolder.

## Create a test case that has attachments

Follow these steps to add a new test case by using RSAT.

1. Select the test suite that you want to add a new test case to (**Procure to Pay – v2** in this example). Then select **New** to open the **Test Case information** dialog box.

    :::image type="content" source="media/test-case-add.png" alt-text="Screenshot of the New button.":::

1. Enter the name of the test case, and add attachment files. These files include the recording XML file that contains steps for the test case. To add attachment files, select **Add**, and then, in the dialog box that appears, select the files to add as attachments.
1. When you're finished, select **Save** to save the new test case or **Cancel** to discard it.

    :::image type="content" source="media/add-test-case.png" alt-text="Screenshot of the Add and Save buttons.":::

When you save a new test case, RSAT copies the attachment files that you selected into your local RSAT working directory. It maintains the copies there so that they can be used with the test case.

There's no feature that automatically clones test cases from one test suite to another. However, you can manually clone test cases by following these steps.

1. Create a test case as described in the previous procedure. As part of this step, add the recording XML file.
1. Save the new test case, and make a note of the **CaseID** value that is assigned to it.
1. You can add a parameter Excel file to the new test case. However, the file name must match the new **CaseID** value. Copy the parameter Excel file from the test case that you're cloning, and change the file name of the copy so that it matches the new **CaseID** value.
1. Open the new parameter Excel file, and change all instances of the old **CaseID** value to the new **CaseID** value.
1. After updating the new parameter Excel file, add it to the new test case as an attachment.

You can generate a parameter Excel file for the new test case first, and then manually edit it so that it matches the parameter Excel file of the test case that you're cloning.

## Remove an attachment from a test case

Remove attachments from a test case when you no longer need them.

- In the **Test Case information** dialog box, select and hold (or right-click) the row for the attachment file, and then select **Remove**.

    :::image type="content" source="media/remove-attachment.png" alt-text="Screenshot of the Remove button.":::

You can also use this procedure if you edited the recording XML file and you want to upload the new version to the test case. In this case, first remove the existing file and then add the new file.

## Delete a test case

Follow these steps to delete a test case.

1. In the **Test Cases** grid, find the test case. Select it by selecting the check mark column. Then select the **Delete** action to delete the test case.

   :::image type="content" source="media/delete-test-case.png" alt-text="Screenshot of the Delete button.":::

1. A message box prompts you to confirm that the test case should be deleted. Confirm the deletion by selecting **Yes**, or cancel it by selecting **No**.

    :::image type="content" source="media/confirm-delete-test-case.png" alt-text="Screenshot of the Confirmation message box for the Delete command.":::

When you delete a test case in RSAT, you remove it from the current test suite, both locally and in Azure DevOps.

In Azure DevOps, work items represent test cases, and test suites contain links to the test case work items. You reuse a test case by linking to it from more than one test suite. When you delete a test case in RSAT, RSAT determines whether the test case is linked to one test suite or more than one test suite. If the test case is used only by the current test suite, RSAT deletes the Azure DevOps work item that represents the test case. If the test case is used by other test suites, RSAT doesn't delete the work item itself. Instead, it deletes only the link to the work item.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

