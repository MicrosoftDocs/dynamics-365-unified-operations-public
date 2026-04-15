--- 
title: Create an operating unit
description: Learn how to create an operating unit, an organization that is used to divide the control of economic resources and operational processes in a business. 
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: OMOperatingUnit, OMInternalOrganizationSelector   
ms.dyn365.ops.version: Version 7.0.0 
---

# Create an operating unit

[!include [banner](../../includes/banner.md)]

An operating unit is an organization that is used to divide the control of economic resources and operational processes in a business. People in an operating unit have a duty to maximize the use of scarce resources, improve processes, and account for their performance. The types of operating units include cost centers, business units, departments, and value streams. 

Starting with Dynamics 365 Finance version 10.0.48, operating units can be used to represent [Establishments](organizations-organizational-hierarchies.md#establishments). An establishment represents an operational unit of a legal entity that carries out economic activity and may require its own regulatory identifiers on business documents, such as invoices. Establishments are modeled by using existing operating units and identified through an organization hierarchy that’s assigned the **Enterprise establishment structure** purpose. Only operating units that are included in such a hierarchy are treated as establishments. The legal entity remains the single legal and accounting entity, while establishments are used for operational and regulatory purposes.

Use the following procedure to create an operating unit. The demo data company used to create this procedure is USMF.

1. Go to **Navigation pane > Modules > Organization administration > Organizations > Operating units**.
1. Select **New** to open the dialog.
1. Find and select the desired record. Select the type of operating unit you want to create.  
1. Select the link in the selected row.
1. In the **Name** field, enter a value.
    + Expand the **General** section, if necessary.  
    + Provide general information about the operating unit, such as an identification number, DUNS number, and manager.
    + Expand the **Addresses** section, if necessary.  
    + Enter address information, such as the street name and number, postal code, and city. Select **Add** to enter a new address record, or select **Edit** to modify an existing address record.
    + Expand the **Contact information** section, if necessary.  
    + Enter information about methods of communication, such as email addresses, URLs, and telephone numbers. To enter a new communication record, select **New**. To modify an existing communication record, select **More options > Advanced**.
1. Optionally, change the **Operating unit number** as needed. This number is a unique identifier for the corresponding **Party** record and can't be the same as any other operating unit.
1. Select **Save**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
