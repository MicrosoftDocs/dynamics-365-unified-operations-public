---
title: Fiscal notes for fine and interest in Brazil tax reform
description: Learn about how to create fiscal notes for fine and interest in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 06/22/2026
ms.custom: bap-template
---

# Fiscal notes for fine and interest in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article explains how to create fiscal notes for fine and interest transactions in Brazil tax reform, for both customer (accounts receivable) and vendor (accounts payable) scenarios in Dynamics 365 Finance.

> [!NOTE]
> The fine and interest fiscal document is available for both **Accounts receivable** and **Accounts payable**. The key difference is the access key requirement, which is described in each of the following sections.

## Create a customer fiscal document with fine and interest

The fiscal establishment issues the customer (AR) fiscal document for fine and interest. You don't need an access key.

To create a customer fiscal document that includes fine and interest charges, follow these steps:

1. Go to **Accounts receivable** > **Fiscal notes** > **All Fiscal notes**.
1. In the list, find and select the desired fiscal document record.
1. Select **Business Type**.
1. Select **Fine and Interest**.
1. In the **Fine** field, enter the fine amount. You can edit the fine and interest amounts on this form.
1. In the **Interest** field, enter the interest amount.
1. Select **OK**.
1. In the list, select the row.
1. In the **Fine amount** field, review or update the value.
1. Select the **Setup** tab.
1. In the list, find and select the desired record.

    > [!NOTE]
    > Only Reform Tax Groups created in Globalization Studio are available in this field.

1. Close the page.
1. In the **Sales tax group** field, enter or select a value.
1. Close the page.
1. Select **Sales tax** to verify tax calculation.
1. Select **OK**.
1. Select the **Header** tab.
1. Select the **Lines** tab.
1. Select the **Product** tab.
1. Select the **Setup** tab.
1. Select the **General** tab.
1. Select **Post**.
1. Close the page.
1. Refresh the page.
1. Use the Quick Filter to find records. For example, filter on the **Number** field with a value of `096002238`.
1. Select **Voucher** to review the voucher transactions.
1. Close the page.
1. Select **Posted sales tax** to verify the posted tax.
1. Close the page.
1. Close the page.
1. Go to **Default dashboard**.
1. Go to **Accounts receivable** > **Fiscal notes** > **All Fiscal notes**.
1. In the list, select the link in the selected row.
1. Select **Fiscal reference** to verify that the original document is recorded as a fiscal reference.
1. Select **Show or hide control**.
1. Close the page.
1. Select the form caption.
1. Close the page.

## Create a vendor fiscal document with fine and interest

A third party (vendor) issues the vendor (AP) fiscal document for fine and interest. Because the fiscal document issuer isn't the fiscal establishment, you need an **access key**. The vendor provides the access key - it's the access key for the vendor-issued fiscal document and you can't retrieve it from the Dynamics 365 system.

To create a vendor fiscal document that includes fine and interest charges, follow these steps:

1. Go to **Accounts payable** > **Fiscal notes** > **All Fiscal notes**.
1. In the list, find and select the desired fiscal document record.
1. Select **Business Type**.
1. Select **Fine and Interest**.
1. In the **Fine** field, enter the fine amount.
1. In the **Interest** field, enter the interest amount.
1. In the **Fiscal document type** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Select the link in the **Vendor account** field to open the vendor record.
1. Use the Escape key to close the form.
1. In the **Access key** field, type the access key value provided by the vendor.

   > [!IMPORTANT]
   > The access key is the key of the fiscal document issued by the vendor. You must get it directly from the vendor, as it isn't stored elsewhere in Dynamics 365 Finance.

1. Select **Save**.
1. Select **Post**.
1. Select the **Header** tab.
1. Refresh the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
