---
# required metadata

title: Automate vendor payment proposals
description: Organizations that pay vendors on a recurring schedule can now automate the process of generating vendor payment proposals. 
author: kweekley
manager: AnnBe
ms.date: 04/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 262034
ms.assetid: 9db38b3f-26b3-436e-8449-7ff243568a18
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-04-08
ms.dyn365.ops.version: 10.0.11

---

# Automate vendor payment proposals

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Organizations that pay vendors on a recurring schedule can now automate the process of generating vendor payment proposals. The payment proposal automation defines the following things: 

 - When payment proposals are run
 - What criteria is used to select the invoices to pay
 - What vendor payment journal the resulting payments are saved in.  

The payment proposal automation does not automatically post the payments, which lets you continue using any validation and workflow processes you have for approving the payments that are created. 

## Define vendor payment proposal occurrence
The vendor payment proposal automation uses the Process automation framework.  The Process automation is used by different business processes to define the recurrence of the selected process. For vendor payment proposal, the automation can be accessed under **Accounts payable – Payment setup – Process automation**.

Begin by using the Create new process automation option and select Vendor payment proposal. A wizard will open to lead you through the process of setting up the vendor payment proposal. 

## General page in wizard
Enter the Name of the vendor proposal you are creating.  For example, if you pay all domestic vendors by check on Monday, enter a descriptive name such as Domestic_Check.  The name displays on the process automation weekly view, which is on the **Vendor payment** workspace. 

Define the owner of the payment journal that is created. This is usually the AP payment clerk, who is responsible for the payment journal after it’s created.  

The remaining settings are generic to the process automation and are used to define the recurrence pattern used for this version of the vendor payment proposal.  For example, if this occurrence is for check payments on Monday, you could define the occurrence to run **Weekly**, and select Monday as the day of the week when it runs. Also, enter an early Schedule time such as 2:00 am so the process automation will be complete by the start of the next business day. 

It’s important to understand that you’re setting up the wizard to define when to process the vendor payment proposal. You don’t use the wizard to define when the vendor payments are actually generated, printed, and posted. The vendor payment proposal process automation will display in the weekly view on the days marked in the occurrence pattern. 

Refer to the Process automation documentation for more information about the other fields found on the **General** tab.  

### General page in wizard
Enter the Name of the vendor proposal you are creating.  For example, if you pay all domestic vendors by check on Monday, enter a descriptive name such as Domestic_Check.  The name displays on the process automation weekly view, which is on the **Vendor payment** workspace. 

Define the owner of the payment journal that is created. This is usually the AP payment clerk, who is responsible for the payment journal after it’s created.  

The remaining settings are generic to the process automation and are used to define the recurrence pattern used for this version of the vendor payment proposal.  For example, if this occurrence is for check payments on Monday, you could define the occurrence to run **Weekly**, and select Monday as the day of the week when it runs. Also, enter an early Schedule time such as 2:00 am so the process automation will be complete by the start of the next business day. 

It’s important to understand that you’re setting up the wizard to define when to process the vendor payment proposal. You don’t use the wizard to define when the vendor payments are actually generated, printed, and posted. The vendor payment proposal process automation will display in the weekly view on the days marked in the occurrence pattern. 

Refer to the Process automation documentation for more information about the other fields found on the **General** tab.  

## Vendor payment proposal page in wizard
The vendor payment proposal page is next in the wizard and is used to define the criteria for selecting the vendor invoices to pay.  Most options are the same as found in the payment proposal on the vendor payment journal, with a few exceptions.  For example, all dates must be defined as relative dates since the payment proposal date changes each time the proposal is run.  

### Journal name
The **Journal name** field defines the journal name into which to create the vendor payments.  The results of the vendor payment proposal automation will create payments in the defined journal, but the journal does not post. 

### From date and To date
Rather than defining a From date and To date for selecting invoices based on the due date or cash discount date, you must use the **Define to date criteria** and **Number of days adjustment for To date** fields to define the To date. There is no concept of a from date in the payment proposal automation.

If you accept the default entry, No, in the **Define to date criteria** field, the process will select all invoices to pay when the process is run because no To date has been defined. 

If you set **Define to date criteria** field to Yes, use the **Number of days adjustment for To date** field to define the number of days before or after the date that the process runs on for selecting invoices. The number can be positive, negative or zero. The system will then pay invoices whose due dates, or cash discount dates, follow or precede the date the process runs on by that number of days. For example, if this payment series creates payments to all vendors by check on Wednesday for all invoices that are due through Friday, set this field to 2. When the occurrence of the payment proposal is run on Wednesday, March 25th, all invoices with a due date or cash discount date on or before March 27th will be selected for payment. 

### Minimum payment date
The minimum payment date is used to define the earliest date used when creating payments. You must first set **Define minimum payment date criteria** to Yes. This setting lets you use the minimum payment date functionality.  If this field is yes, define **Number of days adjustment for minimum payment date** as the number of days before or after the day that the process is run to use as the minimum payment date. The number can be positive, negative or zero.  For example, if this series generates payment on Wednesday with the intention of including all payments that have a minimum payment date of the preceding Monday, set this field to -2.

Assume the payment proposal automation is defined to run on Wednesday. The To date value of 1 is entered in the **Number of days adjustment for To date** field, based on the due date and the value of -2 in the **Number of days adjustment for minimum payment date** field. If the payment process automation starts on Wednesday, March 25, all invoices that are due on or before March 26 will be included in the payment proposal. Payment proposals will be generated as follows. 

 - All invoices that are due on or before March 23, will have a payment date of March 23  
 - Invoices that are due on March 24, will have a payment date of March 24
 - Invoices that are due on March 25, will have a payment date of March 25
 - Invoices that are due on March 26 will have a payment date of March 26 

