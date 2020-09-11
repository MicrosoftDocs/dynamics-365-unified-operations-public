---
# required metadata

title: Type registration
description: This topic describes how to register types from the process automation framework.
author: RyanCCarlson2
manager: AnnBe
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Type registration

[!include [banner](../includes/banner.md)]

Implementing a process using the process automation framework starts with the concept of a type within the framework. The types are stored in the **ProcessScheduleType** table. A type is a unique process that integrates with the batch framework and makes use of **SysOperations** framework, specifically the **SysOperationServiceController** class. Here are a few examples of different types registered with the process automation framework:

- Vendor Payment Proposal (**VendPaymProposalAutomationTypeRegistrationProvider** class)
- Vendor Invoice Posting (**VendInvoicePostProcessScheduleTypeRegistration** class)
- Subledger transfer to general ledger (**SubledgerJournalVoucherTransferServiceRegistration** class)

If an existing process uses **RunBaseBatch**, then consider wrapping it with **SysOperationServiceController**. The framework does not support **RunBaseBatch**.

To register your type with the framework, you must implement the **ProcessScheduleITypeRegistration** interface. This interface has a single method which returns an instance of **ProcessScheduleTypeRegistrationItem**.

If your process uses a feature flag, then you must disable and enable the type as the feature is disabled and enabled, respectively. If you disable the feature flag for a type, then the type doesn't show up in the UI. The scheduler won't schedule any occurrences or background processes of that type for running. The runtime side of the framework won't create any batch jobs for that type. If you enable the feature flag for a type, then the type will cause any occurrences or background processes that are scheduled to run in the past to be immediately run. This behavior is usually what you want, but if not then consider disabling any series related to the type before disabling the feature flag.

Feature management has events that you can subscribe to. The method that you use to enable and disable types is **ProcessScheduleTypeRegistration.enableOrDisableType**.

Every time a database synchronization runs, types and series are refreshed from their definitions in code excluding those background settings that are editable by the system administrator. The framework does this by hooking **SysSetup**. This can be triggered manually by the system administrator through the **System Administration->Setup->Initialize background** settings.

Here is an example of a sample process for a scheduled type. Some things to note:

- A background process doesn't need to set the parameter tab list, because background processes don't support parameters.
- The type name isn't shown in the UI. The name should be a developer-created string like **VendorInvoiceBatchPosting**. This name is used internally as a key to referencing your type for various purposes. It **can't** be a label.
- The type name is used heavily with **SysPlugIn** pattern. Most of the interfaces implemented for this framework follow the **SysPlugIn** pattern and require that the type name is supplied by the export metadata attribute. Following this pattern, the framework in most cases only invokes the implementation of an interface for the type being operated on and not other types. Code examples in these docs follow this patter.

```xpp
using System.ComponentModel.Composition;

// The VendPaymProposalAutomationTypeRegistrationProvider class handles type registration for Vendor payment proposal automations.
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleITypeRegistration))]
public final class VendPaymProposalAutomationTypeRegistrationProvider
implements ProcessScheduleITypeRegistration
{
    private const LabelId Caption = literalStr('@CashManagement:VendPaymProposalAutomationTypeName');
    private const LabelId HelpText = literalStr('@CashManagement:VendPaymProposalAutomationSeriesWizardHelpText');
    private const MenuItemName SeriesFormMenuItemName = menuItemDisplayStr(VendPaymProposalAutomationCriteriaSeries);

    [Wrappable(false)]
    public ProcessScheduleTypeRegistrationItem getScheduleTypeRegistrationItem()
    {
        ProcessScheduleTypeRegistrationItem item =
        ProcessScheduleTypeRegistrationItem::construct();
        item.parmName(VendPaymProposalAutomationConstants::RegisteredTypeName);
        item.parmLabelId(Caption);
        item.parmScheduleType(ProcessScheduleProcessType::Scheduled);
        item.parmCompanyScope(ProcessScheduleTypeCompanyScope::SingleCompany);
        item.parmProcessAutomationTaskClassName(classStr(VendPaymProposalAutomationTask));
        item.parmParameterTabItemList(this.constructParameterTabItemList());
        item.parmIsEnabled(VendPaymProposalAutomationFeature::isEnabled());
        return item;
        }

    private List constructParameterTabItemList()
    {
        List criteriaTabItemList = new List(Types::Class);
        ProcessScheduleTypeRegistrationParameterTabItem criteriaTabItem =
        ProcessScheduleTypeRegistrationParameterTabItem::newFromMenuItem(SeriesFormMenuItemName);

        criteriaTabItem.parmCaption(Caption);
        criteriaTabItem.parmHelpText(HelpText);
        criteriaTabItemList.addEnd(criteriaTabItem);
        return criteriaTabItemList;
        }
}
```

This following code example shows feature management for a process automation framework type:

