---
# required metadata

title: Set up and use pay-when-paid vendor payments
description: This topic explains how to create pay-when-paid (PWP) terms so that you can release partial vendor payments, based on customer payments. 
author: RadhikaRS
manager: AnnBe
ms.date: 03/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15

---

# Set up and use pay-when-paid vendor payments

[!include [banner](../includes/banner.md)]

When you approve a vendor to work as a subcontractor, you might want to withhold payment to the vendor until your customer pays you for the project. To support this scenario, you can set up pay-when-paid (PWP) terms when you set up the purchase order (PO) with the vendor.

For example, when a customer pays an amount on a project invoice, you can release some or all of the vendor invoice amount. Just set up PWP terms that specify that the vendor will be paid after you receive a percentage of the related payment from the customer. If you receive partial payment from a customer, you can manually release some of the related vendor invoices for payment.

The following example outlines the process when PWP terms are used.

## Example

Your organization agrees to provide a customer with 100 computers that have software installed, for a price of 150.00 US dollars (USD) per computer. You then hire a vendor to provide you with the computers that have software installed. According to the agreement, the customer must approve the quality of the computers before it pays your organization. Your organization's policy is to withhold payment to vendors until the customer has paid you. Therefore, you set up the project so that it has a PWP percentage of 100 percent.

The vendor sends you the 100 computers that have software installed, together with an invoice for 10,000.00 USD. Because PWP terms are set up for your project, you don't pay the vendor upon receipt of the computers. Instead, you send the computers to the customer, together with an invoice for 15,000.00. The customer inspects the computers and approves the full amount of the project invoice.

After you receive the full payment from the customer, you pay the vendor 10,000.00, the full amount of the vendor invoice.

## Set up PWP terms for a project

When you set up PWP terms for a project, you must specify, as a percentage, the minimum amount that a customer must pay you for the project before you will pay the vendor. The threshold amount is automatically calculated on the customer invoices for the project. Follow these steps to set up the threshold percentage for PWP terms.

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
2. Find and open the project that you want to set up PWP terms for.
3. On the **Vendor agreements** FastTab, select **Add line**.
3. In the **Account code** field, select one of the following options:

    - **Table** – The PWP terms apply to a single vendor.
    - **Group** – The PWP terms apply to all vendors in a vendor group.
    - **All** – The PWP terms apply to all vendors.

4. If you selected **Table** or **Group** in the previous step, in the **Vendor/Vendor group** field, select the vendor or vendor group that the PWP terms apply to. If you selected **All** in the previous step, the **Vendor/Vendor group** field can't be edited.
5. If vendor retention terms are set up for the vendor in the project, in the **Vendor retention terms** field, select the rule ID for the retention terms.
6. In the **PWP threshold percentage** field, enter the threshold percentage for the project. The percentage that you enter for the project defines the minimum amount that the customer must pay you before you will pay the vendor.

## Create a PO that has PWP terms

When you post an invoice from a vendor, if the vendor is subject to PWP terms, those terms are shown on the PO lines. To create a PO that has PWP terms, follow these steps.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
2. On the Action Pane, select **New**. Then, in the **Create purchase order** dialog box, enter the required information, and select **OK**.

    Alternatively, open an existing PO on the **All purchase orders** list page.

4. On the **Purchase order** page, on the **Purchase order lines** FastTab, review the details of the PO line for the vendor. The **Pay when paid** option is automatically selected, and the value in the **PWP threshold percentage** field is automatically copied from the **PWP threshold percentage** field on the **Projects** page.
6. If you don't want to apply PWP terms to the vendor for a PO line, clear the **Pay when paid** option. In this case, the **PWP threshold percentage** field for the PO line will be reset to 0 (zero).

## Update a customer payment and pay the vendor

When a vendor completes its work on a project and sends you an invoice, you must review the project status and customer invoices to determine whether the PWP terms have been met for the project. If the PWP terms for the vendor were met, you can determine which lines on the vendor invoice to pay, based on the customer payments for the project. If you decide to pay the vendor even though the PWP terms weren't met, you can override the PWP terms on the **Vendor invoice with pay when paid** page.

1. Go to **Project management and accounting** \> **Inquiries and reports** \> **Retention inquiries** \> **Vendor invoice with pay when paid**.
2. On the **Vendor invoices with pay when paid** page, in the search field, enter values to find the vendor invoice that you want to review, and then select **Search**.
3. On the **Vendor invoice lines** FastTab, select the lines that you want to change.
4. If the **Pay when paid** conditions are met for the invoice line, select **Release vendor payment**. The **Pay when paid** option is cleared, and the value of the **Ready for payment** field is changed to **Yes**.
