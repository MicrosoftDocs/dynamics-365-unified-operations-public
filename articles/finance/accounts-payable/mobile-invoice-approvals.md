---
title: Mobile invoice approvals
description: Learn about a practical approach to designing mobile scenarios by taking vendor invoice approvals for mobile as a use case.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: 
ms.dyn365.ops.version: Version 1611
ms.assetid: 9db38b3f-26b3-436e-8449-7ff243568a18
---

# Mobile invoice approvals

[!include [banner](../includes/banner.md)]

Mobile capabilities let a business user design mobile experiences. For advanced scenarios, the platform also lets developers extend the capabilities as they desire. The most effective way to learn some of the new concepts on mobile is to go through the process of designing a few scenarios. This article provides a practical approach to designing mobile scenarios by taking vendor invoice approvals for mobile as a use case. This article helps you design other variations of the scenarios and can also be applied to other scenarios that aren't related to vendor invoices.

## Prerequisites

| Prerequisite                                  | Description                       |
|---------------------------------------|--------------------------------------------|
| Mobile handbook pre-read  |[Mobile platform](../../fin-ops-core/dev-itpro/mobile-apps/platform/mobile-platform-home-page.md)  |
| Dynamics 365 Finance         |                    |
| An Android, iOS, or Windows device that has the mobile app installed. | Search for the app in the appropriate app store.                            |

## Introduction

Every organization orchestrates and defines its business process for vendor invoices differently. Before you design a mobile experience for vendor invoice approvals, consider the following aspects of the business process. Use these data points to optimize the user experience on the device.

- What fields from the invoice header do users want to see in the mobile experience, and in what order?
- What fields from the invoice lines do users want to see in the mobile experience, and in what order?
- How many invoice lines are there in an invoice? Apply the 80-20 rule, and optimize for the 80 percent.
- Do users want to see accounting distributions (invoice coding) on the mobile device during reviews? If yes, consider the following questions:
  - How many accounting distributions (extended price, sales tax, charges, splits, and so on) are there for an invoice line? Again, apply the 80-20 rule.
  - Do the invoices also have accounting distributions on the invoice header? If so, should these accounting distributions be available on the device?

    > [!NOTE]
    > This article doesn't explain how to edit accounting distributions, because this functionality isn't currently supported for mobile scenarios.

- Do users want to see attachments for the invoice on the device?

The design of the mobile experience for invoice approvals differs, depending on the answers to these questions. The objective is to optimize the user experience for the business process on mobile in an organization. In the rest of this article, you look at two scenario variations that are based on different answers to the preceding questions.

As a general guidance, when working with the mobile designer, make sure to publish the changes to prevent losing the updates.

## Designing a simple invoice approval scenario for Contoso

| Scenario attribute | Answer |
|---|---|
| What fields from the invoice header do users want to see in the mobile experience, and in what order? | 1. Vendor name<br>2. Invoice total<br>3. Invoice account<br>4. Invoice number<br>5. Invoice date<br>6. Invoice description<br>7. Due date<br>8. Invoice currency |
| What fields from the invoice lines do users want to see in the mobile experience, and in what order? | 1. Procurement category<br>2. Quantity<br>3. Unit price<br>4. Line net amount<br>5. 1099 amount |
| How many invoice lines are there in an invoice? Apply the 80-20 rule here, and optimize for the 80 percent. | 1 |
| Do users want to see accounting distributions (invoice coding) on the mobile device during reviews? | Yes |
| How many accounting distributions (extended price, sales tax, charges, and so on) are there for an invoice line? Again, apply the 80-20 rule. | Extended price: 2 Sales tax: 0 Charges: 0 |
| Do the invoices also have accounting distributions on the invoice header? If so, should these accounting distributions be available on the device? | Not used |
| Do users want to see attachments for the invoice on the device? | Yes |

### Create the workspace

