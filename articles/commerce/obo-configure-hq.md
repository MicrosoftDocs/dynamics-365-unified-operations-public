---
# required metadata

title: Set up on behalf of in Microsoft Dynamics 365 Commerce.
description: This article describes how to set up on behalf of in Microsoft Dynamics 365 Commerce.
author:  mariash529
ms.date: 02/27/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-27
ms.dyn365.ops.version: 10.0.33
---

# Set up on behalf of in Microsoft Dynamics 365 Commerce

[!include[banner](../includes/banner.md)]

This article describes how to setup on behalf of feature in Microsoft Dynamics 365 Commerce.

## Add Identity providers in Commerce Shared parameters:

To setup identity provider to be used by **Retail server**  follow these steps: Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce Shared parameters**. In **Identity Providers tab**, add an identity provider you [created](obo-create-aad-application.md) for AAD B2C application:
1.	In Identity providers section add the following entry:
    1. **Issuer:** https://sts.windows.net/TENANTID
    1. **Issuer Type:** “Azure Active Directory”.
    1. **Issuer Name:** any name
1. In Relying Party section add the following entry:
    1. **ClientID:**  Client Id of AAD B2C application
    1. **Type:** Confidential
    1. **User Type:** Worker
1.	In Server Resource IDS section add the following entry:
    1. **Server Resource Id:** https://APPLICATIONIDUR
    1. **Name:** blank

## Create and Configure Sales Groups: 
Create a [sales group](tasks/worker.md) of one or more account managers. Assign commissions percentage if your organization assigns commissions. For on behalf of functionality to work it is sufficient for a sale representative to be present in a sales group, a commission percentage can be equal to zero. 

## Associate Sales Group with B2B buyer organization:
Under **Sales and Marketing** -> **Customers** -> **all customers** locate  a customer of type organization that needs to be managed by the sales group you set up in the previous step. Specify this sales group id in the field **Sales group** under **Sales order defaults** tab. Note, in the customer hierarchy that corresponds to this customer organization you will be able to observe the sales group appear as a read-only field in the section **Sales Groups**. Any member of the Sales group is able to work on behalf of any user in this customer hierarchy.  

:::image type="content" source="./media/obo-customer-hierarchy.png" alt-text="Example of Contoso B2B customer hierarchy that has a sales group 998 listed":::

## Additional resources

[Update Commerce headquarters with the new Azure AD B2C information](update-hq-aad-b2c-info.md)

[Configure a worker](tasks/worker.md)

[Enter worker information](../human-resources/hr-personnel-enter-worker-information.md)
