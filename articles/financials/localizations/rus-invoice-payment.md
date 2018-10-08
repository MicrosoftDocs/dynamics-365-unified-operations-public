---
# required metadata

title: Invoices for the purpose of payment (Russia)
description: This topic explains how to post and print invoices for payment in Microsoft Dynamics 365 for Finance and Operations in Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 09/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Invoices for the purpose of payment (Russia)
[!include [banner](../includes/banner.md)]

Invoice for payment is an optional document containing payment details of the recipient (seller), for which the payer (buyer) transfers money for the purposes (works, services) listed in the the invoice for payment. A document that serves to pay for the purchased goods by the buyer or to transfer a prepayment (advance). It has never been a primary document, since it does not reflect the fact of economic life.

## Post a purchase invoice for payment 

Use the **Posting invoice for payment** form to post a purchase invoice for payment.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

2.  Create a new purchase order, and enter the required details.

3.  On the action pane click the **Purchase** tab, and then click **Invoice for payment**.

4.   In the **Invoice for payment date** field in the **Posting invoice for payment** page, enter the date of the invoice for payment and in the **Invoice for payment** field enter the number of the invoice for payment, received from the vendor.
    
    > [!NOTE]
    > By default, the current date is displayed.

5.  Click the **Lines** tab, and then select the line that contains the item details, based on the value that is selected in the **Quantity** field.

6.  Set the **Posting** option to **Yes** to post the invoice for payment.
    
    > [!NOTE]
    > You can post and print an invoice for payment only for active bank accounts.

8.  Set the **Print invoice for payment** option to **Yes** to print the invoice for payment after posting.

9.  Click **OK** to post the invoice for payment. You can view the details of the posted invoice in the **Journal of invoices for payment** list page ().

## Post a sales invoice for payment 

Use the **Posting invoice for payment** form to post a sales invoice for payment.

1.  Click **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Create a new sales order, and enter the required details.

3.  Click the **Sell** tab, and then click **Invoice for payment**.

4.  In the **Invoice for payment date** field, select the date of the invoice for payment.
    
    > [!NOTE]
    > By default, the current date is displayed.

5.  In the **Invoice for payment** field, enter the invoice number.

6.  Click the **Lines** tab, and then select the line that contains the item details, based on the value that is selected in the **Quantity** field.

7.  Select the **Posting** check box to print each invoice as it is updated.
    
    > [!NOTE]
    > You can post and print an invoice for payment only for active bank accounts.

8.  Select the **Print invoice for payment** check box to print the invoice for payment after you post it.

9.  Click **OK** to post the invoice for payment. You can view the details of the posted invoice in the **Journal of invoices for payment** form.

## Post and print an invoice for payment for a free text invoice 

With the Invoice for payment for free text invoices function, you can use the **Posting invoice for payment** page to post and print a free text invoice for payment. After posting, the invoices are displayed on the **Journal of invoices for payment** page. You can post as many invoices for payment as necessary.

1.  Click **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.

2.  Click the **Number sequences** tab.

3.  In the **Number sequence code** field, select the number sequence code for the invoice for payment reference type in the **Reference** field.

4.  Press CTRL+S or close the form.

5.  Click **Accounts receivable** \> **Common** \> **Free text invoices** \> **All free text invoices**.

6.  Press CTRL+N to create a free text invoice, and enter the required details.
    
    > [!NOTE]
    > For more information, see [Create a free text invoice](../accounts-receivable/create-free-text-invoice-new.md).

7.  Click **Post** \> **Invoice for payment** to open the **Posting invoice for payment** form.
    
    > [!NOTE]
    > If the free text invoice, or the facture for the free text invoice, has already been posted, the **Invoice for payment** option is not available.
    
8.  In the **Print** field, select **Current** to print each invoice as it is updated, or select **After** to print after all of the invoices have been updated.

9.  Select the **Print** check box to print the invoice for payment after posting.

10. Select the **Print in national currency** check box to print the invoice for payment in national currency.

11. Select the **Use print management destination** check box to print the invoice for payment using print management destinations. Clear the check box to use the default printer settings.
 
12. Click the **Officials** tab.

13. In the **Employee name** field, select the name of the responsible official from the list of company employees with the corresponding position title.

14. In the **Title** field, select the job title of the employee for the corresponding employee.
    

    > [!NOTE]
    > Use the **Officials** page to set up the default officials to be listed on the invoice for payment.

15. Click the **Other** tab. In the **Comments** field, enter a comment for the invoice for payment.

16. Click **OK** to post and print the invoice for payment.
    

    > [!NOTE]
    > Click **Accounts receivable** > Common > Free text invoices > All free text invoices**. Click **Related information > Invoice for payment**to view the posted invoice. Or click **Accounts receivable > Inquiries > Journals > Invoice for payment**.
    > You can also use the **Journal of invoice for payment** form to print the invoice for payment.