1. In a browser, sign in to the application.
1. After you’ve signed in, append **&mode=mobile** to the URL as shown in the following example, and refresh the page: https://&lt;yoururl&gt;/?cmp=usmf&mi=DefaultDashboard**&mode=mobile**
1. Select the **Settings** (gear) button in the upper right of the page, and then select **Mobile app**. The mobile app designer appears just as Task recorder appears.
1. Select **Add** to create a new workspace. For this example, name the workspace **My approvals**.
1. Enter a description.
1. Select a workspace color. The workspace color is used for the overall style of the mobile experience for this workspace.
1. Select an icon for the workspace.
1. Select **Done**.
1. Select **Publish workspace** to save the changes.

### Vendor invoices assigned to me

The first mobile page that you should design is the list of invoices that are assigned to you for review. To design this mobile page, use the **VendMobileInvoiceAssignedToMeListPage** page. Before you complete this procedure, make sure that at least one vendor invoice is assigned to you for review, and that the invoice line has two distributions. This setup meets the requirements for this scenario.

1. In the URL, replace the name of the menu item with **VendMobileInvoiceAssignedToMeListPage** to open the mobile version of the **Pending vendor invoices assigned to me** list page in the **Accounts payable** module. Depending on the number of invoices that you have in your system assigned to you, this page displays those invoices. To find a specific invoice, you can use the filter on the left. However, this example doesn't require a specific invoice. It just requires some invoice assigned to you which is going to allow you to design the mobile page. The new pages that are available are designed specifically for developing mobile scenarios for vendor invoice. Therefore, you must use these pages. The URL should resemble the following URL, and after you enter it, the page that is shown in the illustration must appear: https://&lt;yourURL&gt;/?cmp=usmf&mi=**VendMobileInvoiceAssignedToMeListPage**&mode=mobile

    :::image type="content" source="./media/mobile-invoice-approvals01.png" alt-text="Screenshot of the Pending vendor invoices assigned to me page.":::

1. Select the **Settings** (gear) button in the upper right of the page, and then select **Mobile app**.
1. Select your workspace and select **Edit**.
1. Select **Add page** to create the first mobile page.
1. Enter a name, such as **My vendor invoices**, and a description, such as **Vendor invoices assigned to me for review**.
1. Select **Done**.
1. In the mobile designer, on the **Fields** tab, select **Select fields**. The columns on the list page must resemble the following illustration.

    :::image type="content" source="./media/mobile-invoice-approvals02.png" alt-text="Screenshot of the columns on the Pending vendor invoices assigned to me page.":::

1. Add the required columns from the list page that must be shown to the users in the mobile page. The order in which you add is the order in which the fields are displayed to the end user. The only way to change the ordering of the fields is by re-selecting all the fields. Based on the requirements for this scenario, the following eight fields are required. However, some users might consider eight fields too much information to have on a mobile device. Therefore, show only the most important fields in the mobile list view. The remaining fields appear in the details view that you design later. For now, add the following fields. Select the plus sign (**+**) in these columns to add to the mobile page.
    - Vendor name
    - Invoice total
    - Invoice account
    - Invoice number
    - Invoice date

    After you add the fields, the mobile page must resemble the following illustration.

    :::image type="content" source="./media/mobile-invoice-approvals03.png" alt-text="Screenshot of the page after fields are added.":::

1. Add the following columns so that you can enable workflow actions later.
    - Show complete task
    - Show delegate task
    - Show recall task
    - Show reject task
    - Show request completion task
    - Show resubmit task

1. Select **Done** to exit edit mode.
1. Select **Back** and then **Done** to exit the workspace.
1. Select **Publish workspace** to save your work.
1. Enable **Display invoice total on pending vendor invoices list** in accounts payable parameters form under **Invoice**. When you enable this parameter, invoice totals are calculated to display on the pending vendor invoices list page. 

### Vendor invoice details

To design the invoice details page for mobile, use the **VendMobileInvoiceHeaderDetails** page. Depending on the number of invoices in your system, this page shows the oldest invoice (the invoice that was created first). To find a specific invoice, use the filter on the left. However, this example doesn't require a specific invoice. It just requires some invoice data so that you can design the mobile page.

:::image type="content" source="./media/mobile-invoice-approvals04.png" alt-text="Screenshot of the workflow page.":::

1. In the URL, replace the name of the menu item with **VendMobileInvoiceHeaderDetails** to open the page.

