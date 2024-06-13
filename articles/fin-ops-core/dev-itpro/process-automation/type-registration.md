---
title: Type registration
description: Learn abouthow to register types from the process automation framework, including overviews and code examples for various classes.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/10/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Type registration

[!include [banner](../includes/banner.md)]

To implement a process by using the process automation framework, you must first understand the concept of a *type* in the framework. A type is a unique process that is integrated with the batch framework and that uses the **SysOperations** framework, specifically the **SysOperationServiceController** class. The types are stored in the **ProcessScheduleType** table.

Here are a few examples of different types that are registered with the process automation framework:

- Vendor Payment Proposal (**VendPaymProposalAutomationTypeRegistrationProvider** class)
- Vendor Invoice Posting (**VendInvoicePostProcessScheduleTypeRegistration** class)
- Subledger transfer to general ledger (**SubledgerJournalVoucherTransferServiceRegistration** class)

If an existing process uses **RunBaseBatch**, consider wrapping it with **SysOperationServiceController**. The process automation framework doesn't support **RunBaseBatch**.

To register your type with the process automation framework, you must implement the **ProcessScheduleITypeRegistration** interface. This interface has a single method that returns an instance of **ProcessScheduleTypeRegistrationItem**.

If your process uses a feature flag, you must disable and enable the type as the feature is disabled and enabled, respectively.

- If you disable the feature flag for a type, the type doesn't appear in the user interface (UI). The scheduler won't schedule any occurrences or background processes of that type to run, and the runtime side of the process automation framework won't create any batch jobs for that type.
- If you enable the feature flag for a type, any occurrences or background processes that are scheduled to run in the past will be run immediately. Usually, this behavior is what you want. However, if it isn't what you want, consider disabling any series that is related to the type before you disable the feature flag.

Feature management has events that you can subscribe to. The method that you use to enable and disable types is **ProcessScheduleTypeRegistration.enableOrDisableType**.

Every time that a database synchronization runs, types and series are updated from their definitions in code. The only background settings that aren't updated are those that can be edited by the system admin. The process automation framework does this update by hooking **SysSetup**. The system admin can manually trigger this update through the settings at **System administration \> Setup \> Initialize background**.

The following example shows a process for a scheduled type. Note the following points:

- A background process doesn't have to set the **Parameter** tab list, because background processes don't support parameters.
- The type name isn't shown in the UI. The name should be a developer-created string such as **VendorInvoiceBatchPosting**. It's used internally as a key to reference your type for various purposes. It **cannot** be a label.
- The type name is used heavily with the **SysPlugIn** pattern. Most of the interfaces that are implemented for the process automation framework follow the **SysPlugIn** pattern and require that the type name be supplied by the **ExportMetadataAttribute**. In most cases in this pattern, the framework invokes the implementation of an interface only for the type that is being operated on, not for other types. Code examples in this article and related topics follow this pattern.

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

The following example shows feature management for a process automation framework type.

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

## ProcessScheduleTypeRegistrationItem class

The **ProcessScheduleTypeRegistrationItem** class is used as a part of type registration and contains information that is specific to your type.

| Method | Description |
|---|---|
| `public ProcessScheduleTypeName parmName(ProcessScheduleTypeName _name = name)` | The type name that is passed to the **item.parmName** method isn't shown to users. This value is a developer-defined string that is used when various events are invoked. It should be assigned as a constant, not as a label. **Never use a label as a type name.** Use names such as **VendPaymentProposal**. |
| `public ProcessScheduleProcessType parmScheduleType(ProcessScheduleProcessType _scheduleType = scheduleType)` | This method determines whether the process is scheduled or polled. |
| `public ProcessScheduleTypeCompanyScope parmCompanyScope(ProcessScheduleTypeCompanyScope _companyScope = companyScope)` | This method determines whether the process is a single-company process or a global process. A single-company process sets the company context in a batch, depending on the company that the user is in when a series is created. If the scope is global, the company context is ignored, and all jobs are in **dat**. |
| `public LabelId parmLabelId(LabelId _labelId = labelId)` | The label that this method returns is shown to users and represents the display name for your type. An example is **Vendor payment proposal**. |
| `public className parmProcessAutomationTaskClassName(ClassName _processAutomationTaskClassName = processAutomationTaskClassName)` | The class name that this method returns is the class name of the class that will implement the **ProcessAutomationTask** interface. |
| `public NoYes parmIsEnabled(NoYes _isEnabled = isEnabled)` | This method determines whether the type that you're registering is enabled by default. If your type is feature-managed, a default value is taken from the state of the feature. Be sure to implement the enabled and disabled feature management events. Enable and disable your type in the process automation framework in the appropriate way, by using **ProcessScheduleTypeRegistration.enableOrDisableType** method. Example code is shown earlier in this article. |
| `public List parmParameterTabItemList(List _parameterTabList = parameterTabList)` | A process can have many parameter pages in the UI. These parameter pages contain parameters that are specific to the process. They are surfaced as form parts in the **Create series** wizard and edit occurrence dialog box. For each parameter page, an instance of the **ProcessSchedulelTypeRegistrationParameterTabItem** class must be constructed and returned in the list. If the process doesn't require parameter pages, return **null**. For more information, see [Process parameters](process-parameters.md). |
| `public static ProcessScheduleTypeRegistrationItem construct()` | This method constructs an instance of the **ProcessScheduleTypeRegistrationItem** class. |

## ProcessSchedulelTypeRegistrationParameterTabItem class

The **ProcessSchedulelTypeRegistrationParameterTabItem** class represents information that is specific to a single parameter page.

| Method | Description |
|---|---|
| `public MenuItemName parmMenuItemName(MenuItemName _menuItemName = menuItemName)` | The **Create series** wizard supports parameter pages by using embedded form parts. This value is the menu item that goes to the form part that is created by the team that owns the process. |
| `public LabelId parmCaption(LabelId _caption = caption)` | The caption on the parameter page. |
| `public LabelId parmHelpText(LabelId _helpText = helpText)` | The Help text for the parameter page. |
| `public static ProcessScheduleTypeRegistrationParameterTabItem newFromMenuItem(MenuItemName _menuItemName)` | Constructor that initializes the instance with the specified menu item name. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
