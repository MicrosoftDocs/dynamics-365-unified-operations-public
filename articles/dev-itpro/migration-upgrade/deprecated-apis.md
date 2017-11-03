---
# required metadata

title: Deprecated APIs in Finance and Operations
description: This document provides the list of deprecated APIs and migration guidance for some of the deprecated APIs.
author: aneesmsft
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
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

## Overview

A number of APIs from Dynamics AX 2012 have been identified. The reason for the deprecation for each API varies. Most commonly, the reasons are one of the following:

- Not suited/applicable to the new client.
- Degrade performance.
- Chatty (cause lot of traffic back and forth between server and client).
- Redundant (framework automatically handles these now).

Throughout this table, under the **Reason for Deprecation** heading, "the client" refers to the Microsoft Dynamics 365 for Finance and Operations Web client.

## List of deprecated APIs
<table>
<tbody>
| Object | Type | Name | Notes |
|---|---|---|---
| ActionPane |Method |tabChanged | Updates to ActionPanes (or controls inside of ActionPanes) should be done based on the active row, not when the tab becomes active. |
| ActionPaneTab |Method |
selectionChanged |Updates to ActionPaneTabs (or controls inside of ActionPaneTabs) should be done based on the active row, not when the tab becomes active. |
| Box |Method |yesNoTextMenuLinkText | |
| ComboBox |Method |getEditText |<h4 id="overview-1"><em>Overview</em></h4>N/A<h4 id="reason-for-deprecation"><em>Reason for deprecation</em></h4>Redundant.<h4 id="migration-notes"><em>Migration notes</em></h4>Use getText instead. |
| DataSet DataSetNode DataSetRun |Class | |<h4 id="overview-2"><em>Overview</em></h4>Used in Dynamics AX 2012 with Enterprise Portal.<h4 id="reason-for-deprecation-1"><em>Reason for deprecation</em></h4>Not applicable in the client.<h4 id="migration-notes-1"><em>Migration notes</em></h4>Remove calls to these APIs from your code. |
| DataSourceMethodInfo DataSourceMethodInfoList |Class | | |

| 
DDEClient DDEServer DLL DLLFunction HDC HWnd Thread WinAPINative WinGDI |
Class |
 |
<h4 id="overview-3"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-2"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-2"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
DocumentManagementHelper |
Class |
 |
 |

| 
Form |
Method |
addhistory currentHistoryName currentHistoryState updateHistory |
<h4 id="overview-4"><em>Overview</em></h4>
Used in Dynamics AX 2012 with address bar.
<h4 id="reason-for-deprecation-3"><em>Reason for deprecation</em></h4>
Navigation model in the client has changed.
<h4 id="migration-notes-3"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
Form |
Method |
arrange |
 |

| 
Form |
Method |
controlCallingMethod |
 |

| 
Form |
Method |
controlMethodOverload controlMethodOverloadObject |
<h4 id="overview-5"><em>Overview</em></h4>
Used in Dynamics AX 2012 to register override methods.
<h4 id="reason-for-deprecation-4"><em>Reason for deprecation</em></h4>
This is not a clean and recommended way to register override methods.
<h4 id="migration-notes-4"><em>Migration notes</em></h4>
Use registerOverrideMethod instead. |

| 
Form |
Method |
copy cut paste |
 |

| 
Form |
Method |
delAutoCompleteString getAutoCompleteString setAutoCompleteString |
<h4 id="overview-6"><em>Overview</em></h4>
Used in Dynamics AX 2012 to set, get, and delete automatic suggestions.
<h4 id="reason-for-deprecation-5"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client.
<h4 id="migration-notes-5"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
Form |
Method |
firstField |
 |

