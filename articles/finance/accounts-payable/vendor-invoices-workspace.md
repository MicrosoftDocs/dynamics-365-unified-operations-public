---
title: Vendor invoice automation workspace
description: Learn about how to set up the workspace that is related to vendor invoices and that shows the information that is available through Microsoft Power BI.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 02/14/2022
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09-21
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
---

# Vendor invoice automation workspace

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article explains how to set up the workspace that is related to vendor invoices and that shows the information that is available through Microsoft Power BI. The vendor invoice information in this workspace is filtered for specific users and is shown in a graphical format.

## Overview

The **Vendor invoice automation** workspace shows information that is related to vendor invoice processing. It includes a **My work** view and an **Analytics - All companies** page. The **My work** view shows summary tiles, vendor transaction grids, and related vendor information. The **Analytics - All companies** page uses the capabilities of Power BI to show visualizations that are related to vendor invoices.

## Set up the workspace to show Power BI content

You must complete this setup before data can be shown in Power BI visualizations in the **Vendor invoice automation** workspace.

1. In the **Feature management** workspace, filter the list to find the **Vendor invoice automation** feature.
3. Select **Enable now**.
4. To ensure that invoices can be processed from beginning to end without requiring manual intervention, set up a vendor invoice workflow. To set up a workflow, go to **Accounts payable \> Setup \> Accounts payable workflows**.
5. Go to **Accounts payable \> Setup \> Accounts payable parameters**, and select the **Vendor invoice automation** tab. For more information, see [Setup options for vendor invoice automation](vnd-invoice-set-up-options.md).
6. Set the **Automatically submit imported invoices to workflow** option to **Yes**.
7. If product receipts should automatically be matched, set the **Automatically match product receipts to invoices lines** option to **Yes**.
8. Review the remaining, optional settings, and configure them according to your organization's requirements.
9. Go to **System administration \> Setup \> System parameters**, and set the **System currency** and **System exchange rate** fields.
10. Go to **General ledger \> Setup \> Ledger**, and set the **Accounting currency** and **Exchange rate type** fields.
11. Go to **General ledger \> Currencies \> Currency exchange rates**, and enter the exchange rates between the transaction currency and the accounting currency, and between the accounting currency and the system currency.
12. Go to **System administration \> Setup \> Entity store**, and look for **Vendor invoice automation measure**. Select **Refresh**.

To view the information that displayed in the workspace, you must have the Accounts payable manager or Accounts payable clerk security role.

## My work view

### Company selection

When the **Vendor invoice automation** feature is turned on, a **Company** field appears at the top of the workspace. The selection in the **Company** field affects all the information displayed in the workspace. By default, the view shows information for the company that you signed in to. By selecting a different company in the **Company** field, you can show information for that company on the workspace. You can then select a tile in the workspace to go the related page in the selected company.

### Summary tiles

The tiles in the **Summary of pending invoices** section of the **My work** view give an overview of the state of your vendor invoices. You can see journals that aren't yet posted and invoices that are on hold. In addition, there are the four tiles that are associated with the Vendor invoice automation feature:

- **Manual receipt match needed**
- **Matching validation not successful**
- **Invoices not submitted to workflow**
- **Invoices not imported**

(These four tiles require that the Vendor invoice automation feature be turned on in **Feature management**.)

To use the **Recover vendor invoices** tile, the feature must be turned on in **Accounts payable parameters**. Go to **Accounts payable \> Accounts payable parameters**, and then, on the **Invoice** tab, set the **Allow vendor invoice recovery** option to **Yes**.

When the feature is turned on, you will also three tiles grouped together on the workspace in a section called **Journals**. The tiles are titled **Journals**, **Journals - Assigned to me**, and **Invoice pool**. 

The information in the **Summary of pending invoices** section is for the company that is set as the default company for your sign-in.

### Creating new records

To create a new invoice record, select **New**, and then select one of the following record types in the list:

- Vendor invoice
- Invoice journal
- Global invoice journal
- Invoice register
- Invoice approval

Note that the record that you create is based on the company filter, not the company that you're signed in to. For example, you're signed in to the **UMSF** company, but the company filter is set to **GBSI**. In this case, when you select **New** and then select a record type in the list, the record is created in the GBSI company.

### Documents not invoiced grids

The **Documents not invoiced** section contains grids that show documents that are awaiting vendor invoices.

The **Open purchase orders** grid shows all purchase orders that aren't yet fully invoiced. You can use the **Invoice now** button to create a vendor invoice for a purchase order. You can use the **Prepayment invoice now** button to create a prepayment invoice for a purchase order.

The **Product receipts** grid shows purchase receipt transactions that aren't yet fully invoiced. You can use the **Invoice now** button to create a vendor invoice for a purchase order.

The **Pending vendor invoices** grid shows all vendor invoices that haven't been submitted to the workflow system. You can use the **Search** field and/or the company filter to search for a specific vendor invoice. You can use the **Edit** button to edit a transaction that appears in the grid.

On the **Find purchase order** grid, you can use the **Search** field to search for a specific purchase order.

### Related information

You can view information about posted invoices by using the links on the right side of the workspace. These links include **Open vendor invoices**, **Invoice journal**, and **Invoice history and matching details**. In the **Vendors** section, you can access a filtered list that shows all vendors that are on hold, or you can use the **All vendors** link. **All purchase orders** and **Open prepayments** links are also available.

### Analytics – All companies page

When the **Automatically submit imported invoices to workflow** option is set to **Yes** on the **Accounts payable parameters** page, you can view automation analytics. The **Analytics - All companies** page provides important metrics, such as vendor invoices that are in approval by approver and by company. This page contains five report pages. One page provides an overview, and the other pages provide details about Accounts payable automation metrics.

The following table shows the visualizations that are available on each report page.

| Report page                    | Visualizations |
|--------------------------------|----------------|
| Vendor invoice overview        | <ul><li>Pending vendor invoices in automation in system currency</li><li>Invoices that failed to import</li><li>Invoices in workflow</li><li>Touchless invoices last 30 days</li><li>Total automated invoices last 30 days</li><li>Balance of open invoices in system currency</li><li>Reasons for failures, last 30 days</li><li>Percent of posted invoices that were processed automatically</li><li>Days to process an invoice</ul></li> |
| Automation status              | <ul><li>Touchless invoices last 30 days</li><li>Touchless invoices last 30 days by company</li><li>Touchless invoices last 30 days by vendor group</li><li>Percent of posted invoices that were processed automatically</li><li>Days to process an invoice</li></ul> |
| Invoices that failed to import | <ul><li>Invoices that failed to import</li><li>Invoices that failed to import by company</li></ul> |
| Reasons for automation failure | <ul><li>Invoices failed</li><li>Invoices failed by company</li><li>Invoices failed by vendor group</li></ul> |
| Workflow status                | <ul><li>Invoices in workflow</li><li>Vendor invoice workflow instances</li><li>Assignment per approver</li><li>Vendor invoice workflow per company</li><li>Average days in workflow by approver</li></ul> |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