### Summarized payment date
The summarized payment date is only used when the method of payment on the invoices is defined by setting the **Period** field to **Total**. If your methods of payment are set up as Total, you must set the **Define summarized payment date criteria** to Yes. If this field is set to yes, enter the number of days before or after the day that processing is run to use as the summarized payment date. Enter this value in the **Number of days adjustment for summarized payment date**field. The number can be positive, negative or zero. For example, if this series generates payment on Wednesday and the company wants to create a summarized payment on Wednesday, set this field to 0.

### Records to include
The Filter options can still be defined on the payment proposal.  If a filter is defined, the filter criteria doesn’t display on the wizard page, but can be viewed by reopening the Filter.  

The remaining fields on the proposal work the same as on the payment proposal on the vendor payment journal.  See Create vendor payments by using payment proposal for information about the other fields. 

 > [!Note]
 > Some country-specific fields, as well as some Public sector fields, are not yet available in the vendor payment proposal automation. 

We recommend that you evaluate whether the automation will beneficial to your organization, based on your requirements. 

## View results for vendor payment proposal automation
After the vendor payment proposal automation series is created, the occurrences for each payment can be seen on the process automation weekly view.  For vendor payments, the process automation weekly view has been added to the **Vendor payments** workspace, as well as to the **Process automation** page. 

*Two illustrations go here*

The process automation weekly view shown here will display only vendor payment proposal automations.  It will show all occurrences of payments for the current week, for all legal entities that user has security to.  For example, if the AP payment clerk is responsible for payments in companies USMF and USSI, they will see the vendor payment proposal automation occurrences for those two companies, but not other companies. 

Each occurrence will display various pieces of information. 

 - Each occurrence displays the company that the payment journal was, or will be, created in.  
 - If payments are created using centralized payments, the company displayed is the company that payments will be created in, and not necessarily which companies’ invoices will be paid

The name of the payment proposal occurrence is also shown to provide context that identifies the  payment proposal that’s displayed.

The state for each occurrence is shown to make it easier to see the status of the occurrence.

 - Scheduled – The payment proposal is scheduled but hasn’t executed yet.
 - Error – The payment proposal has run but an error resulted. The errors can be viewed by choosing the View results button.
 - Completed – The payment proposal has successfully run.  The payments can be viewed by clicking the View payments hyperlink. This will open the payment journal created by the automation occurrence. 
 
After the payments are created, you can see the payment amounts in the journal. The amounts are shown in the transaction currencies. For example, if the payment journal contains payments in both the US and Canadian dollars, the total payments for each currency are shown.  
The payment journal can be deleted after it’s created through the process automation. If a payment is completely deleted, the following things happen. 

 - The process automation view for the week will remain in a **Completed** state
 - The process swill remove the payment totals and the **View payments** link will be replaced with a **View results** button
 - A message indicating that the original journal was deleted will be displayed when you view the results 

The invoices will be open again for payment.  A new occurrence can be created to pay the invoices again. 

## Edit vendor payment proposal automation
The process automation framework lets you edit the payment the series, and the occurrences created for the payment proposal. The series can be edited from either the **Process automation** page or the process automation weekly view.  For example, suppose the AP manager decides to generate all check for domestic vendors on Wednesday instead of Monday. The manager can find an occurrence on the weekly view and select **View/Edit – Series**.  If a series is changed, the system will prompt you to indicate whether the change should be made to all existing occurrences, or only the new occurrences.  Historical occurrences that are already **Completed**, or that end in an **Error** status will not be changed. 

You can also add a new occurrence or change an existing occurrence. For example, suppose the next payment proposal occurrence is scheduled to run Wednesday, January 1, which is a holiday.  You can change the occurrence from the process automation weekly view or from the Process automation page.  A page will open with the schedule details and payment proposal criteria lets you edit the scheduled time and date, as well as the payment proposal criteria, if necessary. For example, if you change the date of the payment occurrence on January 1, to January 2, you might also want to change the relative dates for the To date as a result of changing the scheduled date. 
You can also disable an occurrence or series. Select an occurrence on the weekly view and select Disable to suspend processing that occurrence. The series can be disabled on the Process automation page.

## Security for payment proposal automation
The following duties and privileges have been added for the vendor payment proposal automation. These are the default security settings, but they can be changed based on your organization’s requirements. For example, if the AP payment clerk can edit and create schedule occurrences as well as the AP manager, then assign the Maintain schedule occurrences duty to the person in the AP payment clerk role. 

|                   Duty                  |    Role                                                                               |    Privileges                                                                                                                                                                                                                                                                                           |
|:---------------------------------------:|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Maintain schedule series             |    Accounts payable manager                                                           |    This duty allows the creation and maintenance of the payment proposal   automation series and occurrences through the following privileges:       - Maintain schedule occurrences   - Maintain schedule series   - ProcessScheduleOccurrenceListMaintain   - View the occurrences weekly view        |
|    Inquiry into schedule occurrences    |    Accounts payable payment clerk       Accounts payable Centralized payment clerk    |                                                                                                 ﷒          This duty allows the rights to view the   payment proposal automation occurrences through the following privileges:   - View schedule occurrences   - View the occurrence weekly view        |
|    Inquire into schedule series         |    <none>                                                                             |                                                                                This duty allows the rights to view the series and occurrences setup   through the following privileges:       - View schedule occurrences   - View the occurrences list page   - View the occurrence weekly view        |
|    Maintain schedule occurrences        |    <none>                                                                             |                                                                                                                         This duty allows the creation and maintenance of an occurrence through   the following privileges:   - Maintain schedule occurrences   - View the occurrence weekly view        |