| 
Form |
Method |
formOnTop |
<h4 id="overview-7"><em>Overview</em></h4>
Used in Dynamics AX 2012 to manage windows and navigation.
<h4 id="reason-for-deprecation-6"><em>Reason for deprecation</em></h4>
The client has a new navigation model.
<h4 id="migration-notes-6"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
Form |
Method |
hWnd installMessageProc removeMessageProc |
<h4 id="overview-8"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-7"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-7"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
Form |
Method |
isPreloadedInstance |
<h4 id="overview-9"><em>Overview</em></h4>
Used in Dynamics AX 2012 with preloading.
<h4 id="reason-for-deprecation-8"><em>Reason for deprecation</em></h4>
Preloading is not applicable in the client.
<h4 id="migration-notes-8"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
Form |
Method |
lastField nextField nextGroup prevField prevGroup |
 |

| 
Form |
Method |
Lock lockWindowUpdate unLock |
<h4 id="overview-10"><em>Overview</em></h4>
These methods were used to prevent the redrawing of windows when performing a set of UI updates. Without these the window would be redrawn in response to each individual change leading to bad end-user experience and degraded performance.
<h4 id="reason-for-deprecation-9"><em>Reason for deprecation</em></h4>
These methods are specific to the Windows client and are no longer needed for the client.
<h4 id="migration-notes-9"><em>Migration notes</em></h4>
A code upgrade rule has been provided to remove occurrences of these APIs. You can safely remove any calls to these APIs from your code. |

| 
Form |
Method |
print printPreview send |
<h4 id="overview-11"><em>Overview</em></h4>
Used in Dynamics AX 2012 to override the Auto Report generation for the form
<h4 id="reason-for-deprecation-10"><em>Reason for deprecation</em></h4>
Microsoft Office 365 integration offers a better user experience in the client.  The ‘Export’ function is available for the user in the Dynamics AX client forms.
<h4 id="migration-notes-10"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
Form |
Method |
redraw resetStatusBarBackgroundColor setStatusBarBackgroundColor sysColorChanged |
<h4 id="overview-12"><em>Overview</em></h4>
Used to control styles or colors.
<h4 id="reason-for-deprecation-11"><em>Reason for deprecation</em></h4>
Remove ability for developers to specify the colors via API for consistent visuals.
<h4 id="migration-notes-11"><em>Migration notes</em></h4>
A code upgrade rule has been provided to remove occurrences of the redraw API. Remove usage of these APIs from your code. |

| 
Form |
Method |
reload |
 |

| 
Form |
Method |
resetSize |
<h4 id="overview-13"><em>Overview</em></h4>
This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.
<h4 id="reason-for-deprecation-12"><em>Reason for deprecation</em></h4>
These methods are specific to the Windows client and are no longer needed for the client.
<h4 id="migration-notes-12"><em>Migration notes</em></h4>
You can safely remove any calls to these APIs from your code. |

| 
Form |
Method |
resize |
 |

| 
FormActiveXControl FormAnimateControl FormBuildActiveXControl FormBuildAnimateControl FormBuildManagedHostControl FormBuildSegmentedEntryControl FormManagedHostControl FormSegmentedEntryControl |
Class |
 |
<h4 id="overview-14"><em>Overview</em></h4>
These were used to host or create various custom controls for Dynamics AX 2012.
<h4 id="reason-for-deprecation-13"><em>Reason for deprecation</em></h4>
These technologies will not work with the client.
<h4 id="migration-notes-13"><em>Migration notes</em></h4>
Application developers need to build replacement controls where needed using the control extensibility features. |

| 
FormControl |
Method |
beginDrag dragDrop dragLeave dragOver dragOverEx dragText drop dropEx dropFile endDrag |
<h4 id="overview-15"><em>Overview</em></h4>
Used to enable drag-and-drop scenarios in Dynamics AX 2012.
<h4 id="reason-for-deprecation-14"><em>Reason for deprecation</em></h4>
Drag-and-drop scenarios are not supported in the client.
<h4 id="migration-notes-14"><em>Migration notes</em></h4>
Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on drag-and-drop functionality. |

| 
FormControl |
Method |
calcControlSize |
 |