1. Open the mobile designer from the **Settings** (gear) button.

1. Select **Edit** to start edit mode in the workspace.

1. Select the **My vendor invoices** page that you created earlier, and then select **Edit**.

1. On the **Fields** tab, select the **Grid** column heading.

1. Select **Properties &gt; Add page**. **Note:** When you select the **Grid** heading and add a page, you automatically establish the relationship with the details page.

1. Enter a page title, such as **Invoice details**, and a description, such as **View invoice header and line details**.

1. Select **Select fields**. The order in which you add fields is the order in which the fields display to the end user. The only way to change the ordering of the fields is by reselecting all the fields.

1. Add the following fields from the header, based on the requirements for this scenario:
   - Vendor name
   - Invoice total
   - Invoice account
   - Invoice number
   - Invoice date
   - Invoice description
   - Due date
   - Invoice currency

1. Add the following fields from the lines grid on the page:
    - Procurement category
    - Quantity
    - Unit price
    - Line net amount
    - 1099 amount

1. After you add all the fields from the previous two steps, select **Done**. The page must resemble the following illustration.

    :::image type="content" source="./media/mobile-invoice-approvals05.png" alt-text="Screenshot of the page showing additional fields added.":::

1. Select **Done** to exit edit mode.

1. Select **Back** and then **Done** to exit the workspace.

1. Select **Publish workspace** to save your work.

### Workflow actions

To add workflow actions, use the **VendMobileInvoiceHeaderDetails** page. To open this page, replace the name of the menu item in the URL, as you did earlier. Then open the mobile designer from the **Settings** (gear) button. Follow these steps to add workflow actions on the details page. You must have invoices assigned to you that are in the appropriate state to make the workflow actions available to you that you're going to design for.

#### Record workflow actions

1. Select **Edit** to start edit mode in the workspace.
1. Select the **Invoice details** page that you created earlier, and then select **Edit**.
1. On the **Actions** tab, select **Add action**.
1. Enter an action title, such as **Approve**, and a description, such as **Approve invoice**. The action title that you enter here becomes the name of the action that the user sees in the mobile app.
1. Select **Done**.
1. Select **Select fields**.
1. Go through the workflow process on the **VendMobileInvoiceHeaderDetails** page, and complete the action that you want to record. Make sure that you enter workflow comments during this process, so that a comments field is also included in the mobile experience.
1. After the workflow action runs, select **Done** to complete the Select fields task.
1. Select **Done** to exit edit mode.
1. Select **Back** and then **Done** to exit the workspace.
1. Select **Publish workspace** to save your work.
1. Repeat the previous steps to record all the required workflow actions.

#### Create a .js file

