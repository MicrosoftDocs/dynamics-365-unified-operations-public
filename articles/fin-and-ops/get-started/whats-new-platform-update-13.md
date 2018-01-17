---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 13 (January 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 13. This version was released in January 2018.
author: tonyafehr
manager: AnnBe
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: a764d51c-42d3-47c5-b388-63b8218c692a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-09-30 
ms.dyn365.ops.version: Platform update 13 

---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 13 (January 2018)

[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 13. This version was released to public preview in January 2018 and has a build number of 7.0.4764. Platform update 13 was released to public preview only and isn't generally available.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 13, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=865988).

(SR 10) Certifications for Dynamics 365 for Finance and Operations, Enterprise edition 
---------------------------------------------------------------------------------------

**ISO 27001(Secure)** – ISO 27001 certification confirms that the service
complies with the controls and specifications outlined in the information
security management system (ISMS). By achieving ISO 27001, this helps to ensure
that our service is secure for you to run your business on. This also helps to
support your efforts to certify your own business, if you choose to do so, by
reassuring your auditors that you are running your business on an ISO27001
certified service.

**ISO 27018 (Protects personal data)** – ISO 27018 focuses on protection of
personal data in the cloud. Dynamics 365 for Finance and Operations, Enterprise
edition has achieved ISO 27018 certification. We want you to know that when you
are using our service to manage your business, your personal and sensitive data
is safe and protected in the cloud. Additionally, if you choose to gain your own
ISO 27018 certification for your business, your auditors will appreciate that
Finance and Operations has ISO 27108 certification. 

**SOC-1/Type-2 and SOC-2/Type-2** – The service organization controls report
(SOC) helps to confirm that a cloud service has controls in place to ensure that
financial data is secure and protected. Finance and Operations has achieved
SOC-1/Type-2 and SOC-2/Type-2 certification.

## Ability to color grid rows without overlayering via FormDataSource OnDisplayOptionInitialize event
The ability to color grid rows without overlayering is now possible via the OnDisplayOptionInitialize event on FormDataSource.

Accessibility support for controls and forms developed using the cloud platform 
--------------------------------------------------------------------------------

Reaffirming our commitment to providing accessible software, this update focuses
on broadening our already rich accessibility feature set. These updates improve
many platform components such as grids, tables, and forms to comply with
Microsoft’s Accessibility Standards. With additional support for performing
tasks via the keyboard, there is richer integration with screen readers, high
contrast theming and full label support, and applications built using the cloud
platform which provide additional opportunities for users with disabilities.

## Changed how extension and overlayering options are presented in Visual Studio
In this release we have adjusted how the extension and overlayering options are presented in Visual Studio. The extension options are now shown first and the overlayering option has changed from "Customize" to "Overlayer" to be more explicit.
Extensions should be used whenever possible. 

The customization options are now shown in the recommended order of use:
1.	Create extension
2.	Create extension in new project
3.	Overlayer

Move master data from one environment to another using the Excel add-in 
------------------------------------------------------------------------

Dynamics 365 for Talent provides “getting started” workbooks so users can use
Excel to interactively view, edit, and create data. These workbooks, powered by
the Excel add-in, provide a productive environment configuration experience.
With this enhancement, you can move data from one environment to another by reading data into Excel from one environment, change the environment address, and then publish the data into the new environment.

For more information, see [Copy environment data](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in#copy-environment-data).

Power users can add custom fields to forms without developer customization 
---------------------------------------------------------------------------

Many application customizations involve adding one or more fields to existing
tables and including them in application forms. Most of your customizations may
be comprised of adding fields.

Customizations are expensive because they require developer intervention for
development, test, and code life cycle management. Customizations also need to
be managed and migrated from one environment to another.  

We have made it easier to add custom fields to forms in Dynamics 365 for Finance
and Operations, Enterprise edition. Developer customization is no longer
needed. Instead, a power user can add a custom field to a table and
then place that field on the form using personalization. An IT administrator
can then share the personalization with others in your organization. For information about how to create and manage custom fields, see [Custom fields](user-defined-fields.md).

Service offered via a published range of network addresses
----------------------------------------------------------

Your organization may have specific security policies that prevents users from
navigating to unknown or malicious IP addresses and domains. You can now open
specific firewall rules in your on-premises network to enable your users to
access Dynamics 365 for Finance and Operations, Enterprise edition. This service
will publish the IP addresses to your service environment so that an
administrator can define a custom firewall on your on-premises network.

## Support for display and edit methods on form data sources using augmentation classes (ExtensionOf)

The following examples use Display/Edit methods on augmented classes for tables and forms.

#### Class extension for a form

```
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
  ``` 
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
The form or form extension can then consume the display and edit methods from a form control by providing the `<ClassName>.<MethodName>` in the DataMethod property.

