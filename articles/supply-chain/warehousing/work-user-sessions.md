---
title: Inspect details of active Warehouse Management mobile app sessions
description: This article describes how to view a detailed history of XML messages and errors associated with all active Warehouse Management mobile app sessions.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSWorkUserSession, WHSGS1PolicyTable
ms.topic: how-to
ms.date: 05/26/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inspect details of active Warehouse Management mobile app sessions

[!include [banner](../includes/banner.md)]

The entire time that a [warehouse worker user](manage-warehouse-workers.md) is using the [Warehouse Management mobile app](install-configure-warehouse-management-app), the system maintains a *work user session* for that user. You can view details of each active work user session by going to **Warehouse management \> Periodic tasks \> Work user sessions**. For each session, this page shows the associated **User name**, **User ID**, **Login date and time**, and **Last user action date and time** together with a detailed history of XML communication messages and logged errors.

> [!NOTE]
> If you don't see any historical data on the **Work user sessions** page, then it might be because a clean-up job, such as the [Work user session log cleanup](../../fin-ops-core/dev-itpro/sysadmin/cleanuproutines.md#warehouse-management), is running.

The XML messages can be useful, for example, when you need to look up [mobile device step IDs](mobile-app-titles-instructions.md) as you're setting up a [detour](warehouse-app-detours.md) process. They're also useful for looking up field names to use in your [GS1 policy](gs1-barcodes.md#set-up-custom-specific-gs1-policies) definition, which must match exactly with the field names used in the relevant XML messages.

> [!IMPORTANT]
> To see the correct XML for finding info such as field names and step IDs, you must work using the actual Warehouse Management mobile app (not using an alternative tool like the browser-based emulator).

The following XML content shows an example that was copied from a *Mixed license plate receiving* process, where you can see that the Warehouse Management mobile app is currently processing a step where `Step Id="LoadId"`, which includes a control where `DisplayArea="PrimaryInputArea"` (which is where controls that are awaiting input or confirmation are typically found) and `name="LoadId"` (which is the field name associated with that control).

``` XML
<?xml version="1.0" encoding="utf-8"?>
<ParentNode>
  <Controls PagePattern="Default" PageTitle="Mixed LP receiving" MenuItemName="Mixed LP receiving">
    <Control controlType="label" name="MixedLPReceiving" label="Mixed LP receiving" newLine="1" data="" type="Undefined" length="-1" error="0" defaultButton="0" enabled="1" selected="" color="#000000" Status="1" NumDecimals="-1" DisplayArea="SubHeaderArea" PreferredInputMode="" PreferredInputType="" DisplayPriority="0" DisplaySubPriority="0" DataSequence="3" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="16806" />
    <Control controlType="text" name="LicensePlateId" label="License plate" newLine="1" data="LP33" type="String" length="25" error="0" defaultButton="0" enabled="0" selected="" color="#000000" Status="1" NumDecimals="-1" DisplayArea="InfoAndSecondaryInputArea" PreferredInputMode="Scanning" PreferredInputType="Alpha" DisplayPriority="50" DisplaySubPriority="22" DataSequence="4" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="2694" />
    <Control controlType="text" name="LoadId" label="Load" newLine="1" data="" type="String" length="20" error="0" defaultButton="0" enabled="1" selected="" color="#000000" Status="1" NumDecimals="-1" DisplayArea="PrimaryInputArea" PreferredInputMode="Scanning" PreferredInputType="Alpha" DisplayPriority="70" DisplaySubPriority="11" DataSequence="5" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="14265" />
    <Control controlType="button" name="OK" label="OK" newLine="1" data="" Icon="USMF|ActionIcon|OK" type="Undefined" length="-1" error="0" defaultButton="1" enabled="1" selected="" color="#000000" Status="1" NumDecimals="-1" DisplayArea="PrimaryActionArea" PreferredInputMode="" PreferredInputType="" DisplayPriority="0" DisplaySubPriority="0" DataSequence="6" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="16806" />
    <Control controlType="button" name="Cancel" label="Cancel" newLine="1" data="" Icon="USMF|ActionIcon|Cancel" type="Undefined" length="-1" error="0" defaultButton="0" enabled="1" selected="" color="#000000" Status="1" NumDecimals="-1" DisplayArea="" PreferredInputMode="" PreferredInputType="" DisplayPriority="0" DisplaySubPriority="0" DataSequence="7" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="16806" />
    <Control controlType="detourButton" name="Look up load" label="Look up load" newLine="1" data="" Icon="USMF|MenuIcon|GenericDataInquiry" type="16806" length="0" error="0" defaultButton="0" enabled="1" selected="" color="0" Status="0" NumDecimals="-1" DisplayArea="" PreferredInputMode="" PreferredInputType="" DisplayPriority="0" DisplaySubPriority="0" DataSequence="8" AttachedTo="" InstructionControl="" Footer1="" Footer2="" InputType="0" />
  </Controls>
  <Step Id="LoadId" Icon="USMF|StepIcon|LoadID" Title="Scan load" />
  <Auth userId="51" userGUID="{701F34BD-4E6B-475E-9722-95101E890046}" sessionId="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}" />
  <UserCulture>en-us</UserCulture>
  <UserDateCulture>en-us</UserDateCulture>
  <OperationalInsightsInstrumentationKey />
  <ServerAadTenantId>4dbfcf74-c5a6-4727-b638-d56e51d1f381</ServerAadTenantId>
  <ServerEnvironmentId /><ServerAzureRegion /><ServerVersion /><BatchFlightsEnabled />
  <Device DeviceId="{C1DEE34C-69FA-44DD-BE17-2655931016CC}" /><ServerActivity ServerActivityId="{B2AAD7A2-7674-0006-E259-ABB27476D901}" />
</ParentNode>
```

The following image shows how this step looks in the Warehouse Management mobile app.

:::image type="content" source="media/mixed-lp-receiving-load-id-step.png" alt-text="Mixed license plate receiving - Load item":::
