---
# required metadata

title: Deprecated APIs in Finance and Operations
description: This document provides the list of deprecated APIs and migration guidance for some of the deprecated APIs.
author: aneesmsft
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 26011
ms.assetid: 15d78841-7ea9-4553-905b-ff850d176d4d
ms.search.region: Global
# ms.search.industry: 
ms.author: aneesa
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Deprecated APIs in Finance and Operations

[!include[banner](../includes/banner.md)]


This document provides the list of deprecated APIs and migration guidance for some of the deprecated APIs.

Overview
--------

A number of APIs from Dynamics AX 2012 have been identified. The reason for the deprecation for each API varies. Most commonly, the reasons are one of the following:

-   Not suited/applicable to the new client.
-   Degrade performance.
-   Chatty (cause lot of traffic back and forth between server and client).
-   Redundant (framework automatically handles these now).

Throughout this table, under the **Reason for Deprecation** heading, "the client" refers to the Microsoft Dynamics 365 for Finance and Operations Web client.

## List of deprecated APIs
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Object</strong></td>
<td><strong>Type</strong></td>
<td><strong>Name</strong></td>
<td><strong>Notes</strong></td>
</tr>
<tr class="even">
<td>ActionPane</td>
<td>Method</td>
<td>tabChanged</td>
<td>Updates to ActionPanes (or controls inside of ActionPanes) should be done based on the active row, not when the tab becomes active.</td>
</tr>
<tr class="odd">
<td>ActionPaneTab</td>
<td>Method</td>
<td>selectionChanged</td>
<td>Updates to ActionPaneTabs (or controls inside of ActionPaneTabs) should be done based on the active row, not when the tab becomes active.</td>
</tr>
<tr class="even">
<td>Box</td>
<td>Method</td>
<td>yesNoTextMenuLinkText</td>
<td></td>
</tr>
<tr class="odd">
<td>ComboBox</td>
<td>Method</td>
<td>getEditText</td>
<td><h4 id="overview-1"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation"><em>Reason for deprecation</em></h4>
Redundant.
<h4 id="migration-notes"><em>Migration notes</em></h4>
Use getText instead.</td>
</tr>
<tr class="even">
<td>DataSet DataSetNode DataSetRun</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-2"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal.
<h4 id="reason-for-deprecation-1"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-1"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>DataSourceMethodInfo DataSourceMethodInfoList</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>DDEClient DDEServer DLL DLLFunction HDC HWnd Thread WinAPINative WinGDI</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-3"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-2"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-2"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="odd">
<td>DocumentManagementHelper</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>addhistory currentHistoryName currentHistoryState updateHistory</td>
<td><h4 id="overview-4"><em>Overview</em></h4>
Used in Dynamics AX 2012 with address bar.
<h4 id="reason-for-deprecation-3"><em>Reason for deprecation</em></h4>
Navigation model in the client has changed.
<h4 id="migration-notes-3"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>arrange</td>
<td></td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>controlCallingMethod</td>
<td></td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>controlMethodOverload controlMethodOverloadObject</td>
<td><h4 id="overview-5"><em>Overview</em></h4>
Used in Dynamics AX 2012 to register override methods.
<h4 id="reason-for-deprecation-4"><em>Reason for deprecation</em></h4>
This is not a clean and recommended way to register override methods.
<h4 id="migration-notes-4"><em>Migration notes</em></h4>
Use registerOverrideMethod instead.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>copy cut paste</td>
<td></td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>delAutoCompleteString getAutoCompleteString setAutoCompleteString</td>
<td><h4 id="overview-6"><em>Overview</em></h4>
Used in Dynamics AX 2012 to set, get, and delete automatic suggestions.
<h4 id="reason-for-deprecation-5"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client.
<h4 id="migration-notes-5"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>firstField</td>
<td></td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>formOnTop</td>
<td><h4 id="overview-7"><em>Overview</em></h4>
Used in Dynamics AX 2012 to manage windows and navigation.
<h4 id="reason-for-deprecation-6"><em>Reason for deprecation</em></h4>
The client has a new navigation model.
<h4 id="migration-notes-6"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>hWnd installMessageProc removeMessageProc</td>
<td><h4 id="overview-8"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-7"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-7"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>isPreloadedInstance</td>
<td><h4 id="overview-9"><em>Overview</em></h4>
Used in Dynamics AX 2012 with preloading.
<h4 id="reason-for-deprecation-8"><em>Reason for deprecation</em></h4>
Preloading is not applicable in the client.
<h4 id="migration-notes-8"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>lastField nextField nextGroup prevField prevGroup</td>
<td></td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>Lock lockWindowUpdate unLock</td>
<td><h4 id="overview-10"><em>Overview</em></h4>
These methods were used to prevent the redrawing of windows when performing a set of UI updates. Without these the window would be redrawn in response to each individual change leading to bad end-user experience and degraded performance.
<h4 id="reason-for-deprecation-9"><em>Reason for deprecation</em></h4>
These methods are specific to the Windows client and are no longer needed for the client.
<h4 id="migration-notes-9"><em>Migration notes</em></h4>
A code upgrade rule has been provided to remove occurrences of these APIs. You can safely remove any calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>print printPreview send</td>
<td><h4 id="overview-11"><em>Overview</em></h4>
Used in Dynamics AX 2012 to override the Auto Report generation for the form
<h4 id="reason-for-deprecation-10"><em>Reason for deprecation</em></h4>
Microsoft Office 365 integration offers a better user experience in the client.  The ‘Export’ function is available for the user in the Dynamics AX client forms.
<h4 id="migration-notes-10"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>redraw resetStatusBarBackgroundColor setStatusBarBackgroundColor sysColorChanged</td>
<td><h4 id="overview-12"><em>Overview</em></h4>
Used to control styles or colors.
<h4 id="reason-for-deprecation-11"><em>Reason for deprecation</em></h4>
Remove ability for developers to specify the colors via API for consistent visuals.
<h4 id="migration-notes-11"><em>Migration notes</em></h4>
A code upgrade rule has been provided to remove occurrences of the redraw API. Remove usage of these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>reload</td>
<td></td>
</tr>
<tr class="odd">
<td>Form</td>
<td>Method</td>
<td>resetSize</td>
<td><h4 id="overview-13"><em>Overview</em></h4>
This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.
<h4 id="reason-for-deprecation-12"><em>Reason for deprecation</em></h4>
These methods are specific to the Windows client and are no longer needed for the client.
<h4 id="migration-notes-12"><em>Migration notes</em></h4>
You can safely remove any calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Method</td>
<td>resize</td>
<td></td>
</tr>
<tr class="odd">
<td>FormActiveXControl FormAnimateControl FormBuildActiveXControl FormBuildAnimateControl FormBuildManagedHostControl FormBuildSegmentedEntryControl FormManagedHostControl FormSegmentedEntryControl</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-14"><em>Overview</em></h4>
These were used to host or create various custom controls for Dynamics AX 2012.
<h4 id="reason-for-deprecation-13"><em>Reason for deprecation</em></h4>
These technologies will not work with the client.
<h4 id="migration-notes-13"><em>Migration notes</em></h4>
Application developers need to build replacement controls where needed using the control extensibility features.</td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>beginDrag dragDrop dragLeave dragOver dragOverEx dragText drop dropEx dropFile endDrag</td>
<td><h4 id="overview-15"><em>Overview</em></h4>
Used to enable drag-and-drop scenarios in Dynamics AX 2012.
<h4 id="reason-for-deprecation-14"><em>Reason for deprecation</em></h4>
Drag-and-drop scenarios are not supported in the client.
<h4 id="migration-notes-14"><em>Migration notes</em></h4>
Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on drag-and-drop functionality.</td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>calcControlSize</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>command processBase processForm processLink processPicture processTitle</td>
<td><h4 id="overview-16"><em>Overview</em></h4>
Was marked for deprecation in Dynamics AX 2012.
<h4 id="reason-for-deprecation-15"><em>Reason for deprecation</em></h4>
N/A
<h4 id="migration-notes-15"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>context showContextMenu</td>
<td><h4 id="overview-17"><em>Overview</em></h4>
<span style="color: #000000">This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.</span>
<h4 id="reason-for-deprecation-16"><em>Reason for deprecation</em></h4>
These methods relied on APIs that are specific to the Windows client.
<h4 id="migration-notes-16"><em>Migration notes</em></h4>
Use getContextMenuOptions and selectedMenuOptions instead.</td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>copy cut paste</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>dateTextChange</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>editControl</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>hasControlPositionOverride</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>helpField</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>hWnd</td>
<td><h4 id="overview-18"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-17"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-17"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>inputSearch</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>itemChanging</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>keyDown</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>labelMouseDblClick mouseDblClick</td>
<td><h4 id="overview-19"><em>Overview</em></h4>
The FormControl.labelMouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is called when the label for a control is double-clicked. It provides the x, y co-ordinates of the mouse pointer, a Boolean to indicate which mouse button was clicked and Booleans to indicate whether the Ctrl and Shift key were pressed. The FormControl.mouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is similar in function to the labelMouseDblClick method. The difference is that this method is called whenever there is a double-click (not just on the labels).
<h4 id="reason-for-deprecation-18"><em>Reason for deprecation</em></h4>
The double-click action does not translate well to web-based application and touch-based scenarios. Additionally they might end up being chatty in many instances.
<h4 id="migration-notes-18"><em>Migration notes</em></h4>
The recommended replacement for these methods is to use a button and the <em>clicked</em> event.</td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>labelMousedown labelMouseup mouseDown mouseEnter mouseLeave mouseMove mouseUp</td>
<td><h4 id="overview-20"><em>Overview</em></h4>
Used to detect and respond to mouse events.
<h4 id="reason-for-deprecation-19"><em>Reason for deprecation</em></h4>
These are not touchscreen friendly and not supported in the client.
<h4 id="migration-notes-19"><em>Migration notes</em></h4>
Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on mouse events.</td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>onHScroll onVScroll</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>paint</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>prefColumnSize</td>
<td><h4 id="overview-21"><em>Overview</em></h4>
Used in Dynamics AX 2012 to control width and height
<h4 id="reason-for-deprecation-20"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-20"><em>Migration notes</em></h4>
Set the width and height explicitly instead.</td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>selectionChanging</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>setScrollInfo</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl</td>
<td>Method</td>
<td>size</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl</td>
<td>Method</td>
<td>updateWindow</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>AcquireFocus</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ActiveBackCol ActiveBackColor ActiveBackColorRGB ActiveForeColor ActiveForeColorRGB AlternateRowShading BackgroundColor BackgroundColorRGB BackStyle BackStyleRGB CharacterSet ColorScheme DrawFocusRect ForegroundColor ForegroundColorRGB GridLines GridLinesStyle PromptRect</td>
<td><h4 id="overview-22"><em>Overview</em></h4>
Used to control styles or colors.
<h4 id="reason-for-deprecation-21"><em>Reason for deprecation</em></h4>
Remove ability for developers to specify the colors via API for consistent visuals.
<h4 id="migration-notes-21"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>AlignChild AlignChildren AlignControl Border BottomMargin BottomMarginMode ColumnSpace ColumnSpaceMode ColumnSpaceValue Left LeftMargin LeftMarginMode LeftMode RightMargin RightMarginMode SizeHeight SizeWidth TabAppearance TabAutoChange TabLayout TabMode TabPlacement Top TopMargin TopMarginMode TopMode VerticalSpacing VerticalSpacingMode VerticalSpacingValue</td>
<td><h4 id="overview-23"><em>Overview</em></h4>
Used to control layout.
<h4 id="reason-for-deprecation-22"><em>Reason for deprecation</em></h4>
Remove ability for developers to control layout using this property to achieve a consistent layout.
<h4 id="migration-notes-22"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. Use styles or CSS instead.</td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>AllowDocking AlwaysOnTop ArrangeGuide ArrangeWhen ContainerScrollHorizontalOffset ContainerScrollVerticalOffset IMEMode MaximizeBox MinimizeBox Mode NeededAccessLevel ProgressType Securable SecurityKey StatusBarStyle WindowResize</td>
<td><h4 id="overview-24"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-23"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client, no longer needed.
<h4 id="migration-notes-23"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Bold</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>CanScroll</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>DisabledImage DisabledImageLocation DisabledResource</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>DisplayTarget HyperLinkDataSource HyperLinkMenuItem SaveFilter SaveSize</td>
<td><h4 id="overview-25"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-24"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-24"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Font</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>FontSize</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Frame FramePosition</td>
<td><h4 id="overview-26"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-25"><em>Reason for deprecation</em></h4>
Remove ability for developers to control frames via metadata.
<h4 id="migration-notes-25"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>HideToolbar HorizontalScrollBarVisible Scrollbars VerticalScrollBarVisible</td>
<td><h4 id="overview-27"><em>Overview</em></h4>
N/A.
<h4 id="reason-for-deprecation-26"><em>Reason for deprecation</em></h4>
Remove ability for developers to control scrollbars via metadata.
<h4 id="migration-notes-26"><em>Migration notes</em></h4>
Remove usage of these APIs from your code.</td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ImageMode</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ImageName</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ImageResource</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Italic</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelAlignment</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelBold</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelCharacterSet</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelFont</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelFontSize</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelForegroundColor LabelForegroundColorRGB</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelGuide</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelHeight LabelHeightMode LabelHeightValue</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelItalic</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelUnderline</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>LabelWidth LabelWidthMode LabelWidthValue</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Location</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>NormalResource</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ParentPage</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>SearchAfterInput SearchMode</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>SelectControl</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>SendExternalContext</td>
<td></td>
</tr>
<tr class="odd">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>ShortKey</td>
<td></td>
</tr>
<tr class="even">
<td>FormControl / FormDesign</td>
<td>Property</td>
<td>Underline</td>
<td></td>
</tr>
<tr class="odd">
<td>FormDataRow</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>FormDataSource</td>
<td>Property</td>
<td>autoNotify</td>
<td><h4 id="overview-28"><em>Overview</em></h4>
Was marked for deprecation in Dynamics AX 2012.
<h4 id="reason-for-deprecation-27"><em>Reason for deprecation</em></h4>
N/A
<h4 id="migration-notes-27"><em>Migration notes</em></h4>
Remove usage from your code.</td>
</tr>
<tr class="odd">
<td>FormDataSource</td>
<td>Method</td>
<td>cacheOnlyMode</td>
<td></td>
</tr>
<tr class="even">
<td>FormDataSource</td>
<td>Method</td>
<td>cacheRemoveRecord</td>
<td></td>
</tr>
<tr class="odd">
<td>FormDataSource</td>
<td>Method</td>
<td>defaultMark</td>
<td></td>
</tr>
<tr class="even">
<td>FormDataSource</td>
<td>Method</td>
<td>displayOption</td>
<td></td>
</tr>
<tr class="odd">
<td>FormDataSource</td>
<td>Method</td>
<td>findRecord findValue</td>
<td><h4 id="usage"><em>Usage</em></h4>
The FormDataSource.findRecord(Common record) method finds a specific record in the data source and makes it the current record. The FormDataSource.findValue(FieldId field, str value) method find a specific value in a specific field in the data source and makes the corresponding record the current record. It uses the FormDataSource.findRecord method for this.
<h4 id="reason-for-deprecation-28"><em>Reason for deprecation</em></h4>
These methods use linear searching and load a large number of records in memory and negatively impact performance.
<h4 id="migration-notes-28"><em>Migration notes</em></h4>
Replace with new APIs. Replace findRecord with positionToRecord and findValue with positionToRecordByValue. New APIs do not work in some cases, most notably with Temp tables and Views. The framework will throw an exception in those cases. If replacing with new APIs is not possible, recommended replacement is to call <em>element.args().lookupRecord(recordToFind)</em> Followed by <em>FormDataSource.research(false);</em> FormDataSource is the data source that contains the record you want to find. Passing in a “false” argument to research causes it to not retain the current position since we want to change the position to the record we found using args.lookupRecord avoids resetting sort order, ranges, etc.</td>
</tr>
<tr class="even">
<td>FormDataSource</td>
<td>Method</td>
<td>getDataRow</td>
<td></td>
</tr>
<tr class="odd">
<td>FormDataSource</td>
<td>Method</td>
<td>markAllLoadedRecords</td>
<td></td>
</tr>
<tr class="even">
<td>FormDataSource</td>
<td>Method</td>
<td>maxPagingRowCountValue pagingEnabled startRowIndex setPagingParameters totalNumberOfRows</td>
<td><h4 id="overview-29"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-29"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-29"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>FormDataSource</td>
<td>Method</td>
<td>print</td>
<td></td>
</tr>
<tr class="even">
<td>FormDesign</td>
<td>Method</td>
<td>cssClass localWebMenu showWebHelp supportReload</td>
<td><h4 id="overview-30"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-30"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-30"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>FormObjectSetNotify</td>
<td>Method</td>
<td>onPagingParametersChanged</td>
<td></td>
</tr>
<tr class="even">
<td>FormObjectSetPagingParamsChangedEvtArgs</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Global xInfo</td>
<td>Method</td>
<td>endLengthyOperation startLengthyOperation</td>
<td><h4 id="overview-31"><em>Overview</em></h4>
These methods were used to show/stop showing a progress indicator during long running operations.
<h4 id="reason-for-deprecation-31"><em>Reason for deprecation</em></h4>
In the client, the system automatically takes care of showing/hiding the progress indicator and calls to these APIs are not needed.
<h4 id="migration-notes-31"><em>Migration notes</em></h4>
You can safely remove any calls to these APIs from your code.</td>
</tr>
<tr class="even">
<td>Image</td>
<td>Method</td>
<td> captureScreen captureWindow clipboardCopy clipboardPaste crop displayImage displayOrign exportBitmap flip getImageDimensionUnits getPixel height imageInfo imageSpotlight promoteColor reduceColorOctree resize rotate saveImage saveType transparent width</td>
<td></td>
</tr>
<tr class="odd">
<td>ListPage Page</td>
<td>Method</td>
<td> activeActionPaneTabNames</td>
<td><h4 id="overview-32"><em>Overview</em></h4>
This method was used to find the active action pane tab.
<h4 id="reason-for-deprecation-32"><em>Reason for deprecation</em></h4>
In the client, Action Pane tabs are handled client-side only, the server is not aware of the state.
<h4 id="migration-notes-32"><em>Migration notes</em></h4>
Remove usage of this API from your code.</td>
</tr>
<tr class="even">
<td>MessageWin</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Object</td>
<td>Method</td>
<td>notify notifyAll wait</td>
<td><h4 id="overview-33"><em>Overview</em></h4>
Used to block and wait for an interaction/operation and notify to unblock.
<h4 id="reason-for-deprecation-33"><em>Reason for deprecation</em></h4>
These calls are deprecated for all objects except formRun and it’s derivatives.
<h4 id="migration-notes-33"><em>Migration notes</em></h4>
Calls to these APIs from formRun or it’s derivatives are allowed.  Calls to these APIs from any other object should be removed.</td>
</tr>
<tr class="even">
<td>Object</td>
<td>Method</td>
<td>objectOnServer</td>
<td><h4 id="overview-34"><em>Overview</em></h4>
Used to determine whether an object is on the server.
<h4 id="reason-for-deprecation-34"><em>Reason for deprecation</em></h4>
This is redundant and no longer required because all objects are on the server.
<h4 id="migration-notes-34"><em>Migration notes</em></h4>
You can safely remove calls to these APIs from you code. It will always evaluate to true.</td>
</tr>
<tr class="odd">
<td>Object</td>
<td>Method</td>
<td>setTimeOut</td>
<td><h4 id="overview-35"><em>Overview</em></h4>
This method existed on Object, but was non-functional. The implementation on FormRun was used as a timer to delay the execution of a piece of logic.
<h4 id="reason-for-deprecation-35"><em>Reason for deprecation</em></h4>
The browser based client no longer supported this implementation.
<h4 id="migration-notes-35"><em>Migration notes</em></h4>
Use the new setTimeOutEx method on the FormRun instead. Note that the setTimeOutEx method expects the callback to accept a parameter of type AsyncTaskResult, example: myCallBack(AsyncTaskResult result).</td>
</tr>
<tr class="even">
<td>PopupMenu</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-36"><em>Overview</em></h4>
Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.
<h4 id="reason-for-deprecation-36"><em>Reason for deprecation</em></h4>
Relied on APIs that are specific to the Dynamics AX 2012 Windows Client and cannot be used with the client.
<h4 id="migration-notes-36"><em>Migration notes</em></h4>
Use ContextMenu instead.</td>
</tr>
<tr class="odd">
<td>SysExcel</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-37"><em>Overview</em></h4>
The SysExcel classes used COM to create and edit Excel workbooks.
<h4 id="reason-for-deprecation-37"><em>Reason for deprecation</em></h4>
SysExcel relied on calls to Excel COM objects from the client. Those COM objects are not on the server and COM calls are highly discouraged going forward.
<h4 id="migration-notes-37"><em>Migration notes</em></h4>
Use the OpenXML .NET framework APIs instead. We are investigating the creation of an assembly that wraps OpenXML to make it easier to call from X++.</td>
</tr>
<tr class="even">
<td>SysINetMai SysMailer SmmOutlook</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-38"><em>Overview</em></h4>
These email related classes used predominantly client-side technologies that are no longer available and/or are highly discouraged.
<h4 id="reason-for-deprecation-38"><em>Reason for deprecation</em></h4>
The SysINetMail class is being deprecated because it used client-side MAPI. The SysMailer class is being deprecated because it used CDO (a variant of OLE messaging). The classes beginning with SmmOutlook are being deprecated since they use Outlook COM objects.
<h4 id="migration-notes-38"><em>Migration notes</em></h4>
Sending email via SMTP using the SysMailerNet class will be supported going forward. We are also actively working on client-side interactive email capabilities.</td>
</tr>
<tr class="odd">
<td>SysFormSplitter</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-39"><em>Overview</em></h4>
Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.
<h4 id="reason-for-deprecation-39"><em>Reason for deprecation</em></h4>
No longer needed in the client.
<h4 id="migration-notes-39"><em>Migration notes</em></h4>
Controls automatically provide the functionality. You can safely remove any calls to these APIs from your code. A code upgrade rule may be created in the future to automatically remove the usage.</td>
</tr>
<tr class="even">
<td>SysListPageHelper</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>SysSetupFormRun</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-40"><em>Overview</em></h4>
Used to by classes to indirectly extend FormRun.
<h4 id="reason-for-deprecation-40"><em>Reason for deprecation</em></h4>
Has been merged with FormRun class.
<h4 id="migration-notes-40"><em>Migration notes</em></h4>
Use the FormRun class instead.</td>
</tr>
<tr class="even">
<td>TextBuffer</td>
<td>Method</td>
<td>fromFile</td>
<td>Use the .NET StreamReader class instead.</td>
</tr>
<tr class="odd">
<td>TextBuffer</td>
<td>Method</td>
<td>toFile</td>
<td>Use the .NET StreamWriter class instead.</td>
</tr>
<tr class="even">
<td>Thread</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-41"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-41"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-41"><em>Migration notes</em></h4>
Consider replacing with the new runAsync method or remove usage of these APIs from your code.</td>
</tr>
<tr class="odd">
<td>WinAPI</td>
<td>Class</td>
<td></td>
<td><h4 id="overview-42"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-42"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-42"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. Replace file access APIs, such as WinAPI::getTempPath, WinAPI::fileExists, with the new file APIs.</td>
</tr>
<tr class="even">
<td>WinAPIServer</td>
<td>Method</td>
<td>cryptProtectData cryptUnprotectData</td>
<td><h4 id="overview-43"><em>Overview</em></h4>
The WinAPIServer::cryptProtectData(CryptoBlob _unEncryptedDataBlob) and WinAPIServer::cryptUnProtectData(CryptoBlob _encryptedDataBlob) methods were used to encrypt and decrypt sensitive data.
<h4 id="reason-for-deprecation-43"><em>Reason for deprecation</em></h4>
These methods are best suited to desktop usage and not recommended for web-based application usage. They also have a negative impact on performance.
<h4 id="migration-notes-43"><em>Migration notes</em></h4>
Use the .NET framework APIs and well-known hashing/security algorithms instead.</td>
</tr>
<tr class="odd">
<td>xApplication</td>
<td>Method</td>
<td>runAsync</td>
<td><h4 id="overview-44"><em>Overview</em></h4>
In Dynamics AX 2012 the xApplication::runAsync method was used to make asynchronous calls to methods.
<h4 id="reason-for-deprecation-44"><em>Reason for deprecation</em></h4>
Replaced with methods better suited to the client.
<h4 id="migration-notes-44"><em>Migration notes</em></h4>
Use runAsync methods on the Global or FormRun classes instead. These new versions of runAsync enable the caller to make an async call to a static X++ class method. They leverage the .NET System.Threading.Tasks library to execute an async method in X++.  The use of the System.Threading.Tasks.Task type allows the developer to take advantage of the rich set of features available in .NET.</td>
</tr>
<tr class="even">
<td>xGlobal</td>
<td>Method</td>
<td>clientKind</td>
<td><h4 id="overview-45"><em>Overview</em></h4>
Most commonly used to detect presence of client, such as an interactive session.
<h4 id="reason-for-deprecation-45"><em>Reason for deprecation</em></h4>
Replaced with a method better suited to the client.
<h4 id="migration-notes-45"><em>Migration notes</em></h4>
Use global::hasGUI method instead.</td>
</tr>
<tr class="odd">
<td>xGlobal</td>
<td>Method</td>
<td>computerName</td>
<td></td>
</tr>
<tr class="even">
<td>xGlobal</td>
<td>Method</td>
<td>forceFormPreload</td>
<td><h4 id="overview-46"><em>Overview</em></h4>
Used in Dynamics AX 2012 with preloading.
<h4 id="reason-for-deprecation-46"><em>Reason for deprecation</em></h4>
Preloading is not applicable in the client.
<h4 id="migration-notes-46"><em>Migration notes</em></h4>
Remove calls to these APIs from your code.</td>
</tr>
<tr class="odd">
<td>xGlobal</td>
<td>Method</td>
<td>terminalServer</td>
<td></td>
</tr>
<tr class="even">
<td>xInfo</td>
<td>Method</td>
<td>directory</td>
<td></td>
</tr>
<tr class="odd">
<td>xInfo</td>
<td>Method</td>
<td>navPane</td>
<td></td>
</tr>
<tr class="even">
<td>XmlDocument</td>
<td>Method</td>
<td>LoadSave</td>
<td></td>
</tr>
<tr class="odd">
<td>XmlWriter</td>
<td>Method</td>
<td>CreateNewFile</td>
<td></td>
</tr>
<tr class="even">
<td>XppCompiler</td>
<td>Class</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>





