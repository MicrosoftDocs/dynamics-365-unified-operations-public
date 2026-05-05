---
title: Create a vendor account
description: Learn how to create a vendor account, and add an address and contact information, including step-by-step processes for adding addresses and contact info.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VendTable, LogisticsPostalAddressGrid, DirPartyLookup, LogisticsPostalAddress, SysLookupMultiSelectGrid, WHSFilterGenerallyAvail
ms.topic: how-to
ms.date: 5/5/2026
ms.custom: 
  - bap-template
---

# Create a vendor account

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a vendor account, and add an address and contact information. The procedure doesn't show how to populate all fields for purchasing and financial purposes. To learn more about those fields, read the field descriptions. You can use this procedure in demo data company USMF or on your own data. Procurement professionals or accounts receivable personnel typically create vendor accounts.

## Create a vendor account

1. Go to **Procurement and sourcing** > **Vendors** > **All vendors**.
1. On the Action Pane, select **New**.
1. In the **Vendor account** field, enter a value that uniquely identifies the vendor.
        - The value might be populated automatically. If so, you can skip this step.    
    - You can create vendor accounts for a person or organization. This choice affects which fields are available. In this example, create a vendor account for an organization.
1. In the **Name** field, enter or select a vendor name. If your vendor is already registered in your system, select it in the dropdown list. The new vendor account inherits the address and contact information that's already registered.
1. In the **Group** field, select a vendor group. Use the vendor group to group vendors that have any of the following parameters in common: terms of payment, settle period, inventory posting ledger accounts - including the sales tax group, default ledger accounts, product filter codes, or supply forecast configuration.
1. In the **Number of employees** field, enter the number of employees.
1. In the **Organization number** field, enter the legal organization number of the vendor.

## Add an address

1. Expand the **Addresses** section.
1. Select **Add**.
1. In the **Purpose** field, select a purpose of the address. You can select one or more purposes. These purposes help you select the correct address for a given purpose. For example, if the purpose is *Invoice*, use that address when you send invoices.
1. In the **Name or description** field, enter a name of the address.
1. In the **Country/region** field, select a country/region. Enter the address details. The country/region that you select determines the fields you're presented with, corresponding to the address format for the country/region.
1. Select **OK**.

## Add contact information

1. Expand the **Contact information** section.
1. Select **Add**.
1. In the **Description** field, enter a contact name.
1. In the **Type** field, select a contact type. For example, if the contact details include the phone number, select *Phone* option in the **Type** field.
1. In the **Contact number/address** field, type a contact information. You can select the Primary check box if this is the primary contact.  
1. Select **Save**.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
