# (RUS) Create a purchase book 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

A purchase book is a tax accounting document. In a purchase book, you can record vendor factures, factures on returns and credit notes to vendors, factures on advance reports from advance holders, factures on customer prepayments, and corrected tax transaction factures.


> [!NOTE]
> <P>This topic has not been fully updated for Microsoft Dynamics AX 2012 R2.</P>



1.  Click **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.

2.  Click the **Statutory reporting** FastTab and, in the **Report Folder** field, specify the folder that contains the purchase book template.

3.  Close the form.

4.  Click **Accounts payable** \> **Setup** \> **Accounts payable parameters**.

5.  Click **Number sequences**, and in the **Number sequence code** field, select the number sequence for the reference type **Purchase book**.

6.  Close the form.

7.  Click **Accounts payable** \> **Periodic** \> **Purchase book** \> **Purchase books journal**.. A list of previously created purchase books is displayed in the form.

8.  Create a new purchase book.
    

    > [!NOTE]
    > <P>The <STRONG>New</STRONG> button is available only if all books that are listed in the form are closed. The <STRONG>Code</STRONG> field is updated automatically based on the purchase book numbering sequence.</P>



9.  In the **Name** field, enter a name for the book.

10. Click **Update** to open the **Purchase book** form.
    

    > [!NOTE]
    > <P>You can only update an open book.</P>



11. In the **To date** field, select the end date of the settlement period for which the purchase book is updated.
    

    > [!NOTE]
    > <P>When you create the first book, you can set only the end date. The dates cannot be edited for later books. The <STRONG>From date</STRONG> and <STRONG>To date</STRONG> fields are determined by the tax settlement period.</P>



12. Select the **Close the book** check box to close the book after the update.

13. Click **OK** to create a new purchase book. The lines of the purchase book are refreshed, and the closing date is saved in the **Closed date** field of the book in the **Purchase books journal** form.
    

    > [!NOTE]
    > <P>Click <STRONG>Delete</STRONG> to delete a purchase book. Only the last book can be deleted regardless of whether it is closed or not.</P>



14. Click **Print** \> **Purchase book** to print the purchase book in the internal report.
    

    > [!NOTE]
    > <P>In the <STRONG>Purchase books journal</STRONG> form, click <STRONG>Lines</STRONG> to open the <STRONG>Purchase book lines</STRONG> form to verify purchase book line details.</P>


  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

# (RUS) Create an additional page in a purchase book 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_


> [!NOTE]
> <P>This topic has not been fully updated for Microsoft Dynamics AX 2012 R2.</P>



When you correct transactions for a closed tax period, an additional page is created in the closed purchase book to represent the tax period of the adjustment. Corrected factures are displayed in the new page in the purchase book.

The additional page contains information about purchase book totals at the end of the corrected period, including previous additional pages, corrected factures, and other registered changes.

1.  Click **General ledger** \> **Journals** \> **General journal**.

2.  Press CTRL+N to create a new line, and enter the required details.

3.  In the **Account type** field, select **Ledger**.

4.  In the **Account** field, select the ledger account number.
    

    > [!NOTE]
    > <P>The ledger account must be specified with the <STRONG>Sales tax</STRONG> posting type.</P>



5.  In the **Debit** field, enter the corrected debit amount.

6.  In the **Offset account type** field, select **Ledger**.

7.  In the **Offset account** field, select the ledger offset account number.

8.  Click the **General** tab. In the **Sales tax code** field, select the sales tax code for the transaction.
    

    > [!NOTE]
    > <P>The ledger account specified in the <STRONG>Account</STRONG> field on the <STRONG>Overview</STRONG> tab must belong to the accounting posting group of the selected sales tax code.</P>



9.  Click **Post** \> **Post** to post the journal voucher.

10. In the **Journal voucher** form, click **Functions** \> **Purchase book** to open the **Update facture** form.

11. In the **Counteragent** field, select the vendor.

12. In the **Date of the registration** field, select the registration date of the corrected facture.

