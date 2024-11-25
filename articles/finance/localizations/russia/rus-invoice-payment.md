---
title: Invoices for payment (Russia)
description: Learn how to post and print invoices for payment in Microsoft Dynamics 365 Finance in Russia, including an outline on psting and printing invoices for payments.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Invoices for payment (Russia)
[!include [banner](../../includes/banner.md)]

Invoice for payment is an optional document containing payment details of the recipient (seller), for which the payer (buyer) transfers money for the purposes listed in the invoice for payment, such as work or services. This is a document that serves to pay for the purchased goods by the buyer or to transfer a prepayment (advance). 

Before posting **Invoice for payment** in the Account payable and Account receivable modules it is necessary to set up the number sequences:
1.  Click **Accounts receivable** \> **Setup** \> **Accounts receivable parameters** or **Accounts payable** \> **Setup** \> **Accounts payable parameters**

2.  Click the **Number sequences** tab.

3.  In the **Number sequence code** field, select the number sequence code for the **invoice for payment** (**Reference** field).

## Post and print an invoice for payment from a sales order 

Use the **Posting invoice for payment** page to post an invoice for payment.

1.  Click **Accounts receivable** \> **Common** \> **Orders** \> **All sales orders**.

2.  Create a new sales order, and enter the required details.

3.  Click the **Sell** tab on the action pane, and then click **Invoice for payment**.

4.  In the **Invoice for payment date** field, select the date of the invoice for payment.
    
    > [!NOTE]
    > By default, the current date is displayed.

6.  Click the **Lines** tab, and then select the line that contains the item details, based on the value that is selected in the **Quantity** field.

7.  Set the **Posting** option to **Yes** to post the invoice for payment.
    
    > [!NOTE]
    > You can post and print an invoice for payment only for active bank accounts.

8.  Set the **Print invoice for payment** option to **Yes** to print the invoice for payment after posting.
8. Set the **Use print management destination** option to **Yes** to print the invoice for payment using print management destinations. Set this option to **No** to use the default printer settings.
9. Set the **Print in national currency** option **Yes** to print the invoice for payment in national currency.

10. Click the **Officials** tab to validate and update default values, if needed.

    > [!NOTE]
    > Use the **Officials** page to set up the default officials to be listed on the invoice for payment. For more information, see [Set up officials](rus-officials.md).

11.  Click **OK** to post the invoice for payment. You can view the details of the posted invoice in the **Journal of invoices for payment** page list.

## Post and print an invoice for payment from a free text invoice 

Use the **Posting invoice for payment** page to post an invoice for payment.

1.  Click **Accounts receivable** \> **Common** \> **Invoices** \> **All free text invoices**.

2.  Create a new free text invoice, and enter the required details. For more information, see [Create free text invoices](../../accounts-receivable/create-free-text-invoice-new.md).

3.  On the action pane, click **Post** \> **Invoice for payment** to open the **Posting invoice for payment** page.
    
    > [!NOTE]
    > If the free text invoice has already been posted, the **Invoice for payment** option is not available.
    
4.  In the **Print** field, select **Current** to print each invoice, or select **After** to print after all of the invoices have been posted.

5. Set the **Print** option to **Yes** to print the invoice for payment after posting.

6. Set the **Print in national currency** option **Yes** to print the invoice for payment in national currency.

7. Set the **Use print management destination** option to **Yes** to print the invoice for payment using print management destinations. Set this option to **No** to use the default printer settings.
 
8. Click the **Officials** tab to validate and update default values, if needed.

    > [!NOTE]
    > Use the **Officials** page to set up the default officials to be listed on the invoice for payment. For more information, see [Set up officials](rus-officials.md).

9. Click the **Other** tab. In the **Comments** field, enter a comment for the invoice for payment.

10. Click **OK** to post and print the invoice for payment.
    

    > [!NOTE]
    > Click **Accounts receivable** > **Common** > **Invoices** > **All free text invoices**. On the action pane, click **Related information > Invoice for payment** to view the posted invoices for payment. Or, click **Accounts receivable > Inquiries and reports > Invoices > Invoice for payment**.
    > You can also use the **Journal of invoice for payment** page list to print the invoice for payment.

## Post and print an invoice for payment from a purchase order 

Use the **Posting invoice for payment** page to post a purchase invoice for payment.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

2.  Create a new purchase order, and enter the required details.

3.  On the action pane, click the **Purchase** tab, and then click **Invoice for payment**.

4.   In the **Invoice for payment date** field, on the **Posting invoice for payment** page, enter the date of the invoice for payment and in the **Invoice for payment** field enter the number of the invoice for payment that you received from the vendor. By default, the current date is displayed.

5.  Click the **Lines** tab, and then select the line that contains the item details, based on the value that is selected in the **Quantity** field.

6.  Set the **Posting** option to **Yes** to post the invoice for payment.
    
    > [!NOTE]
    > You can post and print an invoice for payment only for active bank accounts.

8.  Set the **Print invoice for payment** option to **Yes** to print the invoice for payment after posting.

9.  Click **OK** to post the invoice for payment. You can view the details of the posted invoice in the **Journal of invoices for payment** list page (on the **Purchase** action pane click **Journals** \> **Invoice for payment**).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
