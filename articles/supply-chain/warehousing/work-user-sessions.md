---
title: Work user sessions
description: This article describes about the Work user sessions page.
author: perlynne
ms.date: 04/24/2023
ms.topic: article
ms.search.form: WHSWorkUserSession, WHSGS1PolicyTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2023-05-01
ms.dyn365.ops.version: 10.0.35
---

# Work user sessions

[!include [banner](../includes/banner.md)]

A **Work user session** will get maintained for each of the [warehouse work users](manage-warehouse-workers.md) using the [Warehouse management mobile app](install-configure-warehouse-management-app). Here the warehouse manager role will be able to track the *Login date and time* and the *Last user action date and time* together with detailed history XML communication messages and error log history.

The XML messages can for example be used to look up [mobile device step ids](mobile-app-titles-instructions.md) when setting up a [detour](warehouse-app-detours.md) process or used to look up a **Field** name as part of the [GS1 policy](gs1-barcodes.md#set-up-custom-specific-gs1-policies) definition where he names must be having an exact match between the XML message and the the **GS1 policy**.

As an example the below XML content has been copied from a *Mixed license plate receiving* process where it can be seen that the Warehouse management mobile app is in the **Step Id="LoadId"** having the **"PrimaryInputArea"** with a control **name="LoadId"**. 

``` XML example
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

![Mixed license plate receiving - Load item](media/Mixed-LP-receiving-LoadId-step.png "Mixed license plate receiving - Load item")

> [!NOTE]
> In case you cannot find the historical data, please make sure a clean up job like the [Work user session log cleanup](../../fin-ops-core/dev-itpro/sysadmin/cleanuproutines.md#warehouse-management) has not been running.
