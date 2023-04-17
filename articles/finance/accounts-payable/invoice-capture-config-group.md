---
# required metadata

title: Invoice capture solution configuration groups
description: This article provides general information about configuration groups in the Invoice capture solution.
author: sunfzam
ms.date: 04/4/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution configuration groups

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Users can manage the list of invoice fields and the manual review setting for legal entities by using configuration groups. Users can set up invoice configurations for different legal entities in groups. All the legal entities in the same configuration group use the same invoice fields and manual review setting.

## What is a configuration group?

Invoices received from various suppliers often come in different styles and resolutions, which may require various confidence score thresholds to determine whether further review is needed to ensure accurate recognition. 

Typically, invoices from a single supplier are in a consistent format with a specific type of invoice, such as a purchase order invoice or a cost invoice. However, there may be cases where a single supplier sends invoices of different types. In such cases, it is necessary to define separate display fields for each invoice type. The application applies different derivation and mapping logic specific to each type of invoice to ensure accuracy and completeness of the invoice data.

Configuration group is working on incorporating all the necessary settings to effectively determine how to process the invoice in the Invoice capture staging, taking into consideration the review condition, different types of invoices etc.

## Default configuration group

After deployment, a default configuration group (**Default configuration**) is created. This configuration group can't be changed or deleted.

Accounts payable administrators can assign different configuration groups to the vendor, legal entity, and system. After a vendor account and legal entity are determined, system will check whether an existing configuration group is assigned to the vendor. If no configuration group is found, system will check on the legal entity level. If no configuration group assigned to the vendor or the legal entity, the system-level configuration group that's specified in **System preferences** is used.

## Manage configuration groups

To manage configuration groups, go to **Setup**, and select **System setup \> Define configuration groups component**.

To create a new configuration group, select a configuration group and click **Copy**. You can create a new configuration group by duplicating an existing group. The new group has the same values as the original group for all fields except **Group name** and **Group description**. After the configuration group is duplicated, it will be shown in the configuration group list view. 

### Define the confidence score of invoice recognition

Users can define the quality standard that's required for AI Builder to recognize invoice data. When the recognition is completed, structured invoice data and the corresponding confidence score for each field on the invoice are sent from AI Builder. You can configure the threshold of confidence scores to indicate different severities of the messages.

### Define whether manual review is required before invoice creation

You can define whether a manual review is required for each recognized invoice, based on the severity of the issues (warnings or errors).

### Supported invoice types

In Invoice capture, there are different invoice types for incoming invoices. The invoice type determines several details:

- It determines the validation logic that's used to ensure the completeness and correctness of invoices in Invoice capture.
- It determines the invoice fields (on the header or lines) that are shown in the side-by-side viewer.
- Together with the setting in Dynamics 365 Finance, it determines the data entity API that's called on the recipient side (by using the pending vendor invoice or invoice journal).

There are three invoice types in Invoice capture:

- **PO invoice** – Invoices of this type are associated with purchase orders. The purchase order details must be determined on each invoice line. Both the header and the lines must be reviewed in Invoice capture.
- **Header-only** – Invoices of this type are associated with purchase orders. The purchase order field on the invoice header is a mandatory field. If the **Automatically create invoice lines** feature is enabled, the invoice lines are automatically created from the purchase order in Finance, and users don't have to review the line details in Invoice capture. In addition, the line details aren't shown in the side-by-side viewer.
- **Cost invoice** – Invoices of this type contain non-stock items. Those items can be either service items or procurement category items.

The Accounts payable administrator can create a configuration group, select the supported invoice type, and assign the configuration group to the vendor level. This approach increases the touchless rate of invoice processing in Invoice capture.

### Define the control of invoice fields

For each invoice type, different fields can be selected to appear in the side-by-side view, default fields can be added or removed, and fields can be set as mandatory.


