---
# required metadata

title: Pay-when-paid vendor agreements | Microsoft Docs
description: This article explains pay-when-paid (PWP) terms for vendor agreements. PWP terms let you partially or fully withhold payment to a vendor until the customer on the project pays you. This article also provides a real-life example to show how you can use PWP terms for a project.
author: kfend
manager: AnnBe
ms.date: 2015-12-11 22:59:49
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: ProjProjectsListPage
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 23131
ms.assetid: 73816fb8-6eb2-4675-a46c-639820f211d2
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Pay-when-paid vendor agreements

This article explains pay-when-paid (PWP) terms for vendor agreements. PWP terms let you partially or fully withhold payment to a vendor until the customer on the project pays you. This article also provides a real-life example to show how you can use PWP terms for a project.

When you approve a vendor to work on a project as a subcontractor, you might want to withhold payment to the vendor or subcontractor until your customer pays you for the project. To withhold a payment to a vendor, set up pay-when-paid (PWP) terms when you set up the purchase order with the vendor. When you create a purchase order for the vendor and assign a project ID to the purchase order, PWP terms in the project are associated with the purchase order and the vendor. On the **Vendor invoices with pay when paid** page, you can view a list of the unpaid vendor invoices for a purchase order, and the associated customer invoices. Use this form to determine whether and how much to pay a vendor. For example, when a customer pays an amount on a project invoice, you can release part or all of the related vendor invoices for payment. You can set up PWP terms to specify that a vendor is paid after you receive a specific percentage of the related payment from a customer. When you receive partial payment from a customer, you can manually release some of the related vendor invoices for payment. The following example shows how you can use PWP terms to withhold payment to a vendor or subcontractor until the customer pays you. Your organization enters into an agreement with a customer to provide 100 computers on which you install software that the customer requests. The price that you and the customer agree on is 150.00 for each computer. You engage the services of a third-party vendor to provide the computers to you. The customer wants to approve the quality of the computers before your organization is paid. Your organization’s policy is to withhold payment to a third-party vendor until you have been paid by the customer on a project. Therefore, you set up the project with a PWP percentage of 100 percent, so that you withhold all payments to the vendor until you receive full payment for the customer invoice. The vendor charges 100.00 for each computer. When the vendor sends the computers to you, the shipment includes an invoice of 10,000.00 for the 100 computers. Because you have set up the project with PWP terms, you don't pay the vendor. After you receive the computers from the vendor, you install the required software on the computers. When you send the computers to the customer, you also send the customer an invoice for 15,000.00. The customer inspects the computers and approves the quality of the product. The customer then pays your organization the full amount of the project invoice. After you receive the full payment from the customer, you pay the vendor the full amount of the vendor invoice, 10,000.00.