1. Open Notepad or Visual Studio, and paste the following code. Save the file as a .js file. This code does the following tasks:
    - It hides the extra workflow-related columns that you added earlier on the mobile list page. You added these columns so that the app has that information in context and can do the next step.
    - Based on the workflow step that is active, it applies logic to show only those actions.

    > [!NOTE]
    > The name of the pages and other controls in the code must be the same as the names in the workspace.

    ```javascript
    function main(metadataService, dataService, cacheService, $q) {
           return {
               appInit: function (appMetadata) {
                   // Hide controls that need to be present, but not visible
                   metadataService.configureControl('My-vendor-invoices', 'ShowAccept', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowApprove', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowReject', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowDelegate', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowRequestChange', { hidden: true });
                 metadataService.configureControl('My-vendor-invoices', 'ShowRecall', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowComplete', { hidden: true });
               metadataService.configureControl('My-vendor-invoices', 'ShowResubmit', { hidden: true });
               },
               pageInit: function (pageMetadata, params) {
        if (pageMetadata.Name == 'Invoice-details') {
                       // Show/hide workflow actions based on workflow step
                       metadataService.configureAction('Accept', { visible: true });
                       metadataService.configureAction('Approve', { visible: true });
                       metadataService.configureAction('Reject', { visible: true });
                       metadataService.configureAction('Delegate', { visible: true });
                       metadataService.configureAction('Request-change', { visible: true });
                       metadataService.configureAction('Recall', { visible: true });
                       metadataService.configureAction('Complete', { visible: true });
                       metadataService.configureAction('Resubmit', { visible: true });

                       var entityContextParts = params.pageContext.split(':');
                       var data = dataService.getEntityData(entityContextParts[0], entityContextParts[1]);

                       var acceptControl = data.getPropertyValue('VendInvoiceInfoTable/showAccept');
                       var approveControl = data.getPropertyValue('VendInvoiceInfoTable/showApprove');
                       var rejectControl = data.getPropertyValue('VendInvoiceInfoTable/showReject');
                       var delegateControl = data.getPropertyValue('VendInvoiceInfoTable/showDelegate');
                       var requestChangeControl = data.getPropertyValue('VendInvoiceInfoTable/showRequestChange');
                       var recallControl = data.getPropertyValue('VendInvoiceInfoTable/showRecall');
                       var completeControl = data.getPropertyValue('VendInvoiceInfoTable/showComplete');
                       var resubmitControl = data.getPropertyValue('VendInvoiceInfoTable/showResubmit');

                       var showAcceptControl = Boolean(acceptControl == 1);
                       var showApproveControl = Boolean(approveControl == 1);
                       var showRejectControl = Boolean(rejectControl == 1);
                      var showDelegateControl = Boolean(delegateControl == 1);
                       var showRequestChangeControl = Boolean(requestChangeControl == 1);
                       var showRecallControl = Boolean(recallControl == 1);
                       var showCompleteControl = Boolean(completeControl == 1);
                       var showResubmitControl = Boolean(resubmitControl == 1);

                       metadataService.configureAction('Accept', { visible: showAcceptControl });
                       metadataService.configureAction('Approve', { visible: showApproveControl });
                       metadataService.configureAction('Reject', { visible: showRejectControl });
                       metadataService.configureAction('Delegate', { visible: showDelegateControl });
                       metadataService.configureAction('Request-change', { visible: showRequestChangeControl });
                       metadataService.configureAction('Recall', { visible: showRecallControl });
                       metadataService.configureAction('Complete', { visible: showCompleteControl });
                     metadataService.configureAction('Resubmit', { visible: showResubmitControl });
                   }
                 },
           };
        }
    ```

1. Upload the code file to the workspace by selecting the **Logic** tab.
1. Select **Done** to exit edit mode.
1. Select **Back** and then **Done** to exit the workspace.
1. Select **Publish workspace** to save your work.

### Vendor invoice attachments

1. Select the **Settings** (gear) button in the upper right of the page, and then select **Mobile app**.

1. Select the **Edit** button to start edit mode in the workspace.

1. Select the **Invoice details** page that you created earlier, and then select **Edit**.

1. Set the **Document management** option to **Yes** as shown in the following image. If there are no requirements to show attachments on the mobile device, leave this option set to **No**, which is the default setting.

   :::image type="content" source="./media/docmanagement-216x300.png" alt-text="Screenshot of the Document management option.":::

1. Select **Done** to exit edit mode.

1. Select **Back** and then **Done** to exit the workspace.

1. Select **Publish workspace** to save your work.

### Vendor invoice line distributions

The requirements for this scenario confirm that there are only line-level distributions, and that an invoice always has only one line. Because this scenario is simple, the user experience on the mobile device is also simple enough that the user doesn't have to drill down several levels to view the distributions. Vendor invoices include the option of showing all distributions from the invoice header. This experience is what you need for the mobile scenario. Therefore, use the **VendMobileInvoiceAllDistributionTree** page to design this part of the mobile scenario.

> [!NOTE]
> Knowing the requirements helps you decide which specific page to use and how exactly to optimize the mobile experience for the user when you design the scenario. In the second scenario, use a different page to show the distributions, because the requirements for that scenario differ.

1. In the URL, replace the name of the menu item, as you did before. The page that appears should resemble the following illustration.

    :::image type="content" source="./media/mobile-invoice-approvals06.png" alt-text="Screenshot of the All distributions page.":::

1. Open the mobile designer from the **Settings** (gear) button.

