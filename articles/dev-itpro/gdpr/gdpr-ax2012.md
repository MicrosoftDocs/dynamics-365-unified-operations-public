---
# required metadata

title: Respond to a DSR request from Microsoft Dynamics AX 2012
description: This topic describes how you, as a data controller, can use Microsoft Dynamics AX 2012 as a data processor to help you respond to a request for data under the European Union's General Data Protection Regulation (GDPR).
author: ryanc
manager: AnnBe
ms.date: 12/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 10031
ms.search.region: Global
# ms.search.industry: 
ms.author: ryanc
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.0.0
---


# Respond to a DSR request from Microsoft Dynamics AX 2012

[!include[banner](../includes/banner.md)]

This topic can help businesses that use Microsoft Dynamics AX 2012, and also partners and independent software vendors (ISVs), when they comply with data subject rights (DSR) requests. For more information about the European Union's General Data Protection Regulation (GDPR) and the related resources that Microsoft provides, see [Guide to the GDPR for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition](./gdpr-guide.md). Although that topic was written for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, much of the information also applies to AX 2012. This topic lists additional points that are specific to AX 2012. 

Data subjects have the following rights under the GDPR, and a data controller might take any of the actions that are listed under each right in response to a DSR request. 

## Rights

+ **Right to view**
    + Use the built in search capabilities to find information for a request to view data.
    + Author specific reports that contain information that is included in a request and that can be quickly generated in response to a customer request.  
    + Use provided data inventory docuementation to locate data that may be considered personal data.
    + For example reports, see the list at the end of this topic.
    
+ **Right to modify**
    + Use the built in search capabilities to find information for that is the subject of the modification request.
    + Author specific reports that contain personal data that can be quickly generated in response to a customer request and be used to identify data included in a correction request.
    + For example reports, see the list at the end of this topic.
    + Modify personal data directly in the product, where the capability exists.

The GDPR is not a law exclusive of all other laws. AX 2012 (R1, R2, R3) Is an enterprise resource planning system, and does not allow for modification of certain business or transactional data, and will not endorse nor provide functionality for the modification of business data that is necessary for compliance with other laws or certifications. AX 2012 will not provide support for modifications/customizations or other actions that result in the corruption of referential or business data integrity. 

+ **Right to be forgotten**, which might be expressed as the right to have data deleted

    + Delete or anoymize data where the ability is provided in the product.
    
The GDPR is not a law exclusive of all other laws. AX 2012 (R1, R2, R3) Is an enterprise resource planning system, and does not allow for deletion of certain business or transactional data, and will not endorse nor provide functionality for the deletion of business data that is necessary for compliance with other laws or certifications. AX 2012 will not provide support for modifications/customizations or other actions. that result in the corruption of referential or business data integrity. 

+ **Right to port**

    + For AX 2012 versions, extensive reporting options are available for finding and exporting customer data at the customer's request. See the "Additional resources" section for example reports that can be exported to various data formats, such as Microsoft Excel, Microsoft Word, and PDF. 

+ **Right to restrict processing**

    + Remove the customer from, for example, a marketing campaign.

The GDPR is not a law exclusive of all other laws. AX 2012 (R1, R2, R3) is an enterprise resource planning system, and does not allow for restricted processing of certain business or transactional data, and will not endorse nor provide functionality for the restricted processing of business data that is necessary for compliance with other laws or certifications. AX 2012 will not provide support for modifications/customizations or other actions that result in the corruption of referential or business data integrity.

## Additional resources

Link to the European Union (EU) site that contains the GDPR

Additional product updates and further information that is specific to AX 2012 are available from [Microsoft Dynamics Lifecycle Services](https://fix.lcs.dynamics.com/Issue/Results?q=3909273) (LCS). Sign-in is required for access to LCS. 

Here are some example inquiries and reports that are available in AX 2012:

+ **Home** &gt; **Common** &gt; **Global address book**

    In the inquiry window, enter a person's name in the search box.

+ **Accounts payable** &gt; **Common** &gt; **Vendor** &gt; **All vendors**
+ **Accounts receivable** &gt; **Common** &gt; **Customer** &gt; **All Customers**
+ **Human resources** &gt; **Common** &gt; **Workers**
+ **Sales and marketing** &gt; **Common** > **Customers**, **Prospects**, **Leads**, or **Contacts**

## Additional resources
To learn more about the GDPR on the [European Union's website](http://europa.eu/) and on the [Microsoft Trust Center](https://www.microsoft.com/en-us/TrustCenter/Privacy/gdpr/default.aspx).

### Disclaimer
(c)2018 Microsoft Corporation. All rights reserved. This document is provided "as-is." Information and views expressed in this document, including URL and other Internet Web site references, may change without notice. You bear the risk of using it. This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes.