| 
FormControl |
Method |
command processBase processForm processLink processPicture processTitle |
<h4 id="overview-16"><em>Overview</em></h4>
Was marked for deprecation in Dynamics AX 2012.
<h4 id="reason-for-deprecation-15"><em>Reason for deprecation</em></h4>
N/A
<h4 id="migration-notes-15"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
FormControl |
Method |
context showContextMenu |
<h4 id="overview-17"><em>Overview</em></h4>
<span style="color: #000000">This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.</span>
<h4 id="reason-for-deprecation-16"><em>Reason for deprecation</em></h4>
These methods relied on APIs that are specific to the Windows client.
<h4 id="migration-notes-16"><em>Migration notes</em></h4>
Use getContextMenuOptions and selectedMenuOptions instead. |

| 
FormControl |
Method |
copy cut paste |
 |

| 
FormControl |
Method |
dateTextChange |
 |

| 
FormControl |
Method |
editControl |
 |

| 
FormControl |
Method |
hasControlPositionOverride |
 |

| 
FormControl |
Method |
helpField |
 |

| 
FormControl |
Method |
hWnd |
<h4 id="overview-18"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-17"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-17"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
FormControl |
Method |
inputSearch |
 |

| 
FormControl |
Method |
itemChanging |
 |

| 
FormControl |
Method |
keyDown |
 |

| 
FormControl |
Method |
labelMouseDblClick mouseDblClick |
<h4 id="overview-19"><em>Overview</em></h4>
The FormControl.labelMouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is called when the label for a control is double-clicked. It provides the x, y co-ordinates of the mouse pointer, a Boolean to indicate which mouse button was clicked and Booleans to indicate whether the Ctrl and Shift key were pressed. The FormControl.mouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is similar in function to the labelMouseDblClick method. The difference is that this method is called whenever there is a double-click (not just on the labels).
<h4 id="reason-for-deprecation-18"><em>Reason for deprecation</em></h4>
The double-click action does not translate well to web-based application and touch-based scenarios. Additionally they might end up being chatty in many instances.
<h4 id="migration-notes-18"><em>Migration notes</em></h4>
The recommended replacement for these methods is to use a button and the <em>clicked</em> event. |

| 
FormControl |
Method |
labelMousedown labelMouseup mouseDown mouseEnter mouseLeave mouseMove mouseUp |
<h4 id="overview-20"><em>Overview</em></h4>
Used to detect and respond to mouse events.
<h4 id="reason-for-deprecation-19"><em>Reason for deprecation</em></h4>
These are not touchscreen friendly and not supported in the client.
<h4 id="migration-notes-19"><em>Migration notes</em></h4>
Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on mouse events. |

| 
FormControl |
Method |
onHScroll onVScroll |
 |

| 
FormControl |
Method |
paint |
 |

| 
FormControl |
Method |
prefColumnSize |
<h4 id="overview-21"><em>Overview</em></h4>
Used in Dynamics AX 2012 to control width and height
<h4 id="reason-for-deprecation-20"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-20"><em>Migration notes</em></h4>
Set the width and height explicitly instead. |

| 
FormControl |
Method |
selectionChanging |
 |

| 
FormControl |
Method |
setScrollInfo |
 |

| 
FormControl |
Method |
size |
 |

| 
FormControl |
Method |
updateWindow |
 |

| 
FormControl / FormDesign |
Property |
AcquireFocus |
 |

| 
FormControl / FormDesign |
Property |
ActiveBackCol ActiveBackColor ActiveBackColorRGB ActiveForeColor ActiveForeColorRGB AlternateRowShading BackgroundColor BackgroundColorRGB BackStyle BackStyleRGB CharacterSet ColorScheme DrawFocusRect ForegroundColor ForegroundColorRGB GridLines GridLinesStyle PromptRect |
<h4 id="overview-22"><em>Overview</em></h4>
Used to control styles or colors.
<h4 id="reason-for-deprecation-21"><em>Reason for deprecation</em></h4>
Remove ability for developers to specify the colors via API for consistent visuals.
<h4 id="migration-notes-21"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
FormControl / FormDesign |
Property |
AlignChild AlignChildren AlignControl Border BottomMargin BottomMarginMode ColumnSpace ColumnSpaceMode ColumnSpaceValue Left LeftMargin LeftMarginMode LeftMode RightMargin RightMarginMode SizeHeight SizeWidth TabAppearance TabAutoChange TabLayout TabMode TabPlacement Top TopMargin TopMarginMode TopMode VerticalSpacing VerticalSpacingMode VerticalSpacingValue |
<h4 id="overview-23"><em>Overview</em></h4>
Used to control layout.
<h4 id="reason-for-deprecation-22"><em>Reason for deprecation</em></h4>
Remove ability for developers to control layout using this property to achieve a consistent layout.
<h4 id="migration-notes-22"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. Use styles or CSS instead. |

