--- 
title: Create an organization hierarchy
description: Learn how to create an organization hierarchy, including a step-by-step processes, including an outline on adding organizations to hierarchies. 
author: johnmichalak
ms.author: johnmichalak 
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: OMHierarchyManager, OMHierarchyPurposeAssociation, OMHierarchySelection, HierarchyDesigner  
ms.dyn365.ops.version: Version 7.0.0 
---

# Create an organization hierarchy

[!include [banner](../../includes/banner.md)]

Use the following procedure to create an organizational hierarchy. You can use organizational hierarchies to view and report on your business from various perspectives. For example, you can set up one hierarchy for tax, legal, or statutory reporting. You can then set up another hierarchy to report financial information that isn't legally required, but that is used for internal reporting.

Starting with Dynamics 365 Finance version 10.0.48, organization hierarchies can also be used to model [Establishments](organizations-organizational-hierarchies.md#establishments). Establishments represent operational units of a legal entity that may require their own regulatory identifiers on invoices. Establishments are modeled using existing operating units and are identified through a dedicated organization hierarchy purpose, **Enterprise establishment structure**. This hierarchy determines which operating units are treated as establishments in invoicing, while the legal entity remains the single legal and accounting entity.

Before you create an organizational hierarchy, you must create organizations. For more information, see the "Create a legal entity" or "Create an operating unit" tasks. You can also create departments and teams. 

The demo data company used to create this procedure is USMF.

## Create a hierarchy

1. Go to **Navigation pane** > **Modules** > **Organization administration** > **Organizations** > **Organization hierarchies**.
1. On the **Action pane**, select **New**.
1. In the **Name** field, enter a value.
1. In the **Purpose** section, select **Assign purpose**.
1. In the list, find and select the desired record. Select a purpose to assign to your organization hierarchy.  
1. In the **Assigned hierarchies** section, select **Add**.
1. In the list, select the row. Find the hierarchy you just created.  
1. Select **OK**.

## Add organizations to the hierarchy

1. In the list, find and select the desired record. Select your hierarchy.  
1. In the **Assigned hierarchies** section, select **View hierarchy**.
    - Add organizations, as necessary.  
    - To add an organization, select **Edit** and then **Insert** to add the organization. When you're done making changes, you can **Save** a draft and/or **Publish** the changes.  

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
