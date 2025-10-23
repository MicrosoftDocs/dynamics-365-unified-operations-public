--- 
title: Vendor payment overview
description: Learn about the various methods used to create vendor payments, including how to use a payment proposal or manually entering an one-off payment.
author: kweekley
ms.author: kweekley
ms.topic: how-to
ms.date: 08/25/2025
ms.reviewer: twheeloc 
ms.collection: get-started
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0 
---

# Vendor payment overview

[!include [banner](../../includes/banner.md)]

This procedure walks through various methods used to create vendor payments, including how to use a payment proposal or manually entering an one-off payment. This procedure uses the USMF demo company.

1. Go to **Accounts payable > Payments > Vendor payment journal**.
2. Click **New**.
3. Select the payment journal in which to save the vendor payments. 
4. Select the journal or manually enter it.
5. Click **Lines**.
6. Click **Payment proposal**.
7. Click **Create payment proposal**. The payment proposal is a query used to select invoices for payment. You can edit the list of invoices to pay before creating or generating the vendor payments.
8. Select invoices for payment by due date, cash discount, or both. 
9. Enter the date for comparing to the due date or cash discount. 
10. Optional: Enter a payment date used for all payments. The date entered here is the payment date for all payments created, regardless of the due date or cash discount date.  
11. Optional: Enter a minimum payment date which may be used as the payment date. The minimum payment date is the earliest date used when creating payments. For example, if an invoice has a due date after the minimum payment date, the due date becomes the payment date instead of the minimum payment date in order to pay the invoice on the latest possible date.
12. Enter additional query restrictions under **Records to include** section. The filter is used to restrict the invoices selected for payment by vendor group or method of payment. For example, you may add a filter to only pay invoices by check in this pay run.
13. Enter additional query restriction or payment defaults. The additional parameters can be used to define the payment currency or to enable centralized payments for this pay run.  
14. Click **OK**. After clicking **OK**, the results of the query appear. If you don't want to preview the list of invoices selected to pay, go back to the **Parameters** FastTab and change the setting **Create payments without invoice preview** to **Yes**.  
15. Click **Show payment overview** to view the payments that will be created for the vendor on the invoice selected.
16. Click **Hide payment overview** to hide the payments. 
17. Click **Create payments**. Before choosing **Create payments**, you can right-click on the grid and export the list of invoices to Excel. **Create payments** creates the vendor payments in the payment journal.  
18. Confirm the method of payment is defined for all payments. If you generate the payments, such as printing a check or creating an electronic payment, the method of payment must be defined. The method of payment also defaults the bank account from the payment is made.  
19. Click **New** to create a one-off payment. A one-off payment can be added to a payment journal at any time prior to posting. Click **New** and add the payment information manually, rather than using the **Payment proposal**.  
20. Select the vendor to whom the payment will be made.
21. If an invoice exists to pay, select **Settle transactions** to select the invoice for payment. If this is a prepayment, this step is optional. You can create the payment without selecting any invoice. 
22. Mark any invoices that will be paid. If you use the **Settle transactions** to select the invoices for payment, the payment amount will automatically be calculated based on what invoices you mark for payment, and what amount you enter in the **Amount to settle**.
23. Click **OK**.
24. If you want to delete a payment, mark the row.
25. Click **Delete**. Deleting a payment only deletes the payment. Any invoices marked for payment are still available to be paid by another payment.
26. Click **Yes**.
27. Choose **Generate payment** to print checks or create the electronic payment file.
28. Select the method of payment that you want to generate. The payment journal can contain payments for both checks and electronic payments, but you can only generate one payment type at a time.
29. Select the bank account from which to generate the payments.
30. Click **OK**. Payments are only be generated for payments that match the **Method of payment** and **Bank account** you selected.
31. If you are generating **Checks**, choose **Document** to ensure the correct print destination for the checks.
32. Click **OK**.
33. Click **OK** to generate the payments.
34. Click **Post** if all the payments are approved and generated. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