| 
FormControl / FormDesign |
Property |
AllowDocking AlwaysOnTop ArrangeGuide ArrangeWhen ContainerScrollHorizontalOffset ContainerScrollVerticalOffset IMEMode MaximizeBox MinimizeBox Mode NeededAccessLevel ProgressType Securable SecurityKey StatusBarStyle WindowResize |
<h4 id="overview-24"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-23"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client, no longer needed.
<h4 id="migration-notes-23"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
FormControl / FormDesign |
Property |
Bold |
 |

| 
FormControl / FormDesign |
Property |
CanScroll |
 |

| 
FormControl / FormDesign |
Property |
DisabledImage DisabledImageLocation DisabledResource |
 |

| 
FormControl / FormDesign |
Property |
DisplayTarget HyperLinkDataSource HyperLinkMenuItem SaveFilter SaveSize |
<h4 id="overview-25"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-24"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-24"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
FormControl / FormDesign |
Property |
Font |
 |

| 
FormControl / FormDesign |
Property |
FontSize |
 |

| 
FormControl / FormDesign |
Property |
Frame FramePosition |
<h4 id="overview-26"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-25"><em>Reason for deprecation</em></h4>
Remove ability for developers to control frames via metadata.
<h4 id="migration-notes-25"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
FormControl / FormDesign |
Property |
HideToolbar HorizontalScrollBarVisible Scrollbars VerticalScrollBarVisible |
<h4 id="overview-27"><em>Overview</em></h4>
N/A.
<h4 id="reason-for-deprecation-26"><em>Reason for deprecation</em></h4>
Remove ability for developers to control scrollbars via metadata.
<h4 id="migration-notes-26"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. |

| 
FormControl / FormDesign |
Property |
ImageMode |
 |

| 
FormControl / FormDesign |
Property |
ImageName |
 |

| 
FormControl / FormDesign |
Property |
ImageResource |
 |

| 
FormControl / FormDesign |
Property |
Italic |
 |

| 
FormControl / FormDesign |
Property |
LabelAlignment |
 |

| 
FormControl / FormDesign |
Property |
LabelBold |
 |

| 
FormControl / FormDesign |
Property |
LabelCharacterSet |
 |

| 
FormControl / FormDesign |
Property |
LabelFont |
 |

| 
FormControl / FormDesign |
Property |
LabelFontSize |
 |

| 
FormControl / FormDesign |
Property |
LabelForegroundColor LabelForegroundColorRGB |
 |

| 
FormControl / FormDesign |
Property |
LabelGuide |
 |

| 
FormControl / FormDesign |
Property |
LabelHeight LabelHeightMode LabelHeightValue |
 |

| 
FormControl / FormDesign |
Property |
LabelItalic |
 |

| 
FormControl / FormDesign |
Property |
LabelUnderline |
 |

| 
FormControl / FormDesign |
Property |
LabelWidth LabelWidthMode LabelWidthValue |
 |

| 
FormControl / FormDesign |
Property |
Location |
 |

| 
FormControl / FormDesign |
Property |
NormalResource |
 |

| 
FormControl / FormDesign |
Property |
ParentPage |
 |

| 
FormControl / FormDesign |
Property |
SearchAfterInput SearchMode |
 |

| 
FormControl / FormDesign |
Property |
SelectControl |
 |

