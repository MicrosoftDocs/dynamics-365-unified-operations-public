---
# required metadata

title: GST project transactions
description:  
author: kfend
manager: AnnBe
ms.date: 07/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.scope: Core, Operations
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 7.3.1
ms.search.validFrom: 2019-7-02
---


# GST project transactions

[!include [banner](../includes/banner.md)]


## Project category
1. Go to **Project management and accounting** \> **Setup** \> **Categories** \> **Project categories.**
2. On the **Project** fast tab, in the **Service accounting code** field, select a value.
3.  Click **Close**.

## Project through approved project quotation
1. Go to **Project management and accounting** \> **Quotations** \> **Project quotations**.
2. Create a project quotation.

    ![](media/0160f30b8c8e1109f805d514bdbf1b7e.png)

3. Click **Tax information** button

    ![](media/70dd34b3973ef79f001c3804dfc0627b.png)

4. Click **OK**
5. On the Action Pane, on the **Quote** tab, in the **Tax** group, click **Tax
    document**.

![](media/1a57f9db40ffeb55410b96dc75c18475.png)

6. Close the form.

7. On the action Pane, Click **Workflow \> Submit**, to process the quotation
    through workflow

8. Update the comment and Click **Submit**

    **After the approval of the quotation**

4.  On the action Pane, click action pane **Quote \> Process \> Send
    quotation**.

5.  Click **OK**.

6.  On the action Pane, click action pane **Follow up \> Generate \> Confirm**.

7.  Click **OK**.

>   **Project contract**

1.  Go to **Project management and accounting \> Projects \> Project contracts**

2.  Create Project contract

3.  On the action Pane, on the **Project contract** tab, in the **Attachments**
    group, Click **Tax information** button.

    ![](media/9d215cfac16a9f3fc47b1b6ded8f957f.png)

    **Create Project**

4.  On the action Pane, on the **Maintain** tab, in the **New** group, click
    **Project**.

5.  Select **Project type** ‘Time and material’

6.  Enter **Project name**

7.  Select **Project group**

8.  Select **Project contract ID**

9.  Click **Create project**

10. On the action Pane, on the **Project** tab, in the **Setup** group, click
    **Tax information**.

    ![](media/ccbf4beae766b499f28af4c9d6a377bc.png)

11. Click **OK**.

**Expense journal**

1.  On the action Pane, on the **Project** tab, in the **Journals** group, click
    **Expense**.

2.  Create journal.

3.  Click **Lines.**

4.  Create project expense journal.

![](media/789a0ac935fb899b84dab14a59a0e8f9.png)

1.  Click **General** tab

2.  Click **Invoice** tab

3.  Enter **Invoice**

4.  Click menu item **Tax information \> Cost**

    ![](media/ebda0adb28b0272c8cd71c447250be16.png)

5.  Click **OK**

6.  Click menu item **Tax information \> Invoice**

    ![](media/8b307b0c88dee6e641e95d05e5bbc144.png)

7.  Click **OK**

8.  Click **Tax document**

    ![](media/418b7c0f07f8c12d2446e1bed3ded583.png)

9.  Close the form.

10. Click **Post \> Post**.

11. Click menu item **Inquiries** \> **Voucher**

| Ledger account name      | Debit amount (Rs.) | Credit amount (Rs.) |
|--------------------------|--------------------|---------------------|
| Purchases account        | 5,000.00           |                     |
| CGST recoverable account | 500                |                     |
| SGST recoverable account | 500                |                     |
| Vendor account           |                    | 6,000.00            |

1.  Close the form.

**Hour journal**

1.  On the action Pane, on the **Project** tab, in the **Journals** group, click
    **Hour**.

2.  Create journal.

3.  Click **Lines.**

4.  Create project hour journal.

    ![](media/e23ad52f54dfc437580c5d64317528c8.png)

5.  Click **General** tab

    ![](media/efd80326815f2d967bc05eb657779b2e.png)

6.  Save the record

7.  Click **Tax information**

    ![](media/0b2179736579e997a601b13d80fb7615.png)

8.  Click **OK**

9.  Click **Post**

10. Click **OK**

11. Close the form.

**Item journal**

1.  On the Action Pane, on the **Project** tab, in the **Journals** group, click
    **Item**.

2.  Create journal

3.  Click **Lines**

4.  Create journal

    ![](media/7e99eeb1a625626602cd38cc0e692a80.png)

5.  Click **Project** tab

    ![](media/c0c8d849fca4e6c2fd1f3e0ea8b309a5.png)

