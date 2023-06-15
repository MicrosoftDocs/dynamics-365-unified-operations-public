---
title: Respond to requests for personal data in Human Resources
description: This article describes how you, as a data controller, can use Microsoft Dynamics 365 Human Resources as a data processor to help you respond to a request for data under the European Union's General Data Protection Regulation (GDPR).
author: shielasogge
ms.date: 02/28/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: shielas
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: AX 7.0.0
---


# Respond to requests for personal data in Human Resources

[!include [banner](../includes/banner.md)]

This article can help both businesses that use Microsoft Dynamics 365 Human Resources, and also partners and independent software vendors (ISVs), when they comply with data subject rights (DSR) requests. For more information about the European Union's General Data Protection Regulation (GDPR) and the related resources that Microsoft provides, see [General Data Protection Regulation overview](./gdpr-guide.md).

For Human Resources, Microsoft acts as a processor. As a data processor, Human Resources provides processes and features that let you comply with your GDPR obligations as a data controller.

## Rights

Data subjects have the following rights under the GDPR, and a data controller might take any of the actions that are listed under each right in response to a DSR request. 

### Right to view

+ Use the Person search report to find and collect personal data that is subject to a DSR request. For information about using this report, see the [Person search report](gdpr-person-search-report.md) article.  
+ Use advanced search and filters to find specific personal data and export that data by using the Microsoft Office Export functionality.
+ Extend the Person search report by adding an existing entity. For information that can help you extend the report, see [Extend the Person search report](gdpr-extend-person-search-report.md).

### Right to modify\*

+ Use advanced search and filters to find the data that should be corrected, and correct the data directly in Human Resources.

\* You might find that some data that qualifies as personal data can't be modified directly in the product or feature. Typically, this data is part of a financial transaction or other business data that is kept "as is" for compliance with financial laws (for example, tax laws), prevention of fraud (such as security audit trail), or compliance with industry certifications. As the controller, it's your responsibility to correct inaccurate or incomplete personal data.

### Right to be forgotten\*

+ You can delete or erase personal data where the product enables that action directly. As the controller, you should ensure any personal data that a data subject requests be erased does not conflict with other compliance obligations your organization may have around data retention, for example proof of payment or proof of tax.

\* You might find that some data that qualifies as personal data can't be modified directly in the product or feature. Typically, this data is part of a financial transaction or other business data that is kept "as is" for compliance with financial laws (for example, tax laws), prevention of fraud (such as security audit trail), or compliance with industry certifications. As the controller, it's your responsibility to correct inaccurate or incomplete personal data.

### Right to port
The following options are available to help you port personal data in response to a data rights request. 

+ Use the Microsoft Office Add-in to export personal data.
+ Author a custom report that enables the export of personal data.
+ Use or extend the Person search report to gather information in support of a request for a copy of the data subject's personal data.

### Right to restrict processing

+ Remove the employee from, for example, a course.
+ Following guidance from an organization's legal counsel, the company might refuse the right to restrict processing where data is needed by the company for compliance with other legal or industry mandates.

## Additional notes that apply to requests for personal data

+ Personal data that is found in Microsoft Power BI is generated from the information that is entered in Human Resources and then transferred to that application for reporting purposes. Any request for personal data should be fulfilled from the information in Human Resources, by using tools such as reports, Export to Excel, and the Person search report. You should not need to do additional reporting from Power BI to fulfill a DSR request. 
+ Human Resources doesn't export documents that are attached to records. These attachments must be manually downloaded and shared with the individual who has made the DSR.
+ If transactional data is associated with a master record, that record can't be deleted. 
+ Similarly, transactions that have been posted or completed can't be deleted.

### Reasons why certain personal data may not be modified or deleted in Human Resources

The following table lists several reasons why personal data modification or deletion is restricted in certain scenarios.

| Reason | Comment |
|--------|---------|
| Financial, tax, generally accepted accounting principles (GAAP) | A party can't be deleted, but the party's name can be updated. |
| Financial, tax, GAAP | A current worker's data can't be deleted, but the worker's name can be updated. | 
| GAAP | Posted or completed transactions can't be modified. |

## Additional information

Only terminated workers can be deleted from Human Resources. Follow these steps to delete terminated workers.

+ Delete position assignments. 

    To delete a position assignment, select **Position assignments** on the **Worker** page. Select **As of date** and select **Display all records**. Drill into the position number, select **Changes timeline** &gt; **Manage changes** &gt; **Position worker assignments**, and remove the position assignment record that is associated with the worker that you're deleting.

+ Delete fixed compensation.

    To delete fixed compensation, select **Employment history** on the **Worker** page. Select **Employment history** &gt; **Employment** &gt; **Fixed compensation**, and delete the fixed compensation plans for the worker.

+ Delete variable compensation enrollments.

    To delete variable compensation, select **Employment history** on the **Worker** page. Select **Employment history** &gt; **Employment** &gt; **Variable compensation plan enrollment** and delete the variable compensation plan enrollments for the worker.

+ Delete any associated checklists.

    To delete the checklists, select the **Checklists** option on the **Worker** page.+ Delete the Party in the Address book
    
+ Delete the Party in the Address book

     If the **Delete parties with no roles** option is selected on the **Global Address book parameters** page and the party is NOT associated to another role (ex: vendor, customer, contact) the associated party record will be deleted automatically when the worker is deleted. If this option isn't enabled, the user will need to manually delete the party in the address book. 

Compensation isn't assigned to contractors. Therefore, those steps can be skipped in the preceding process.


## Additional resources
You can learn more about the GDPR on the [European Union's website](https://europa.eu/) and on the [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx).



### Disclaimer
(c)2019 Microsoft Corporation. All rights reserved. This document is provided "as-is." Information and views expressed in this document, including URL and other Internet Web site references, may change without notice. You bear the risk of using it. This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