| 
FormControl / FormDesign |
Property |
SendExternalContext |
 |

| 
FormControl / FormDesign |
Property |
ShortKey |
 |

| 
FormControl / FormDesign |
Property |
Underline |
 |

| 
FormDataRow |
Class |
 |
 |

| 
FormDataSource |
Property |
autoNotify |
<h4 id="overview-28"><em>Overview</em></h4>
Was marked for deprecation in Dynamics AX 2012.
<h4 id="reason-for-deprecation-27"><em>Reason for deprecation</em></h4>
N/A
<h4 id="migration-notes-27"><em>Migration notes</em></h4>
Remove usage from your code. |

| 
FormDataSource |
Method |
cacheOnlyMode |
 |

| 
FormDataSource |
Method |
cacheRemoveRecord |
 |

| 
FormDataSource |
Method |
defaultMark |
 |

| 
FormDataSource |
Method |
findRecord findValue |
<h4 id="usage"><em>Usage</em></h4>
The FormDataSource.findRecord(Common record) method finds a specific record in the data source and makes it the current record. The FormDataSource.findValue(FieldId field, str value) method find a specific value in a specific field in the data source and makes the corresponding record the current record. It uses the FormDataSource.findRecord method for this.
<h4 id="reason-for-deprecation-28"><em>Reason for deprecation</em></h4>
These methods use linear searching and load a large number of records in memory and negatively impact performance.
<h4 id="migration-notes-28"><em>Migration notes</em></h4>
Replace with new APIs. Replace findRecord with positionToRecord and findValue with positionToRecordByValue. New APIs do not work in some cases, most notably with Temp tables and Views. The framework will throw an exception in those cases. If replacing with new APIs is not possible, recommended replacement is to call <em>element.args().lookupRecord(recordToFind)</em> Followed by <em>FormDataSource.research(false);</em> FormDataSource is the data source that contains the record you want to find. Passing in a “false” argument to research causes it to not retain the current position since we want to change the position to the record we found using args.lookupRecord avoids resetting sort order, ranges, etc. |

| 
FormDataSource |
Method |
getDataRow |
 |

| 
FormDataSource |
Method |
markAllLoadedRecords |
 |

| 
FormDataSource |
Method |
maxPagingRowCountValue pagingEnabled startRowIndex setPagingParameters totalNumberOfRows |
<h4 id="overview-29"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-29"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-29"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
FormDataSource |
Method |
print |
 |

| 
FormDesign |
Method |
cssClass localWebMenu showWebHelp supportReload |
<h4 id="overview-30"><em>Overview</em></h4>
Used in Dynamics AX 2012 with Enterprise Portal
<h4 id="reason-for-deprecation-30"><em>Reason for deprecation</em></h4>
Not applicable in the client.
<h4 id="migration-notes-30"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
FormObjectSetNotify |
Method |
onPagingParametersChanged |
 |

| 
FormObjectSetPagingParamsChangedEvtArgs |
Class |
 |
 |

| 
Global xInfo |
Method |
endLengthyOperation startLengthyOperation |
<h4 id="overview-31"><em>Overview</em></h4>
These methods were used to show/stop showing a progress indicator during long running operations.
<h4 id="reason-for-deprecation-31"><em>Reason for deprecation</em></h4>
In the client, the system automatically takes care of showing/hiding the progress indicator and calls to these APIs are not needed.
<h4 id="migration-notes-31"><em>Migration notes</em></h4>
You can safely remove any calls to these APIs from your code. |

| 
Image |
Method |
 captureScreen captureWindow clipboardCopy clipboardPaste crop displayImage displayOrign exportBitmap flip getImageDimensionUnits getPixel height imageInfo imageSpotlight promoteColor reduceColorOctree resize rotate saveImage saveType transparent width |
 |

| 
ListPage Page |
Method |
 activeActionPaneTabNames |
<h4 id="overview-32"><em>Overview</em></h4>
This method was used to find the active action pane tab.
<h4 id="reason-for-deprecation-32"><em>Reason for deprecation</em></h4>
In the client, Action Pane tabs are handled client-side only, the server is not aware of the state.
<h4 id="migration-notes-32"><em>Migration notes</em></h4>
Remove usage of this API from your code. |

