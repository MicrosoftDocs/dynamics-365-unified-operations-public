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
ms.collection: get-started
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

Admin can manage the list of invoice fields and the manual review settings by using configuration groups. Users can assign the configuration groups to different legal entities or different vendors. All the legal entities in the same configuration group display the same invoice fields and use the same manual review setting.

## What is a configuration group?

Invoices received from various suppliers are in different styles and resolutions. These invoices may require different confidence score thresholds to determine if further review is needed to confirm the recognized invoice context.

Typically, invoices from a single supplier are in a consistent format with a specific type of invoice (a purchase order invoice or a cost invoice). There may be cases where a single supplier sends invoices of different types, it might be necessary to define separate display fields for each invoice type. The application applies different derivations and mapping logic specific to each invoice type to ensure accuracy and completeness of the invoice data. The mandatory flag will help Admin to ensure the value does exist on the fields which requires values. 

The configuration group incorporates all the necessary settings for the review process in Invoice capture.

## Default configuration group

After deployment, a default configuration group (**Default configuration**) is created. This configuration group can't be changed or deleted.

Admin can assign different configuration groups to different levels (vendor account, legal entity and system). After a vendor account and legal entity are determined, the application will check whether an existing configuration group is assigned to the vendor first. If no configuration group is found, the system will check on the legal entity level. If no configuration group is assigned to both the vendor and the legal entity, the configuration group that's specified in **System preferences** will be used. 

## Manage configuration groups

To manage configuration groups, go to **Setup**, and select **System setup \> Define configuration groups component**.

To create a new configuration group, select a configuration group and click **Copy**. You can create a new configuration group by duplicating an existing group. The new group has the same values as the original group for all fields except **Group name** and **Group description**. After the configuration group is duplicated, it will display in the **Configuration group** list view. 

### Define the confidence score
Admin can define the quality standard for the invoice date recognized by AI Builder. When the recognition is completed, structured invoice data and the corresponding confidence score for each field on the invoice are sent from AI Builder. The [confidence score](https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/concept-accuracy-confidence?view=form-recog-3.0.0#confidence-scores) on each recognized field indicates confidence about the accuracy for the returned result. The value range of confidence score in Invoice capture is interpreted from 0 to 100. A higher score means AI Builder has more confidence in the recognized result. Admin can configure the threshold of confidence scores to indicate different severity of message. The low confidence error/warning message will pop in the side-by-side viewer. 

### Define whether manual review is required before invoice creation

Admin can define whether a manual review is required for each recognized invoice, based on the severity of the issues (warnings or errors). 
In default configuration group, it is defined that manual review is only required when there are errors. This means that if there is no error during the process in Invoice capture, the invoice will be automatically transferred from invoice capture to Dynamics 365 Finance and Operations.  
The parameter will influence the touchless rate for invoice process in Invoice capture. 

### Supported invoice types

In Invoice capture, there are different invoice types for incoming invoices. The invoice type determines several details:

- It determines the validation logic that's used to ensure the completeness and correctness of invoices in Invoice capture.
- It determines the invoice fields (on the header or lines) that are shown in the side-by-side viewer.
- Together with the setting in Dynamics 365 Finance, it determines the data entity API that's called on the recipient side (by using the pending vendor invoice or invoice journal).

There are three invoice types in Invoice capture:

- **PO invoice** – Invoices of this type are associated with purchase orders. The purchase order details must be determined on each invoice line. Both the header and the lines must be reviewed in Invoice capture.
- **Header-only** – Invoices of this type are associated with purchase orders. The purchase order field on the invoice header is a mandatory field. If the **Automatically create invoice lines** feature is enabled, the invoice lines are automatically created from the purchase order in Finance, and users don't have to review the line details in Invoice capture. In addition, the line details aren't shown in the side-by-side viewer.
- **Cost invoice** – Invoices of this type contain non-stock items. Those items can be either service items or procurement category items.

Admin can create a configuration group, select the supported invoice type, and assign the configuration group to the vendor level. This approach increases the touchless rate of invoice processing in Invoice capture.

### Define the control of invoice fields

For each invoice type, different fields can be selected to appear in the side-by-side view, default fields can be added or removed, and fields can be set as mandatory.


