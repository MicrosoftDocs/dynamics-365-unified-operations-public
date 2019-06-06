---
# required metadata

title: Create main accounts for the GST posting type
description:  This topic provides information about how to create main accounts for the GST posting type.
author: EricWang
manager: RichardLuan
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Create main accounts for the GST posting type

To enable the India localization solution for GST in Microsoft Dynamics 365 for Finance and Operation, the following master data setup configurations are required:

- Define business vertical
- Update the state code and union territory
- Create a GSTIN master
- Define GSTIN numbers for the legal entity, warehouse, vendor, or customer masters
- HSN codes and Service accounting codes
- Create main accounts for the GST posting type
- Create a tax settlement period
- Attach the GSTIN to a tax registration group

Complete the following steps to create main accounts for the GST posting type.

1. Click **General ledger** \> **Chart of Accounts** \> **Accounts** \> **Main accounts**.
2. Create a record and in the **Main account** field, enter a value.
3. In the **Name** field, enter a value.
4. On the **General** FastTab, in the **Main account type** field, select a value.
5. On the **Setup** FastTab, in the **Posting type** field, select GST.
6. Repeat steps 2 through 5 to create all of the required state-wide ledger accounts.

![Create main accounts for the GST posting type](media/Create-main-accounts-for-the-GST-posting-type.png)