6.  Save the record

7.  Click **Tax information**

    ![](media/450f83146bbbc2221314b35c5767d381.png)

8.  Click **OK**

9.  Click **Post**

10. Click **OK**

11. Close the form.

**Fee journal**

1.  On the action Pane, on the **Project** tab, in the **Journals** group, click
    **Fee**.

2.  Create journal

3.  Click **Lines**

4.  Create journal line

5.  Click **General** tab

    ![](media/cc3c98a18fa4e48ad05266d2f6c81d04.png)

6.  Click **Tax information**

    ![](media/2edff88e2a4b9fd0f3711f76e2d022e0.png)

7.  Click **OK**

8.  Click **Post**

9.  Click **OK**

10. Close the form

**On-account transactions**

1.  On the Action Pane, on the **Manage** tab, in the **Bill** group, click
    **On-account transactions**.

2.  Click **New**

3.  Enter **Sales price**.

    ![](media/06bc73db7d2da73c285416b6e793d796.png)

4.  Click **Tax information**

5.  Click **GST** fasttab

6.  Select **SAC** code.

    ![](media/ffe8cc74c1e42484ee15a813f37dd545.png)

7.  Click **OK**

8.  Close the form.

**Project invoice proposal**

1.  On the Action Pane, on the **Manage** tab, in the **New** group, click
    **Invoice proposal**.

2.  Select the transactions.

3.  Click **OK**.

4.  Click **View details**.

5.  Click **Tax information**.

    ![](media/6be0a5a181e71c5fe864aafdb20eaf01.png)

6.  Click **OK.**

7.  Close the form.

8.  Click **Tax document.**

    ![](media/8917cd8ec518f087d1f42d646c37ab32.png)

9.  Close the form.

>   **Update additional Fee**

1.  Click **Create Fees**.

2.  Define the values.

3.  Click **OK**.

4.  Click **Fee** tab

5.  Select the Additional fee record and Click **View details**

6.  Click **Tax information.**

    ![](media/8994a9b397920f831aa67be9324e5fce.png)

7.  Click **OK.**

8.  Close the form.

9.  Click **Tax document**.

    ![](media/89ffce4d9834e9af20cc6a2446e6a837.png)

10. Close the form.

11. Click **Post**.

12. Click **OK**.

13. Click **OK**.

**Customer advance invoice**

1.  On the Action Pane, on the **Manage** tab, in the **Bill** group, click
    **Customer advance \> Request a customer advance**.

2.  Enter **Description**.

3.  Enter **Advance amount**.

4.  Click **OK.**

5.  Click **View details**.

6.  Click **Tax information.**

7.  Click **GST** fasttab.

8.  Select **SAC** code.

    ![](media/96ffe6e654b48633a5f5729ee6a6adc8.png)

9.  Click **OK**.

10. Close the form.

11. Click **Tax document**, to validate the tax computation.

12. Close the form.

13. Click **Post**.

14. Mark **Print invoice**.

15. Click **OK**.

16. Click **OK**.

>   **Validate Tax report**

![](media/156d8853fceeeec33e1169fb7814e8b1.png)

Service management
==================

1.  Go to **Service management \> Common \> Service agreements \> Service
    agreements**

2.  Create service agreement.

3.  Click **Create service orders**.

    ![](media/1d861ffc08e842dff419b52e495d299d.png)

4.  Click **OK**.

>   **Validate Service order**

1.  On the Action Pane, on the **Deliver** tab, in the **Service order** group,
    click View.

    ![](media/2cf0e0471801a1c0cb6ac10faf397f8d.png)

2.  Click **Edit**.

3.  On the action Pane, on the **Service order** tab, in the **Show** group,
    click Header view.

4.  Mark **Sign off** checkbox**.**

5.  On the Action Pane, on the **Dispatch** tab, in the **Service stage** group,
    click Next stage.

6.  On the Action Pane, on the **Invoice** tab, in the **Post** group, click
    Service order.

    ![](media/aed75a960b5096bbbb34b2bb47640c3a.png)

7.  Click **OK.**

>   **Project Invoice proposal**

1.  On the action Pane, on the **Invoice** tab, in the **Related information**
    group, click **Project invoice proposals**.

2.  Click **New \> Invoice proposal**.

3.  Select **Project** and Click **Search.**

4.  Click **OK.**

5.  Click **Post**.

6.  Click **OK**.

7.  Click **OK**.