13. In the **Facture** field, select the corrected facture from the vendor factures page, as specified in the **Counteragent** field.

14. In the **Facture date** field, view the facture creation date.
    

    > [!NOTE]
    > <P>The corrected book code is determined by the date of the corrected period. Previous period modifications are registered in the book for the current period. These modifications are displayed on additional pages that are added to the books for previous periods.</P>



15. In the lower section of the form, on the **Invoice** tab, use the **To facture** check box to select the invoice or invoices for the facture.
    

    > [!NOTE]
    > <P>If you do not want to create a facture for a particular invoice line, clear the <STRONG>To facture</STRONG> check box on the <STRONG>Invoice lines</STRONG> tab.</P>



16. Click **Posting** \> **Update facture** to post the facture journal.
    

    > [!NOTE]
    > <P>The created facture is updated in the <STRONG>Facture journal</STRONG> form. After VAT is processed and the purchase book lines are refreshed, the corrected facture is displayed in the <STRONG>Purchase book lines</STRONG> form. The <STRONG>Correction</STRONG> field group displays the details about the corrected facture.</P>



17. Click **Accounts payable** \> **Periodic** \> **Purchase book** \> **Purchase books journal** to open the **Purchase books journal** form.

18. Select the additional page and click **Print** \> **Print additional list** to print the page.
    

    > [!NOTE]
    > <P>Corrected purchase book lines are included in the additional pages. Other additional pages are created if other tax periods were corrected in the current reporting period.</P>
    > <P>The purchase book can be printed in a Microsoft Office Excel template.</P>



## See also

[(RUS) Purchase books journal (form)](https://technet.microsoft.com/en-us/library/jj853172\(v=ax.60\))

[(RUS) Facture journal (form)](https://technet.microsoft.com/en-us/library/jj923567\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).


# (RUS) Create a sales book 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

VAT debt accrual is generated according to sales book entries. All factures for sales of goods, services, and advance payments from customers are included in the sales book.


> [!NOTE]
> <P>This topic has not been fully updated for Microsoft Dynamics AX 2012 R2.</P>



1.  Click **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.

2.  Click the **Statutory reporting** FastTab and, in the **Report Folder** field, specify the folder that contains the purchase book template.

3.  Close the form.

4.  Click **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.

5.  Click **Number sequences**, and in the **Number sequence code** field, select the number sequence for the reference type **Sales book**.

6.  Close the form.

7.  Click **Accounts receivable** \> **Periodic** \> **Sales book** \> **Sales books journal**. A list of previously created sales books is displayed in the form.

8.  Create a new sales book.
    

    > [!NOTE]
    > <P>The <STRONG>New</STRONG> button is available only if all books that are listed in the form are closed. The <STRONG>Code</STRONG> field is updated automatically, based on the sales book numbering sequence.</P>



9.  In the **Name** field, enter a name for the book.

10. Click **Update** to open the **Sales book** form.

11. In the **To date** field, select the end date of the settlement period for which the sales book is updated.
    

    > [!NOTE]
    > <P>When you create the first book, you can set only the end date. The dates cannot be edited for later books. The <STRONG>From date</STRONG> and <STRONG>To date</STRONG> fields are determined by the tax settlement period.</P>



12. Select the **Close the book** check box to close the book after the update.
    

    > [!NOTE]
    > <P>After you create and close the book, you cannot remove factures from the closed book. You cannot create new factures in a closed period.</P>



13. Click **OK** to create a new sales book. The lines of the sales book are refreshed, and the closing date is saved in the **Closed date** field of the book in the **Sales books journal** form.
    

    > [!NOTE]
    > <P>Click <STRONG>Delete</STRONG> to delete a sales book. Only the last book can be deleted regardless of whether it is closed or not.</P>



14. Click **Print** \> **Sales book** to print the sales book in the internal report.
    

    > [!NOTE]
    > <P>In the <STRONG>Sales books journal</STRONG> form, click <STRONG>Lines</STRONG> to open the <STRONG>Sales book lines</STRONG> form to verify the sales book line details.</P>


  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