1. Select **Edit** to start edit mode in the workspace. You see that two new pages are created automatically. The system creates these pages because you turned on document management in the previous section. You can ignore these new pages.

1. Select **Add page**.

1. Enter a page title, such as **View accounting**, and a description, such as **View accounting for the invoice**.

1. Select **Done**.

1. On the **Fields** tab, select **Select fields**, select the following fields from the distributions page, and then select **Done**:
    1. Amount
    1. Currency
    1. Ledger account

    > [!NOTE]
    > Don't select the **Description** column from the distributions grid, because the requirements for this scenario confirm that the extended price is the only amount that has distributions. Therefore, the user doesn't require another field to determine the amount type that the distribution is for. However, in the next scenario, you **will** use this information, because the requirements for that scenario specify that other amount types have distributions (for example, sales tax).

1. Select **Done** to exit edit mode.

1. Select **Back** and then **Done** to exit the workspace.

1. Select **Publish workspace** to save your work.

#### Adding navigation to "View accounting" page

The **View accounting** mobile page isn't currently linked to any of the mobile pages that you designed so far. Because the user should be able to navigate to the **View accounting** page from the **Invoice details** page on the mobile device, you must provide navigation from the **Invoice details** page to the **View accounting** page. Establish this navigation by using additional logic via JavaScript.

1. Open the .js file that you created earlier, and add the lines that are highlighted in the following code. This code does two things:
    1. It helps guarantee that users can't navigate directly from the workspace to the **View accounting** page.
    1. It establishes a navigation control from the **Invoice details** page to the **View accounting** page.

    > [!NOTE]
    > The name of the pages and other controls in the code must be the same as the names in the workspace.

    ```javascript
    function main(metadataService, dataService, cacheService, $q) {
           return {
               appInit: function (appMetadata) {
                   // Hide controls that need to be present, but not visible
                   metadataService.configureControl('My-vendor-invoices', 'ShowAccept', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowApprove', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowReject', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowDelegate', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowRequestChange', { hidden: true });
                 metadataService.configureControl('My-vendor-invoices', 'ShowRecall', { hidden: true });
                   metadataService.configureControl('My-vendor-invoices', 'ShowComplete', { hidden: true });
               metadataService.configureControl('My-vendor-invoices', 'ShowResubmit', { hidden: true });
                   // Hide pages not applicable for root navigation
                   metadataService.hideNavigation('View-accounting');
                   //Link to view accounting
                   metadataService.addLink('Invoice-details', 'View-accounting', 'View-accounting-nav-control', 'View accounting', true);
               },
               pageInit: function (pageMetadata, params) {
        if (pageMetadata.Name == 'Invoice-details') {
                       // Show/hide workflow actions based on workflow step
                       metadataService.configureAction('Accept', { visible: true });
                       metadataService.configureAction('Approve', { visible: true });
                       metadataService.configureAction('Reject', { visible: true });
                       metadataService.configureAction('Delegate', { visible: true });
                       metadataService.configureAction('Request-change', { visible: true });
                       metadataService.configureAction('Recall', { visible: true });
                       metadataService.configureAction('Complete', { visible: true });
                       metadataService.configureAction('Resubmit', { visible: true });

                       var entityContextParts = params.pageContext.split(':');
                       var data = dataService.getEntityData(entityContextParts[0], entityContextParts[1]);

                       var acceptControl = data.getPropertyValue('VendInvoiceInfoTable/showAccept');
                       var approveControl = data.getPropertyValue('VendInvoiceInfoTable/showApprove');
                       var rejectControl = data.getPropertyValue('VendInvoiceInfoTable/showReject');
                       var delegateControl = data.getPropertyValue('VendInvoiceInfoTable/showDelegate');
                       var requestChangeControl = data.getPropertyValue('VendInvoiceInfoTable/showRequestChange');
                       var recallControl = data.getPropertyValue('VendInvoiceInfoTable/showRecall');
                       var completeControl = data.getPropertyValue('VendInvoiceInfoTable/showComplete');
                       var resubmitControl = data.getPropertyValue('VendInvoiceInfoTable/showResubmit');

                       var showAcceptControl = Boolean(acceptControl == 1);
                       var showApproveControl = Boolean(approveControl == 1);
                     var showRejectControl = Boolean(rejectControl == 1);
                       var showDelegateControl = Boolean(delegateControl == 1);
                       var showRequestChangeControl = Boolean(requestChangeControl == 1);
                       var showRecallControl = Boolean(recallControl == 1);
                       var showCompleteControl = Boolean(completeControl == 1);
                       var showResubmitControl = Boolean(resubmitControl == 1);

                       metadataService.configureAction('Accept', { visible: showAcceptControl });
                       metadataService.configureAction('Approve', { visible: showApproveControl });
                       metadataService.configureAction('Reject', { visible: showRejectControl });
                       metadataService.configureAction('Delegate', { visible: showDelegateControl });
                       metadataService.configureAction('Request-change', { visible: showRequestChangeControl });
                       metadataService.configureAction('Recall', { visible: showRecallControl });
                       metadataService.configureAction('Complete', { visible: showCompleteControl });
                       metadataService.configureAction('Resubmit', { visible: showResubmitControl });
        }
                 },
           };
        }
    ```

