---
title: Date of vendor VAT register
description: Learn about a feature for enabling date of vendor VAT register. You can deduct the incoming VAT amount for purchase invoices.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: global
ms.search.validFrom: 2022-01-15
---

# Date of vendor VAT register

In Microsoft Dynamics 365 Finance version 10.0.24, a new **Date of vendor VAT register** field is available for vendor invoices. This field specifies the date of the taxable supply for a purchase.

To enable the new field, go to the **Feature management** workspace, find and select the **Enable date of vendor VAT register on vendor invoices** feature, and then select **Enable now**.

Incoming invoices from your suppliers can have two dates: the date when the vendor issued the invoice and the date of the taxable supply (that is, the date when the vendor charged the value-added tax [VAT] payable). In some scenarios, these two dates differ.

You can deduct the incoming VAT amount for a purchase invoice and include that invoice on VAT reports later, on a date that differs from both previously mentioned dates. Local legislation rules about postponed incoming VAT deduction for some scenarios control this date. It varies by country or region.

Some VAT reports, such as the [VAT Control statement report](../czech-republic/emea-cze-vat-declaration-tax-declaration-model.md#vat-control-statement) in the Czech Republic, require that you report the date of the taxable supply for a purchase document. You must report this date so that the tax authorities can reconcile the VAT reporting between counterparties.

In Finance, you can define dates in the following fields:

- **Invoice date** – The date when the supplier issues the invoice.
- **Date of VAT register** – The date of the VAT amount deduction for the purchase invoice.
- **Date of vendor VAT register** – The date of the taxable supply of the vendor.
- **Receive document date** – The date when you receive the invoice.

These fields are included on the following pages:

- Vendor invoice
- Vendor invoice register
- Vendor invoice approval
- Vendor invoice journal

After you post the vendor invoice, you can review the dates on the **Invoice journal** and **Vendor transactions** pages.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]