---
title: Create a vendor account
description: This procedure shows how to create a vendor account, and add an address and contact information. 
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: VendTable, LogisticsPostalAddressGrid, DirPartyLookup, LogisticsPostalAddress, SysLookupMultiSelectGrid, WHSFilterGenerallyAvail
ms.topic: how-to
ms.date: 12/08/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create a vendor account

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a vendor account, and add an address and contact information. The procedure doesn't show how to populate all fields for purchasing and financial purposes. To learn more about those fields, read the field descriptions. You can use this procedure in demo data company USMF or on your own data. Vendor accounts are typically created by a procurement professional or accounts receivable personnel.

## Create a vendor account

1. Go to **Procurement and sourcing > Vendors > All vendors**.
2. On the Action Pane, select **New**.
3. In the **Vendor account** field, enter a value that will uniquely identify the vendor.
    - The value may be populated automatically. If so, you can skip this step.  
    - You can create vendor accounts for a person or organization. This will affect which fields are available. In this example, we'll create a vendor account for an organization.
4. In the **Name** field, enter or select a vendor name. If your vendor is an already registered in your system, select it in the drop-down list and the new vendor account will inherit the address and contact information that's already registered.
5. In the **Group** field, select a vendor group. The vendor group is used to group vendors that have any of the following parameters in common: Terms of payment, settle period, inventory posting ledger accounts – including the sales tax group, default ledger accounts, product filter codes, or supply forecast configuration.
6. In the **Number of employees** field, enter the number of employees.
7. In the **Organization number** field, enter the legal organization number of the vendor.

## Add an address

1. Expand the **Addresses** section.
2. Select **Add**.
3. In the **Purpose** field, select a purpose of the address. You can select one or more purposes. These are used to select the correct address for a given purpose. For example, if the purpose is *Invoice* that address will be used when you send invoices.
4. In the **Name or description** field, enter a name of the address.
5. In the **Country/region** field, select a country. Enter the address details. The country/region that you selected will determine the fields you're presented with, corresponding to the address format for the country/region.
6. Select **OK**.

## Add contact information

1. Expand the **Contact information** section.
2. Select **Add**.
3. In the **Description** field, enter a contact name.
4. In the **Type** field, select a contact type. For example, if the contact details include the phone number, select *Phone* option in the **Type** field.
5. In the **Contact number/address** field, type a contact information. You can select the Primary check box if this is the primary contact.  
6. Select **Save**.
7. Close the page.
8. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
