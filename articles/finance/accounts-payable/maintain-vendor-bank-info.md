---
# required metadata

title: Maintain vendor bank account information
description: 
author: v-kiarnd
manager: AnnBe
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 26181
ms.assetid: 10f56dea-ea2d-48ea-9622-4ef715eb1179
ms.search.region: USA
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2011-01-14
ms.dyn365.ops.version: AX 10.0.17

---

# Maintain vendor bank account information

Vendors can maintain their bank account information within Vendor  collaboration. Vendor account maintenance can be performed in the Vendor information workspace. From here, vendors will select **More details** and **Bank accounts**. To add a new bank accounts, click the **Add** button above the bank account grid. A **New** slider will display. You can enter the following information in the slider.   
 
- **Bank account** 
- **Bank name** 
- **Bank account number** 
- **Bank routing number** 
- **Effective date** 
- **Expiration date**
- **Comments** can be entered, but are optional
 
Swift code and IBAN number fields will display if the legal entity is outside the United States.
 
If there are documents related to the specific certification, you can attach them by clicking the **Document** button.     
 
Bank information entered by the vendor on this page will display Vendor as the source.   The customer can also enter bank account information on the vendors behalf under vendor bank accounts, and the information will display here and the source will display **Customer**.
 
Vendors can edit their bank’s effective and expiration dates as needed after an account has been added.
 
 
## Vendor collaboration generated bank changes page
Once bank information is updated by a vendor, the information will be visible in a new **Vendor collaboration-generated bank changes** page available under **Accounts payable > Inquiries > Vendor reports**. By default, all newly entered or modified bank records are visible. The accounts payable clerk can view the changes and run the account information through their pre-note process to validate the account information. When this process is complete and the primary payment method has been manually updated, the bank account listed on the **Vendor collaboration-generated bank changes** page can be selected and marked as reviewed. This action will remove the account from the default list.
 
You can see all changes to a vendor’s bank information by modifying the filters to view by vendor account, the effective date range, and by whether or not the changes have been reviewed.
