---
# required metadata

title: Set up and manage vendor payments
description: This article describes how to create pay-when-paid (PWP) terms to release partial vendor payments  based on client payments. 
author: RadhikaRS
manager: AnnBe
ms.date: 03/24/2020
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

# Set up and manage vendor payments

[!include [banner](../includes/banner.md)]

When you approve a vendor to work as a subcontractor and want to withhold payment to the vendor until your customer pays you for the project, you can set up the pay-when-paid (PWP) terms when you set up the purchase order (PO) with the vendor. 

For example, when a customer pays an amount on a project invoice, you can release a partial amount, or the complete amount of the vendor invoice. To do this, set up the PWP terms specifying payment to the vendor after you receive a percentage of the related payment from the customer. When you receive partial payment from a customer, you can manually release some of the related vendor invoices for payment. The following example outlines the process flow when using PWP terms. 

 

**Example**

1. Your organization agrees to provide a customer with 100 computers, with software installed, for a price 150.00 per computer. You then hire a vendor to provide the computers to you. 
2. According to the agreement, the customer needs to approve the quality of the computers before they pay your organization.  Your organization’s policy is to withhold payment to a vendor until the customer has paid you. Your set up the project with a PWP percentage of 100 percent to withhold all payments to the vendor until you receive full payment from the customer.
3. The vendor sends you the computers with an invoice amount of 10,000.00 for 100 computers. Since your project is set up with PWP terms, you do not pay the vendor upon receipt of the computers. 
4. You send the computers with the software installed to the customer, along with an invoice for 15,000.00. The customer inspects the computers and approves the full amount of the project invoice.  
5. After you receive the full payment from the customer, you pay 10,000.00 to the vendor for the full amount of the vendor invoice. 

## Set up PWP terms for the project

You set the minimum amount percentage PWP terms that a customer must pay you on a project before you can pay the vendor. The threshold amount is automatically calculated on the customer invoices for the project. To set PWP threshold percentage terms, complete the following steps:

1. Select **Project management and accounting** > **Projects** > **All projects**.
2. Open the project from the **Project** list page and on the **Vendor agreements** FastTab, select **Add line**.
3. In the **Account code** field, select one of the following options:
   - **Table** – If the PWP terms apply to a single vendor. 
   - **Group** – If the PWP terms apply to all vendors in a vendor group.
   - **All** – If the PWP terms apply to all vendors
4. In the **Vendor/Vendor group** field, select the vendor or vendor group to which the PWP terms apply. If you selected **All** in the previous step, this field becomes unavailable.
5. If the project has vendor retention terms set up for the vendor, in the **Vendor retention terms** field, select the **Rule ID** for the retention terms. 
6. In the **PWP threshold percentage** field, enter the threshold percentage for the project. The percentage that you enter for the project sets the minimum amount the customer must pay you before you pay the vendor. 

##  Create a purchase order with PWP terms

When you post an invoice from the vendor and the vendor is subject to PWP terms, the PWP terms are displayed on the purchase order lines. To create a purchase order (PO) with PWP terms, complete the following procedure.

1. Select **Procurement and sourcing** > **Purchase orders** > **All purchase orders**. 
2. In the Action Pane, select **New.**
3. In the **Create purchase order** page, enter the required information and select **OK**. Alternatively, open an existing PO in the **All purchase orders** list.
4. In the **Purchase order** page, on the **Purchase order lines** FastTab, review the details of the purchase order line for the vendor. 
5. The **Pay when paid** option is automatically selected, and the **PWP threshold percentage** value is automatically copied to this page from the **PWP threshold percentage** field in the **Projects** page.
6. If you do not want to apply PWP terms to the vendor for a purchase order line, you can clear the **Pay when paid** option, and the **PWP threshold percentage** field for the purchase order line is set to 0 (zero). 

## Update customer payment and pay the vendor

When the vendor completes work on the project and sends you an invoice, review the project status and customer invoices to see whether the PWP terms were met for the project. If the PWP terms for the vendor were met, you can determine which lines on the vendor invoice to pay, based on the customer payments for the project. If you decide to pay the vendor even if the PWP terms were not met, you can override the PWP terms in the **Vendor invoices with retention** page.

1. Select **Project management and accounting** > **Retention \**Inquiries\**** > **Vendor \**invoices with retention.\****
2. In the **Vendor invoices with retention** page, enter values to find the vendor invoice to review, and select **Search**.
3. On the **Vendor invoice lines** FastTab, review the lines and select the lines you want to change.
4. If the PWP conditions are met for the invoice line, select **Release vendor payment**. This clears the **Pay when paid** option, and the status of the **Ready for payment** field changes to **Yes**.

 
