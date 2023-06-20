---
# required metadata

title: Invoice capture solution configuration groups
description: This article provides general information about configuration groups in the Invoice capture solution.
author: sunfzam
ms.date: 06/19/2023
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


Admins can manage the list of invoice fields and the manual review settings by using configuration groups. Users can assign the configuration groups to different legal entities or different vendors. All the legal entities in the same configuration group will display the same invoice fields and use the same manual review setting.

## What is a configuration group?

Invoices received from various suppliers are in different styles and resolutions. These invoices may require different confidence score thresholds to determine if further review is needed to confirm the recognized invoice context.

Typically, invoices from a single supplier are in a consistent format with a specific type of invoice (a purchase order invoice or a cost invoice). There may be cases where a single supplier sends invoices of different types, it might be necessary to define separate display fields for each invoice type. The application applies different derivations and mapping logic specific to each invoice type to ensure accuracy and completeness of the invoice data. The mandatory flag helps Admins ensure values exist on the fields that require values. 
=======
Administrators can manage the list of invoice fields and the manual review settings by using configuration groups. Users can assign configurations to different legal entities or different vendors. All the legal entities in the same configuration group use the same invoice fields and manual review setting.

## What is a configuration group?

Invoices that are received from various suppliers are in different styles and resolutions. These invoices might require different confidence score thresholds to determine whether further review is needed to confirm the recognized invoice context.

Typically, invoices from a single supplier are in a consistent format and are a specific type of invoice, such as a purchase order invoice or a cost invoice. However, in cases where a single supplier sends invoices of different types, it might be necessary to define separate display fields for each invoice type. The application applies different derivations and mapping logic that are specific to each type of invoice to ensure accuracy and completeness of the invoice data.


The configuration group incorporates all the necessary settings for the review process in Invoice capture.

## Default configuration group

After deployment, a default configuration group (**Default configuration**) is created. This configuration group can't be changed or deleted.


Admins can assign different configuration groups to different levels (vendor account, legal entity and system). After a vendor account and legal entity are determined, the application will check whether an existing configuration group is assigned to the vendor first. If no configuration group is found, the legal entity will be checked. If no configuration group is assigned to either the vendor and the legal entity, the configuration group that's specified in **System preferences** is used. 


## Manage configuration groups

To manage configuration groups, go to **Setup**, and select **System setup \> Define configuration groups component**.

To create a new configuration group, select a configuration group, and then select **Copy**. A new configuration group is created by duplicating the existing group. The new configuration group appears in the **Configuration group** list view. It has all the same values as the original configuration group except in the **Group name** and **Group description** fields.

### Define the confidence score

Admins can define the quality standard for the invoice date recognized by AI Builder. When the recognition is completed, structured invoice data and the corresponding confidence score for each field on the invoice are sent from AI Builder. The confidence score on each recognized field indicates confidence about the accuracy for the returned result. For more information about confidence scores, see [Confidence score](/azure/applied-ai-services/form-recognizer/concept-accuracy-confidence?view=form-recog-3.0.0#confidence-scores). The range of confidence scores in Invoice capture is interpreted from 0 to 100. A higher score means AI Builder has more confidence in the recognized result. Admins can configure the threshold of confidence scores to indicate different severity of message. The low confidence message will display in the side-by-side viewer. 

### Define whether manual review is required before invoice creation

Admins define if a manual review is required for each recognized invoice, based on the severity of the issues (warnings or errors). 
In the default configuration group, a manual review is only required when there are errors. If there are no errors during the Invoice capture process, the invoice will be automatically transferred from invoice capture to Dynamics 365 Finance and Operations. The parameter influences the touchless rate for invoice process in Invoice capture. 


### Supported invoice types

In Invoice capture, there are different invoice types for incoming invoices. The invoice type determines several details:

- It determines the validation logic that's used to ensure the completeness and correctness of invoices in Invoice capture.
- It determines the invoice fields (on the header or lines) that are shown in the side-by-side viewer.
- Together with the setting in Dynamics 365 Finance, it determines the data entity API that's called on the recipient side (by using the pending vendor invoice or invoice journal).

There are three invoice types in Invoice capture:

- **PO invoice** – Invoices of this type are associated with purchase orders. The purchase order details must be determined on each invoice line. Both the header and the lines must be reviewed in Invoice capture.
- **Header-only** – Invoices of this type are associated with purchase orders. The purchase order field on the invoice header is a mandatory field. If the **Automatically create invoice lines** feature is enabled, the invoice lines are automatically created from the purchase order in Finance, and users don't have to review the line details in Invoice capture. In addition, the line details aren't shown in the side-by-side viewer.
- **Cost invoice** – Invoices of this type contain non-stock items. Those items can be either service items or procurement category items.

Admins can create a configuration group, select the supported invoice type, and assign the configuration group to the vendor level. This approach increases the touchless rate of invoice processing in Invoice capture.

### Define the control of invoice fields

For each invoice type, different fields can be selected to appear in the side-by-side view, default fields can be added or removed, and fields can be set as mandatory.