```xpp
using System.ComponentModel.Composition;
using Microsoft.Dynamics.ApplicationPlatform.FeatureExposure;
using Microsoft.Dynamics.ApplicationPlatform.FeatureExposure.Implementation;

// The VendPaymProposalAutomationFeature class defines the Vendor Payment Proposal Automation feature.
[Export(identifierStr(Microsoft.Dynamics.ApplicationPlatform.FeatureExposure.IFeatureMetadata))]
internal final class VendPaymProposalAutomationFeature implements IFeatureMetadata, IFeatureMetadataEnablementNotifiable
{
    private static VendPaymProposalAutomationFeature instance;
    private void new()
    {
    }

    private static void typeNew()
    {
        instance = new VendPaymProposalAutomationFeature();
    }

    [Hookable(false)]
    public static VendPaymProposalAutomationFeature instance()
    {
        return VendPaymProposalAutomationFeature::instance;
    }

    [Hookable(false)]
    public FeatureLabelId label()
    {
        return literalStr("@CashManagement:VendPaymProposalAutomationFeatureName");
    }

    [Hookable(false)]
    public int module()
    {
        return FeatureModuleV0::AccountsPayable;
    }

    [Hookable(false)]
    public FeatureLabelId summary()
    {
        return literalStr("@CashManagement:VendPaymProposalAutomationFeatureSummary");
    }

    [Hookable(false)]
    public WebSiteURL learnMoreUrl()
    {
        return "<your URL>";
    }

    [Hookable(false)]
    public boolean isEnabledByDefault()
    {
        return false;
    }

    [Hookable(false)]
    public boolean canDisable()
    {
        return true;
    }

    [Hookable(false)]
    public void onEnabled()
    {
        this.enableOrDisableRegisteredType(NoYes::Yes);
    }

    [Hookable(false)]
    public void onDisabled()
    {
        this.enableOrDisableRegisteredType(NoYes::No);
    }

    private void enableOrDisableRegisteredType(NoYes _isEnabled)
    {
        ProcessScheduleTypeRegistration::enableOrDisableType(VendPaymProposalAutomationConstants::RegisteredTypeName,
    _isEnabled);
    }

    internal static boolean isEnabled()
    {
        return Dynamics.AX.Application.FeatureStateProvider::isFeatureEnabled(VendPaymProposalAutomationFeature::instance());
    }
}
```

## ProcessScheduleITypeRegistration class

## ProcessScheduleTypeRegistrationItem class
  
The ProcessScheduleTypeRegistrationItem class is used as a part of type registration and contains information specific to your type.

Method | Description
---|---
`public ProcessScheduleTypeName parmName(ProcessScheduleTypeName _name = name)` | The type name that is passed to the **item.parmName** method isn't displayed to users. This value is a developer-defined string that is used when invoking various events and should be assigned as a constant and not a label. **Never use a label as a type name.** Use names like **VendPaymentProposal**.
`public ProcessScheduleProcessType parmScheduleType(ProcessScheduleProcessType _scheduleType = scheduleType)` | This method determines if the process is scheduled or a polled.
`public ProcessScheduleTypeCompanyScope parmCompanyScope(ProcessScheduleTypeCompanyScope _companyScope = companyScope)` |  This method determines if the process is a single company or a global process. A single company process sets the company context in batch depending upon what company the user is in when a series is created. If the scope is global, then the company context is ignored and all jobs will run in **dat**.
`public LabelId parmLabelId(LabelId _labelId = labelId)` | The label returned by this method is displayed to users and represents the display name for your type. For example, **Vendor payment proposal**.
`public className parmProcessAutomationTaskClassName(ClassName _processAutomationTaskClassName = processAutomationTaskClassName)` | The class name returned by this method is the class name of your class that will implement the **ProcessAutomationTask** interface.
`public NoYes parmIsEnabled(NoYes _isEnabled = isEnabled)` | Determines if the type you're registering is enabled by default. If your type is feature-managed, then default this value from the state of the feature. Be sure to implement the enabled and disabled feature management events. Enable and disable your type within the framework appropriately by using **ProcessScheduleTypeRegistration.enableOrDisableType** method. Example code is shown in this topic.
`public List parmParameterTabItemList(List _parameterTabList = parameterTabList)` | A process can have many parameter pages in the UI containing parameters specific to the process. These parameter pages surface as form parts on the create series wizard and edit occurrence dialog. For each parameter page, an instance of the class **ProcessSchedulelTypeRegistrationParameterTabItem** must be constructed and returned in the list. If the process doesn't need parameter pages, then return **null**. For more information, see [Process parameters](process-parameters.md).
`public static ProcessScheduleTypeRegistrationItem construct()` | Constructs an instance of the ProcessScheduleTypeRegistrationItem class.

## ProcessSchedulelTypeRegistrationParameterTabItem class

The **ProcessSchedulelTypeRegistrationParameterTabItem** class represents information specific to a single parameter page.

Method | Description
---|---
`public MenuItemName parmMenuItemName(MenuItemName _menuItemName = menuItemName)` | The series wizard supports parameter pages using embedded form part. This value is the menu item to the form part created by the team that owns the process.
`public LabelId parmCaption(LabelId _caption = caption)` | This value is the caption on this parameter page.
`public LabelId parmHelpText(LabelId _helpText = helpText)` | This value is the help text for this parameter page.
`public static ProcessScheduleTypeRegistrationParameterTabItem newFromMenuItem(MenuItemName _menuItemName)` | Constructor initializing the instance with the given menu item name.