1. Upload the code file to the workspace by selecting the **Logic** tab to overwrite the previous code.
1. Select **Done** to exit edit mode.
1. Select **Back** and then **Done** to exit the workspace.
1. Select **Publish workspace** to save your work.

### Validation

From your mobile device, open the app, and connect to your instance. Make sure that you sign in to the company where vendor invoices are assigned to you for review. You should be able to perform the following actions:

- See the **My approvals** workspace.
- Drill into the **My approvals** workspace and see the **My vendor invoices** page.
- Drill into the **My vendor invoices** page and see the list of invoices that are assigned to you.
- Drill into one of the invoices, and see the invoice header details and line details.
- On the details page, see a link to attachments, and use this link to navigate to the attachments list and view the attachments.
- On the details page, see a link to the **View accounting** page, and use this link to navigate to the distributions page and view the distributions.
- On the details page, click the **Actions** menu at the bottom, and perform workflow actions that are applicable to the workflow step.

## Designing a complex invoice approval scenario for Fabrikam

| Scenario attribute | Answer |
|---|---|
| What fields from the invoice header do users want to see in the mobile experience, and in what order? | 1. Vendor name<br>2. Invoice amount<br>3. Invoice account<br>4. Invoice number<br>5. Invoice date<br>6. Invoice description<br>7. Due date<br>8. Invoice currency |
| What fields from the invoice lines do users want to see in the mobile experience, and in what order? | 1. Procurement category<br>2. Quantity<br>3. Unit price<br>4. Line net amount<br>5. 1099 amount |
| How many invoice lines are there in an invoice? Apply the 80-20 rule here, and optimize for the 80 percent. | 5 |
| Do users want to see accounting distributions (invoice coding) on the mobile device during reviews? | Yes |
| How many accounting distributions (extended price, sales tax, charges, and so on) are there for an invoice line? Again, apply the 80-20 rule. | Extended price: 2 Sales tax: 2 Charges: 2 |
| Do the invoices also have accounting distributions on the invoice header? If so, should these accounting distributions be available on the device? | Not used |
| Do users want to see attachments for the invoice on the device? | Yes |

### Next steps

Use this section to improve your mobile app experience.

1. Because you expect more invoice lines in the second scenario, make the following changes to the design to help optimize the user experience on the mobile device:
    1. Instead of viewing invoice lines on the details page, users can choose to view lines on a separate mobile page.
    1. Because you expect more than one invoice line, if you use the **VendMobileInvoiceAllDistributionTree** page to design the distributions page for mobile, it might be confusing for the user to correlate lines to distributions. Therefore, use the **VendMobileInvoiceLineDistributionTree** page to design the distributions page.
    1. Ideally, the distributions should be shown in the context of an invoice line. Therefore, make sure that the user can drill into a line to see the distributions page. Use the page link capability to establish the drill-through, just as you did for the header and details pages in scenario 1.

1. Because you expect more than one amount type on the distributions in second scenario, it is useful to show the description of the amount type. 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
