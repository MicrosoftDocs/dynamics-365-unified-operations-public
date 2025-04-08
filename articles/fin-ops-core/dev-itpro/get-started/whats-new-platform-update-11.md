---
title: What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 11 (October 2017)
description: Learn about new or changed features in Dynamics 365 Finance and Operations, Enterprise edition platform update 11. This version was released in October 2017.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-09-30
ms.dyn365.ops.version: Platform update 11 
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 11 (October 2017)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 11. This version was released in October 2017 and has a build number of 7.0.4679.35176.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 11, log in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4047244&bugId=3869536&qc=310ad7de90642ce961cc3f51358f3b40788c975dec466891d0fcc17c13145f56).

## Attachment presence and document count indicator

When viewing a record, the system will indicate the number of attachments on that record by showing a count on the Attachments button. This number will indicate that there are attachments associated with the record, without having to navigate to the attachment details form. The count will show up to 9 attachments, with more than 9 attached documents being represented as "9+". For more information, see [Configure document management](../organization-administration/configure-document-management.md).

## Auditing

Auditing of user sign in and sign out is now enabled in Finance and Operations. The system logs when a user signs in or out of the application. A sign out is logged even if the user's session expires or ends.

A system administrator or security administrator can access the audit logs by going to the **User log** page (**System administration** \> **Inquiries** \> **User log**).

## Bring your Own Database (BYOD) support for delete operations

Bring your own data store (BYOD) is a feature that's used by customers to integrate data from Finance and Operations with existing data warehouses. BYOD allows you to incrementally export data into a customer's SQL Azure database. While an incremental export feature is ideal for propagating changes, we will also support full export, which is typically used for initial data population. Incremental operation propagates insert and update operations to the destination database. With this addition, BYOD incremental refresh operations delete records in the destination database if corresponding records are deleted in source.

## Cloud and Edge elements

The metadata properties, **Operational domain** and **Subscriber access level** have been added for tables, views, data entities, menu items, and service operations. The new metadata properties are needed to support [Cloud and Edge deployments](https://community.dynamics.com/b/msftdynamicsblog/archive/2017/02/23/the-right-cloud-option-for-your-business), and are visible in Microsoft Visual Studio.

Additionally, three tables, **Deployment**, **DeploymentAccessibleCompany**, and **NumberSequenceDeployments** have been added, for the same purpose.

At this time, you are not required to uptake the new properties and tables.

## Copy legal entity configurations to a new legal entity

As new companies are needed, users will be able to save time and potential errors by copying an existing legal entity's setup to the new company. This will allow the onboarding of a new location to be quick and consistent with the company's golden template design.

## Development and customization - Field groups - Extension of another extension

Consider you have a table (Table1) that has two extensions in 2 separate models: TableExtension1 and TableExtension2. TableExtension1 contains a new field group (NewFieldGroup1). Using TableExtension2, you can now add a field to NewFieldGroup1. If you add NewFieldGroup1 to a form extension, all fields are recognized and rendered at runtime by the user interface. This functionality was not available prior to Platform update 11.

## Development and customization - Support for display and edit methods in class extensions

You can now use class extensions (table class extensions) to define display and edit methods. The following example illustrates this.

Create an extension of the table LedgerJournalTransAccrual and add a new string field named **MyStringField1** to the table. Augment the table class LedgerJournalTransAccrual as follows.

```
[ExtensionOf(tableStr(LedgerJournalTransAccrual))]
final class MyLedgerJournalTransAccrual_Extension
{
    [SysClientCacheDataMethodAttribute(true)]
    public static display LedgerJournalAccountName
    MyLedgerAccountName(LedgerJournalTransAccrual \_ledgerJournalTransAccrual)
    {
        return \_ledgerJournalTransAccrual.MyStringField1 + "Hello";
    }
}
```

Add a new field group to the table extension of **MyLedgerAccountName** and select the method **MyLedgerAccountName** as a display data field in the field group. 

1. Add a new field group.
2. Add a new field to the field group.
3. Set the **Data Field** property to **LedgerJournalTransAccrual\_Extension::MyLedgerAccountName**. (You can type it in or select it from the **Data Field** drop-down list).

## Development and customization - Support for field arrays in table extensions

When you extend a table and add a new field to the table extension, if the new field is of type EDT that is an array, you can now access EDT array fields from X++ code. Here is an example of how to do this.

1. Create a table extension.
2. Add a new field to the table extension.
3. Set the field type to an EDT that is an array.
4. Use the new extension field in X++ as follows.

```
A table1;
table1.EDTArrayField1[1] = 'text1';
table1.EDTArrayField1[2] = 'text2';
table1.EDTArrayField1[3] = 'text3';
// perform insert or update operations here on table 1
```

## Development and customization - Use EDT extensions to customize number of decimals

When you use an extension of an extended data type of type EDTReal, you can know change the decimal point precision. If the EDT element you are extending has the property **Number of Decimals is Extensible** set to True, you can create an extension of this EDT and modify the **No of Decimals** property. This allows developers to customize the decimal point precision of an EDT of type EDTReal. As of Platform update 11, the following EDTs allow decimal point extension: Amount and AmountMST.

## Multiple document reports sent as a .zip file to streamline delivery

The framework has been extended to better handle scenarios where reporting sessions produce multiple documents for download. As a security precaution, the Dynamics 365 Finance and Operations service has adjusted how to handle scenarios that download multiple files to the browser. Instead of receiving multiple documents, one after another, the documents will be packaged and downloaded in a single .zip file. This will affect existing reports that produce multiple documents such customer account statements and collection letters.

## Resource governor manages server workloads

Resource governor is a component that reduces the management overhead for a system administrator. Finance and Operations contains batch and processing tasks that are compute intensive. Users can schedule many jobs as the business demands dictate, such as the month-end workload where there are multiple posting jobs. While these compute processes occupy the server, interactive operations such as front-office processes, continue to run without any degradation of performance.

Resource governor uses the built-in resource governance services offered by SQL Azure database. Dynamics 365 Finance and Operations Runtime service allocates quotas for interactive, as well as batch processes, so that SQL Azure database (where most of the compute is performed) does not degrade if there are sudden compute spikes.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