| 
MessageWin |
Class |
 |
 |

| 
Object |
Method |
notify notifyAll wait |
<h4 id="overview-33"><em>Overview</em></h4>
Used to block and wait for an interaction/operation and notify to unblock.
<h4 id="reason-for-deprecation-33"><em>Reason for deprecation</em></h4>
These calls are deprecated for all objects except formRun and it’s derivatives.
<h4 id="migration-notes-33"><em>Migration notes</em></h4>
Calls to these APIs from formRun or it’s derivatives are allowed.  Calls to these APIs from any other object should be removed. |

| 
Object |
Method |
objectOnServer |
<h4 id="overview-34"><em>Overview</em></h4>
Used to determine whether an object is on the server.
<h4 id="reason-for-deprecation-34"><em>Reason for deprecation</em></h4>
This is redundant and no longer required because all objects are on the server.
<h4 id="migration-notes-34"><em>Migration notes</em></h4>
You can safely remove calls to these APIs from you code. It will always evaluate to true. |

| 
Object |
Method |
setTimeOut |
<h4 id="overview-35"><em>Overview</em></h4>
This method existed on Object, but was non-functional. The implementation on FormRun was used as a timer to delay the execution of a piece of logic.
<h4 id="reason-for-deprecation-35"><em>Reason for deprecation</em></h4>
The browser based client no longer supported this implementation.
<h4 id="migration-notes-35"><em>Migration notes</em></h4>
Use the new setTimeOutEx method on the FormRun instead. Note that the setTimeOutEx method expects the callback to accept a parameter of type AsyncTaskResult, example: myCallBack(AsyncTaskResult result). |

| 
PopupMenu |
Class |
 |
<h4 id="overview-36"><em>Overview</em></h4>
Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.
<h4 id="reason-for-deprecation-36"><em>Reason for deprecation</em></h4>
Relied on APIs that are specific to the Dynamics AX 2012 Windows Client and cannot be used with the client.
<h4 id="migration-notes-36"><em>Migration notes</em></h4>
Use ContextMenu instead. |

| 
SysExcel |
Class |
 |
<h4 id="overview-37"><em>Overview</em></h4>
The SysExcel classes used COM to create and edit Excel workbooks.
<h4 id="reason-for-deprecation-37"><em>Reason for deprecation</em></h4>
SysExcel relied on calls to Excel COM objects from the client. Those COM objects are not on the server and COM calls are highly discouraged going forward.
<h4 id="migration-notes-37"><em>Migration notes</em></h4>
Use the OpenXML .NET framework APIs instead. We are investigating the creation of an assembly that wraps OpenXML to make it easier to call from X++. |

| 
SysINetMai SysMailer SmmOutlook |
Class |
 |
<h4 id="overview-38"><em>Overview</em></h4>
These email related classes used predominantly client-side technologies that are no longer available and/or are highly discouraged.
<h4 id="reason-for-deprecation-38"><em>Reason for deprecation</em></h4>
The SysINetMail class is being deprecated because it used client-side MAPI. The SysMailer class is being deprecated because it used CDO (a variant of OLE messaging). The classes beginning with SmmOutlook are being deprecated since they use Outlook COM objects.
<h4 id="migration-notes-38"><em>Migration notes</em></h4>
Sending email via SMTP using the SysMailerNet class will be supported going forward. We are also actively working on client-side interactive email capabilities. |

| 
SysFormSplitter |
Class |
 |
<h4 id="overview-39"><em>Overview</em></h4>
Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.
<h4 id="reason-for-deprecation-39"><em>Reason for deprecation</em></h4>
No longer needed in the client.
<h4 id="migration-notes-39"><em>Migration notes</em></h4>
Controls automatically provide the functionality. You can safely remove any calls to these APIs from your code. A code upgrade rule may be created in the future to automatically remove the usage. |

