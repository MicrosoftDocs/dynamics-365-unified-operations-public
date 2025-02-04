---
title: What's new or changed in Dynamics 365 for Finance and Operations platform update 15 (March 2018)
description: Learn about new or changed features in Dynamics 365 for Finance and Operation platform update 15. This version was released in March 2018.
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
ms.dyn365.ops.version: Platform update 13, Platform update 14, Platform update 15 
ms.assetid: a765d51c-52d3-45c5-b578-63b5242c592a
---

# What's new or changed in Dynamics 365 for Finance and Operations platform update 15 (March 2018)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Finance and Operations platform update 15. This version was released in March 2018 and has a build number of 7.0.4841.

> [!NOTE]
> This platform release is cumulative. It contains new or changed features from Platform update 13, Platform update 14, and Platform update 15, as well as all earlier updates.

### Announcing the Dynamics 365 Spring '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Download the Spring '18 release notes](https://download.microsoft.com/download/1/C/0/1C0A4DB7-9CE8-4D25-AC7F-65579E713BA8/ReleaseNotes_Dynamics365_03192018.pdf). We've captured all the details, end to end, top to bottom, in a single PDF that you can use for planning.

### Platform update 15 bug fixes

For information about the bug fixes included in Platform update 15, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=869898).

## Ability to color grid rows without overlayering via FormDataSource OnDisplayOptionInitialize event

The ability to color grid rows without overlayering is now possible via the OnDisplayOptionInitialize event on FormDataSource.

## Accessibility support for controls and forms developed using the cloud platform

Reaffirming our commitment to providing accessible software, this update focuses on broadening our already rich accessibility feature set. These updates improve many platform components such as grids, tables, and forms to comply with Microsoft's Accessibility Standards. With additional support for performing tasks via the keyboard, there is richer integration with screen readers, high contrast theming and full label support, and applications built using the cloud platform which provides additional opportunities for users with disabilities.

## Client-based alerts

Client-based alert functionality enables a user to define an alert rule without leaving the Finance and Operations client. Users can define alerts based on business events, such as when an invoice is paid or a customer changes an address. When specific conditions are met, the system will show a notification to alert the user.

Alerts form a notification system for critical events in Dynamics 365 for Finance and Operations. You can use alerts to stay informed about events that you want to keep track of during the workday. You can also easily set up your own set of rules so that you are alerted about overdue deliveries, orders that are deleted, prices that change, or other events that you must respond to.

For more information about alerts, see [Alerts overview](../../fin-ops/get-started/alerts-overview.md).

## Data entity behavior with configuration keys

Data management honors the configuration key settings on data entities, tables, and fields. Because of the hierarchical structure of these artifacts, data management will allow a child in the hierarchy to be used if the configuration key on itself and its parent is enabled. If a parent's configuration key is disabled, none of the children will be made available for use in imports and exports. For a detailed explanation of this behavior, see [Configuration keys and data entities](../../fin-ops/data-entities/config-key-entities.md)

## Embed Power Apps

Microsoft Power Apps, a service that allows developers and nontechnical users to build custom business apps without writing code, is now supported. You can add an embedded PowerApp to a page as well as edit, delete, or share the embedded PowerApp. You can also build a PowerApp to leverage data from Finance and Operations. For more information, see [Embed Power Apps](embed-power-apps.md).

## Extension and overlayering options in Visual Studio

In this release we have adjusted how the extension and overlayering options are presented in Visual Studio. The extension options are now shown first and the overlayering option has changed from "Customize" to "Overlayer" to be more explicit.
Extensions should be used whenever possible.

The customization options are now shown in the recommended order of use:

1. Create extension
2. Create extension in new project
3. Overlayer

## Message Center has been upgraded to the new Action Center with improved notification visuals and capabilities

The Message Center has been upgraded to the new Action Center. Not only have the visuals been refreshed to reflect a more modern notification interface, but messages sent to the Action Center using the new messaging API also come with additional capabilities including notification persistence, the ability to specify one or more actions associated with a message, and the ability to send a message to a list of users or a list of roles. All existing messages that were routed to the Message Center will automatically be surfaced in the Action Center.

## Move master data from one environment to another using the Excel add-in

Dynamics 365 Talent provides "getting started" workbooks so users can use Excel to interactively view, edit, and create data. These workbooks, powered by the Excel add-in, provide a productive environment configuration experience. With this enhancement, you can move data from one environment to another by reading data into Excel from one environment, change the environment address, and then publish the data into the new environment.

For more information, see [Copy environment data](../../fin-ops/mobile-apps/use-excel-add-in.md#copy-environment-data).

## Power users can add custom fields to forms without developer customization

Many application customizations involve adding one or more fields to existing tables and including them in application forms. Most of your customizations may be composed of adding fields.

Customizations are expensive because they require developer intervention for development, test, and code life cycle management. Customizations also need to be managed and migrated from one environment to another.

We have made it easier to add custom fields to forms in Dynamics 365 for Finance and Operations. Developer customization is no longer needed. Instead, a power user can add a custom field to a table and then place that field on the form using personalization. An IT administrator can then share the personalization with others in your organization. For information about how to create and manage custom fields, see [Create and work with custom fields](../../fin-ops/get-started/user-defined-fields.md).

## (SR 10) Certifications for Dynamics 365 for Finance and Operations

**ISO 27001(Secure)** – ISO 27001 certification confirms that the service complies with the controls and specifications outlined in the information security management system (ISMS). By achieving ISO 27001, this helps to ensure that our service is secure for you to run your business on. This also helps to support your efforts to certify your own business, if you choose to do so, by reassuring your auditors that you are running your business on an ISO27001 certified service.

**ISO 27018 (Protects personal data)** – ISO 27018 focuses on protection of personal data in the cloud. Dynamics 365 for Finance and Operations has achieved ISO 27018 certification. We want you to know that when you are using our service to manage your business, your personal and sensitive data is safe and protected in the cloud. Additionally, if you choose to gain your own ISO 27018 certification for your business, your auditors will appreciate that Finance and Operations has ISO 27108 certification. 

**SOC-1/Type-2 and SOC-2/Type-2** – The service organization controls report (SOC) helps to confirm that a cloud service has controls in place to ensure that financial data is secure and protected. Finance and Operations has achieved SOC-1/Type-2 and SOC-2/Type-2 certification.

## Support for display and edit methods on form data sources using augmentation classes (ExtensionOf)

The following examples use Display/Edit methods on augmented classes for tables and forms.

#### Class extension for a form

```xpp
[ExtensionOf(formstr(abForm))]
public final class abClassForm_Extension
{
    private Name previousName;
    private Counter noOfChanges;

    public display Name formExt_Display()
    {
        return previousName;
    }

    public edit Name formExt_Edit(boolean _set, Name _value)
    {
        if (_set)
        {
            noOfChanges++;
            previousName = strFmt("%1 %2", _value, noOfChanges);
        }

        return previousName;
    }
}
```

#### Class extension for a table

```xpp
[ExtensionOf(tablestr(abTable))]
public final class abClassTable_Extension
{
    public display Name tableExt_Display()
    {
        return "tableExt_Display " + this.FirstName + " " + this.LastName;
    }

    public edit Name tableExt_Edit(boolean _set, Name _value)
    {
        if (_set)
        {
            this.FirstName = "tableExt_Edit " +_value;
        }

        return this.FirstName;
    }
}
```

The form or form extension can then consume the display and edit methods from a form control by providing the **\<ClassName\>.\<MethodName\>** in the DataMethod property.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
