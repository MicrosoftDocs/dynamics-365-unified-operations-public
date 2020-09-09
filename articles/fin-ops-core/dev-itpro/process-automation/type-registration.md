
# Type Registration

Implementing the process automation framework starts with the concept of a type within the Process Automation Framework. The types are stored in the table ProcessScheduleType. A type is a unique process which integrates with the batch framework and makes use of SysOperations framework specifically the class SysOperationServiceController. If an existing process uses RunBaseBatch then consider wrapping it with SysOperationServiceController. The process automation framework does not support RunBaseBatch. These are a few examples of different types registered with the process automation framework:

- Vendor Payment Proposal (Class VendPaymProposalAutomationTypeRegistrationProvider)
- Vendor Invoice Posting (Class VendInvoicePostProcessScheduleTypeRegistration)
- Subledger transfer to GL (Class SubledgerJournalVoucherTransferServiceRegistration)

To register your type with the Process Automation Framework implement the ProcessScheduleITypeRegistration interface. This interface has a single method which returns an instance of ProcessScheduleTypeRegistrationItem.

If your process uses a feature flag then you must disable/enable the type as the feature is enabled/disabled. Disabling the feature flag for a type will cause the type to not display in the UI. The scheduler will not schedule any occurrences or background processes for that type for execution. The execution side of the framework will not create any batch jobs for that type. Enabling the type will cause any occurrences or background processes scheduled to run in the past to be immediately executed. Often this is desired but if not then consider disabling any series related to the type prior to disabling the feature flag.

Feature management has events that can be subscribed to. The API to use to enable/disable types is ProcessScheduleTypeRegistration.enableOrDisableType().

Every time a Database Synchronization is run types and series get refreshed from their definitions in code excluding those background settings that are editable by the system administrator. This is done by the framework hooking SysSetup. This can be triggered manually by the system administrator executing System Administration->Setup->Initialize background settings.

Here is an example of a sample process for a scheduled type:

Note: A background process would not need to set the parameter tab list as background processes do not support parameters.

Note: The type name is not shown in the UI. This should be a developer created string like “VendorInvoiceBatchPosting”. This is used internally as a key to referencing your type for various purposes. It must Not be a label.

Note: The type name is used heavily with SysPlugIn pattern. Most of the interfaces implemented for this framework follow the SysPlugIn pattern and require the type name to be supplied via the export metadata attribute. Following this pattern the framework in most case only invokes the implementation of an interface for the type being operated on and not other types. Code examples in this document show examples of this.

```xpp
using System.ComponentModel.Composition;

/// <summary>
/// The <c>VendPaymProposalAutomationTypeRegistrationProvider</c>
class handles type registration for Vendor payment proposal automations.
/// </summary>
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

Example implementation of feature management for a process automation framework type:

```xpp
using System.ComponentModel.Composition;
using Microsoft.Dynamics.ApplicationPlatform.FeatureExposure;
using Microsoft.Dynamics.ApplicationPlatform.FeatureExposure.Implementation;

/// <summary>
/// The <c>VendPaymProposalAutomationFeature</c> class defines the
Vendor Payment Proposal Automation feature.
/// </summary>
[Export(identifierStr(Microsoft.Dynamics.ApplicationPlatform.FeatureExposure.IFeatureMetadata))]
internal final class VendPaymProposalAutomationFeature implements
IFeatureMetadata, IFeatureMetadataEnablementNotifiable
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
        return "https://go.microsoft.com/fwlink/?linkid=2115447\&clcid=0x409";
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
parmName | The type name that is passed to item.parmName() is not displayed to customers. This is a developer defined string that is used when invoking various events and should be assigned as a constant and not a label. **Never use a label as atype name.** Use names like ‘VendPaymentProposal’.
parmScheduleType | This method determines if the process is a scheduled or a polled type.
parmCompanyScope |  This method determines if the process is either a single company or a global process. Single company processes will set the company context in batch depending upon what company the user is in when a series is created. If global then company context is ignored and all jobs will run in dat.
parmLabelId | The label returned by this method is displayed to users and represents the display name for your type. For example, ‘Vendor payment proposal’.
parmProcessAutomationTaskClassName | The class name returned by this method is the class name of your class that will implement the ProcessAutomationTask interface.
parmIsEnabled | Determines if the type we are registering is enabled by default. If your type is feature managed then default this value from the state of the feature. Be sure to implement the enabled/disabled feature management events and enable/disable your type within the process automation framework appropriately by using ProcessScheduleTypeRegistration.enableOrDisableType(). See code example above.
parmParameterTabItemList | A process can have many parameter pages in the UI containing parameters specific to the process. These parameter pages surface as form parts on the create series wizard and edit occurrence dialog. For each parameter page an instance of the class ProcessSchedulelTypeRegistrationParameterTabItem must be constructed and returned in the list. See Process Parameters for more details. If the process does not need parameter pages then return null.

## ProcessSchedulelTypeRegistrationParameterTabItem class

The ProcessSchedulelTypeRegistrationParameterTabItem class represents information specific to a single parameter page.

Method | Description
---|---
parmMenuItemName | The series wizard supports parameter pages using embedded form part. This is the menu item to the form part created by the team that owns the process.
parmCaption | This is the caption on this parameter page.
parmHelpText | This is the help text for this parameter page.
newFromMenuItem | Constructor initializing the instance with the given menu item name.