| 
SysListPageHelper |
Class |
 |
 |

| 
SysSetupFormRun |
Class |
 |
<h4 id="overview-40"><em>Overview</em></h4>
Used to by classes to indirectly extend FormRun.
<h4 id="reason-for-deprecation-40"><em>Reason for deprecation</em></h4>
Has been merged with FormRun class.
<h4 id="migration-notes-40"><em>Migration notes</em></h4>
Use the FormRun class instead. |

| 
TextBuffer |
Method |
fromFile |
Use the .NET StreamReader class instead. |

| 
TextBuffer |
Method |
toFile |
Use the .NET StreamWriter class instead. |

| 
Thread |
Class |
 |
<h4 id="overview-41"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-41"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-41"><em>Migration notes</em></h4>
Consider replacing with the new runAsync method or remove usage of these APIs from your code. |

| 
WinAPI |
Class |
 |
<h4 id="overview-42"><em>Overview</em></h4>
N/A
<h4 id="reason-for-deprecation-42"><em>Reason for deprecation</em></h4>
Specific to Dynamics AX 2012 Windows client and not compatible with the client.
<h4 id="migration-notes-42"><em>Migration notes</em></h4>
Remove usage of these APIs from your code. Replace file access APIs, such as WinAPI::getTempPath, WinAPI::fileExists, with the new file APIs. |

| 
WinAPIServer |
Method |
cryptProtectData cryptUnprotectData |
<h4 id="overview-43"><em>Overview</em></h4>
The WinAPIServer::cryptProtectData(CryptoBlob _unEncryptedDataBlob) and WinAPIServer::cryptUnProtectData(CryptoBlob _encryptedDataBlob) methods were used to encrypt and decrypt sensitive data.
<h4 id="reason-for-deprecation-43"><em>Reason for deprecation</em></h4>
These methods are best suited to desktop usage and not recommended for web-based application usage. They also have a negative impact on performance.
<h4 id="migration-notes-43"><em>Migration notes</em></h4>
Use the .NET framework APIs and well-known hashing/security algorithms instead. |

| 
xApplication |
Method |
runAsync |
<h4 id="overview-44"><em>Overview</em></h4>
In Dynamics AX 2012 the xApplication::runAsync method was used to make asynchronous calls to methods.
<h4 id="reason-for-deprecation-44"><em>Reason for deprecation</em></h4>
Replaced with methods better suited to the client.
<h4 id="migration-notes-44"><em>Migration notes</em></h4>
Use runAsync methods on the Global or FormRun classes instead. These new versions of runAsync enable the caller to make an async call to a static X++ class method. They leverage the .NET System.Threading.Tasks library to execute an async method in X++.  The use of the System.Threading.Tasks.Task type allows the developer to take advantage of the rich set of features available in .NET. |

| 
xGlobal |
Method |
clientKind |
<h4 id="overview-45"><em>Overview</em></h4>
Most commonly used to detect presence of client, such as an interactive session.
<h4 id="reason-for-deprecation-45"><em>Reason for deprecation</em></h4>
Replaced with a method better suited to the client.
<h4 id="migration-notes-45"><em>Migration notes</em></h4>
Use global::hasGUI method instead. |

| 
xGlobal |
Method |
computerName |
 |

| 
xGlobal |
Method |
forceFormPreload |
<h4 id="overview-46"><em>Overview</em></h4>
Used in Dynamics AX 2012 with preloading.
<h4 id="reason-for-deprecation-46"><em>Reason for deprecation</em></h4>
Preloading is not applicable in the client.
<h4 id="migration-notes-46"><em>Migration notes</em></h4>
Remove calls to these APIs from your code. |

| 
xGlobal |
Method |
terminalServer |
 |

| 
xInfo |
Method |
directory |
 |

| 
xInfo |
Method |
navPane |
 |

| 
XmlDocument |
Method |
LoadSave |
 |

| 
XmlWriter |
Method |
CreateNewFile |
 |

| 
XppCompiler |
Class |
 |
 |

</tbody>
</table>





