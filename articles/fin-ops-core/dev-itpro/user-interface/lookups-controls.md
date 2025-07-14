---
title: Lookup controls
description: Learn about how to enable lookup behavior on controls, including overviews on multiselect lookups and unsupported lookup scenarios.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.update-cycle: 1095-days
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 1c71ebac-47c3-4c7e-bb48-a1c45619c95e
ms.custom: 
  - bap-template
  - evergreen
---

# Lookup controls

[!include [banner](../includes/banner.md)]

This article discusses how to enable lookup behavior on controls. It also discusses how to create multi-select lookups and outlines lookup scenarios that are no longer supported.

## Enabling lookup behavior in controls

### Controls bound to an Extended Data Type

Controls with their Extended Data Type property set (no FormDataSource in play) have a lookup under the following conditions:

1.  If the EDT has its Table Relations or Table References nodes populated.
2.  If the FormHelp property is set (custom lookup); doesn’t require rule \#1 to be true.
3.  If the control has lookup or lookupReference methods overridden. This rule also applies to fully unbound controls (no EDT, field, or data method). This condition includes overrides via registerOverrideMethod and others.

### Controls bound to a form data source

Controls that are bound to a data source can have a lookup under the following conditions: **Field bound**

1.  The “lookup” or “lookupReference” (Reference Controls) methods are overridden.
    1.  If the FormDataSource field has lookup or lookupReference methods overridden.
    2.  If the control has lookup or lookupReference methods overridden.
        -   This condition includes overrides via registerOverrideMethod and others.

2.  If the field has an EDT, then rule \#2 from the "Controls bound to an Extended Data Type" section applies.
3.  If the bound field maps to a relation per DBFGetRef rules.
    1.  High level rules:
        1.  If there's an EDT relation backing the field, with the Table Relations node populated and Ignore EDT Relations is false on the field, the relation is used (has a lookup).
        2.  If there's a relation mapping to the field and any fixed field link conditions are satisfied, the relation is used (has a lookup).
            1.  Validate must be “Yes”.

        3.  Note the special case of migrated EDT relations that occurs when:
            1.  Field is backed by an EDT with the Relations node populated.
            2.  Field is backed by a TABLE relation with the “EDTRelation” set to Yes.
            3.  The table relation link has the SourceEDT set to the appropriate EDT.

        4.  You can also have cases where IgnoreEDTRelation is set to true on a field, in which case a lookup occurs only if rule \#3.1.2 of this section is true.

**Data method bound**

1.  If the return type of the data method is an EDT, then rules \#1 and \#2 from the "Controls bound to an Extended Data Type" section apply.
2.  If the control has lookup or lookupReference methods overridden.
    -   This condition includes overrides by using registerOverrideMethod.

## Multiselect lookups
### Available system forms for building multi-select lookups

There are currently two system forms for creating multi-select lookups:

-   SysLookup – Multiselect based on an Enum.
-   SysLookupMultiselectGrid – Multiselect based on a collection of data.

### What happened to the SysLookupMultiselect form?

SysLookupMultiselect was marked for deprecation in Microsoft Dynamics AX 2012 and was removed. Any use of this form for multiselect lookup scenarios should be migrated to use SysLookupMultiselectGrid. For an example, see the form tutorial\_LookupMultiSelectGrid.

## Unsupported lookup scenarios
### Creating multiple lookup forms when the lookup button is used

An error may occur if you create multiple lookup forms when the lookup button is used. For example, overriding the ‘lookup’ method and creating a new lookup form, but also calling ‘super’ (which creates another lookup form).

### Using SelectedControl() to determine which control is hosting a lookup

Using SelectedControl() to determine which control is hosting a lookup is unsupported. While it may work in some cases, it fails in others. For example, in disambiguation lookups, no control is selected on the parent form since the act of leaving the control is what triggers a disambiguation lookup. As an alternative to using SelectedControl(), there are a few other ways to retrieve the control that is hosting the lookup:
-   Check the ‘selectTarget’ of the lookup form.
    ```xpp
    FormStringControl selectTarget = formRun.selectTarget();
    ```

-   Check the ‘callerFormControl’ on the lookup form args. SysTableLookup::getCallerControl(Args args) encapsulates that call.
    ```xpp
    FormStringControl argsCallerFormControl = args.callerFormControl();
    ```
    
The selectTarget and callerFormControl are set automatically if the lookup form instance is generated automatically by the kernel. If the form instance is created in app code, they can be set manually as shown in the following example.

```xpp
public void lookup()
{
    Args args = new Args(formStr(<formName>));
    args.caller(element);
    args.callerFormControl(this);
    FormRun formRun = classfactory.formRunClass(args);
    formRun.init();
    this.performFormLookup(formRun);
}
```

### Creating a slider dialog (instead of a lookup form) when the lookup button is used

Lookup controls should open lookup forms when the lookup button is used (not slider dialogs or other kinds of forms). The first reason for this functionality is product consistency. The second and more important reason is that opening a slider dialog from a lookup is incompatible with the new type-ahead feature in lookups.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
