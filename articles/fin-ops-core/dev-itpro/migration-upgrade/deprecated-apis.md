---
title: Deprecated APIs
description: This document provides the list of deprecated APIs and migration guidance for some of the deprecated APIs.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 15d78841-7ea9-4553-905b-ff850d176d4d
---

# Deprecated APIs

[!include [banner](../includes/banner.md)]

This document provides the list of deprecated APIs and migration guidance for some of the deprecated APIs.

## Overview

A number of APIs from Dynamics AX 2012 have been identified. The reason for the deprecation for each API varies. Most commonly, the reasons are one of the following:

- Not suited/applicable to the new client.
- Degrade performance.
- Chatty (cause lot of traffic back and forth between server and client).
- Redundant (framework automatically handles these now).

Throughout this table, under the <br/>**Reason for Deprecation** heading, "the client" refers to the web client.

## List of deprecated APIs

| Object | Type | Name | Notes |
|---|---|---|---|
| ActionPane |Method |tabChanged | Updates to ActionPanes (or controls inside of ActionPanes) should be done based on the active row, not when the tab becomes active. |
| ActionPaneTab |Method | selectionChanged |Updates to ActionPaneTabs (or controls inside of ActionPaneTabs) should be done based on the active row, not when the tab becomes active. |
| Box |Method |yesNoTextMenu- <br>LinkText | |
| ComboBox |Method |getEditText |**Overview**<br/>N/A<br/>**Reason for deprecation**<br/>Redundant.<br/>**Migration notes**<br/>Use getText instead. |
| DataSet DataSetNode DataSetRun |Class | |**Overview**<br/>Used in Dynamics AX 2012 with Enterprise Portal.<br/>**Reason for deprecation**<br/>Not applicable in the client.<h4 ><br/><br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| DataSourceMethodInfo <br>DataSourceMethodInfoList |Class | | |
| DDEClient DDEServer DLL DLLFunction HDC HWnd Thread WinAPINative WinGDI |Class | |**Overview**<br/>N/A<br/>**Reason for deprecation**<br/>Specific to Dynamics AX 2012 Windows client and not compatible with the client.<br/>**Migration notes**<br/>Remove usage of these APIs from your code. |
| DocumentManagement- <br>Helper |Class | | |
| Form |Method | addhistory <br>currentHistoryName <br>currentHistoryState <br>updateHistory |**Overview**<br/>Used in Dynamics AX 2012 with address bar.<br/>**Reason for deprecation**<br/>Navigation model in the client has changed.<br/><br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| Form |Method |arrange | |
| Form |Method |controlCallingMethod | |
| Form |Method |controlMethod- <br>Overload controlMethod- <br>OverloadObject |**Overview**<br/>Used in Dynamics AX 2012 to register override methods.<br/>**Reason for deprecation**<br/>This is not a clean and recommended way to register override methods.<br/><br/>**Migration notes**<br/>Use registerOverrideMethod instead. |
| Form |Method |copy cut paste | |
| Form |Method |delAutoCompleteString getAutoCompleteString setAutoCompleteString |**Overview**<br/>Used in Dynamics AX 2012 to set, get, and delete automatic suggestions.<br/>**Reason for deprecation**<br/>Specific to Dynamics AX 2012 Windows client.<br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| Form |Method |firstField | |
| Form |Method |formOnTop |**Overview**<br/>Used in Dynamics AX 2012 to manage windows and navigation.<br/>**Reason for deprecation**<br/>The client has a new navigation model.<br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| Form |Method |hWnd installMessageProc removeMessageProc |**Overview**<br/>N/A<br/>**Reason for deprecation**<br/>Specific to Dynamics AX 2012 Windows client and not compatible with the client.<br/>**Migration notes**<br/>Remove usage of these APIs from your code. |
| Form |Method |isPreloadedInstance |**Overview**<br/>Used in Dynamics AX 2012 with preloading.<br/>**Reason for deprecation**<br/>Preloading is not applicable in the client.<br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| Form |Method |lastField nextField nextGroup prevField prevGroup | |
| Form |Method |Lock <br>lockWindowUpdate <br>unLock |**Overview**<br/>These methods were used to prevent the redrawing of windows when performing a set of UI updates. Without these the window would be redrawn in response to each individual change leading to bad end-user experience and degraded performance.<br/>**Reason for deprecation**<br/>These methods are specific to the Windows client and are no longer needed for the client.<br/>**Migration notes**<br/>A code upgrade rule has been provided to remove occurrences of these APIs. You can safely remove any calls to these APIs from your code. |
| Form |Method |print printPreview send |**Overview**<br/>Used in Dynamics AX 2012 to override the Auto Report generation for the form<br/>**Reason for deprecation**<br/>Microsoft 365 integration offers a better user experience in the client.  The ‘Export’ function is available for the user in the Dynamics AX client forms.<br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| Form |Method |redraw <br>resetStatusBar- <br>BackgroundColor <br>setStatusBar- <br>BackgroundColor <br>sysColorChanged |**Overview**<br/>Used to control styles or colors.<br/>**Reason for deprecation**<br/>Remove ability for developers to specify the colors via API for consistent visuals.<br/>**Migration notes**<br/>A code upgrade rule has been provided to remove occurrences of the redraw API. Remove usage of these APIs from your code. |
| Form |Method |reload | |
| Form |Method |resetSize |**Overview**<br/>This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.<br/>**Reason for deprecation**<br/>These methods are specific to the Windows client and are no longer needed for the client.<br/>**Migration notes**<br/>You can safely remove any calls to these APIs from your code. |
| Form |Method |resize | |
| FormActiveXControl <br>FormAnimateControl <br>FormBuildActiveXControl <br>FormBuildAnimateControl <br>FormBuildManaged- <br>HostControl <br>FormBuildSegmented- <br>EntryControl FormManagedHostControl <br>FormSegmented- <br>EntryControl |Class | |**Overview**<br/>These were used to host or create various custom controls for Dynamics AX 2012.<br/>**Reason for deprecation**<br/>These technologies will not work with the client.<br/>**Migration notes**<br/>Application developers need to build replacement controls where needed using the control extensibility features. |
| FormControl |Method |beginDrag <br>dragDrop <br>dragLeave <br>dragOver <br>dragOverEx <br>dragText <br>drop <br>dropEx <br>dropFile <br>endDrag |**Overview**<br/>Used to enable drag-and-drop scenarios in Dynamics AX 2012.<br/>**Reason for deprecation**<br/>Drag-and-drop scenarios are not supported in the client.<br/>**Migration notes**<br/>Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on drag-and-drop functionality. |
| FormControl |Method |calcControlSize | |
| FormControl |Method |command processBase processForm processLink processPicture processTitle |**Overview**<br/>Was marked for deprecation in Dynamics AX 2012.<br/>**Reason for deprecation**<br/>N/A<br/>**Migration notes**<br/>Remove calls to these APIs from your code. |
| FormControl |Method |context showContextMenu |**Overview**<br/>This method was used when controls were added/removed from a form causing its size to change. Without it the window might not be correctly sized to account for the added/removed controls.<br/>**Reason for deprecation**<br/>These methods relied on APIs that are specific to the Windows client.<br/>**Migration notes**<br/>Use getContextMenuOptions and selectedMenuOptions instead. |
| FormControl |Method |copy cut paste | |
| FormControl |Method |dateTextChange | |
| FormControl |Method |editControl | |
| FormControl |Method |hasControl- <br>PositionOverride | |
| FormControl |Method |helpField | |
| FormControl |Method |hWnd |**Overview**<br/>N/A<br/>**Reason for deprecation**<br/>Specific to Dynamics AX 2012 Windows client and not compatible with the client.<br/>**Migration notes**<br/>Remove usage of these APIs from your code. |
| FormControl |Method |inputSearch | |
| FormControl |Method |itemChanging | |
| FormControl |Method |keyDown | |
| FormControl |Method |labelMouseDblClick <br>mouseDblClick |**Overview**<br/>The FormControl.labelMouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is called when the label for a control is double-clicked. It provides the x, y co-ordinates of the mouse pointer, a Boolean to indicate which mouse button was clicked and Booleans to indicate whether the Ctrl and Shift key were pressed. The FormControl.mouseDblClick (int x, int y, int button, Boolean Ctrl, Boolean Shift) method is similar in function to the labelMouseDblClick method. The difference is that this method is called whenever there is a double-click (not just on the labels).<br/>**Reason for deprecation**<br/>The double-click action does not translate well to web-based application and touch-based scenarios. Additionally they might end up being chatty in many instances.<br/>**Migration notes**<br/>The recommended replacement for these methods is to use a button and the **clicked** event. |
| FormControl |Method |labelMousedown labelMouseup mouseDown mouseEnter mouseLeave mouseMove mouseUp |**Overview**<br/>Used to detect and respond to mouse events.<br/>**Reason for deprecation**<br/>These are not touchscreen friendly and not supported in the client.<br/>**Migration notes**<br/>Remove usage of these APIs from your code and refactor to enable the scenarios without dependency on mouse events. |
| FormControl | Method | onHScroll onVScroll |  |
| FormControl | Method | paint |  |
| FormControl | Method | prefColumnSize | **Overview** <br/>Used in Dynamics AX 2012 to control width and height<br/>**Reason for deprecation** <br/>Not applicable in the client.<br/>**Migration notes** <br/>Set the width and height explicitly instead. |
| FormControl | Method | selectionChanging |  |
| FormControl | Method | setScrollInfo |  |
|FormControl | Method | size |  |
| FormControl | Method | updateWindow |  |
| FormControl / FormDesign | Property | AcquireFocus |  |
| FormControl / FormDesign | Property | ActiveBackCol ActiveBackColor ActiveBackColorRGB ActiveForeColor ActiveForeColorRGB AlternateRowShading BackgroundColor BackgroundColorRGB BackStyle BackStyleRGB CharacterSet ColorScheme DrawFocusRect ForegroundColor ForegroundColorRGB GridLines GridLinesStyle PromptRect | **Overview** <br/>Used to control styles or colors.<br/>**Reason for deprecation** <br/>Remove ability for developers to specify the colors via API for consistent visuals.<br/>**Migration notes** <br/>Remove usage of these APIs from your code. |
| FormControl / FormDesign | Property | AlignChild AlignChildren AlignControl Border BottomMargin BottomMarginMode ColumnSpace ColumnSpaceMode ColumnSpaceValue Left LeftMargin LeftMarginMode LeftMode RightMargin RightMarginMode SizeHeight SizeWidth TabAppearance TabAutoChange TabLayout TabMode TabPlacement Top TopMargin TopMarginMode TopMode VerticalSpacing VerticalSpacingMode VerticalSpacingValue | **Overview** <br/>Used to control layout.<br/>**Reason for deprecation** <br/>Remove ability for developers to control layout using this property to achieve a consistent layout.<h4 ><br/>**Migration notes** <br/>Remove usage of these APIs from your code. Use styles or CSS instead. |
| FormControl / FormDesign | Property | AllowDocking AlwaysOnTop ArrangeGuide ArrangeWhen ContainerScroll- <br>HorizontalOffset ContainerScroll- <br>VerticalOffset IMEMode MaximizeBox MinimizeBox Mode NeededAccessLevel ProgressType Securable SecurityKey StatusBarStyle WindowResize |**Overview** <br/>N/A<br/>**Reason for deprecation** <br/>Specific to Dynamics AX 2012 Windows client, no longer needed.<br/>**Migration notes** <br/>Remove usage of these APIs from your code. |
| FormControl / FormDesign | Property | Bold |  |
| FormControl / FormDesign | Property | CanScroll |  |
| FormControl / FormDesign | Property | DisabledImage DisabledImageLocation DisabledResource |  |
| FormControl / FormDesign | Property | DisplayTarget HyperLinkDataSource HyperLinkMenuItem SaveFilter SaveSize | **Overview** <br/>Used in Dynamics AX 2012 with Enterprise Portal<br/>**Reason for deprecation** <br/>Not applicable in the client.<br/>**Migration notes** <br/>Remove calls to these APIs from your code. |
| FormControl / FormDesign | Property | Font |  |
| FormControl / FormDesign | Property | FontSize |  |
| FormControl / FormDesign | Property | Frame FramePosition | **Overview** <br/>N/A<br/>**Reason for deprecation** <br/>Remove ability for developers to control frames via metadata.<br/>**Migration notes** <br/>Remove usage of these APIs from your code. |
| FormControl / FormDesign | Property | HideToolbar HorizontalScrollBarVisible Scrollbars VerticalScrollBarVisible |**Overview** <br/>N/A.<br/>**Reason for deprecation** <br/>Remove ability for developers to control scrollbars via metadata.<br/>**Migration notes** <br/>Remove usage of these APIs from your code. |
| FormControl / FormDesign | Property | ImageMode |  |
| FormControl / FormDesign | Property | ImageName |  |
| FormControl / FormDesign | Property | ImageResource |  |
| FormControl / FormDesign | Property | Italic |  |
| FormControl / FormDesign | Property | LabelAlignment |  |
| FormControl / FormDesign | Property | LabelBold |  |
| FormControl / FormDesign | Property | LabelCharacterSet |  |
| FormControl / FormDesign | Property | LabelFont |  |
| FormControl / FormDesign | Property | LabelFontSize |  |
| FormControl / FormDesign | Property | LabelForegroundColor LabelForegroundColorRGB |  |
| FormControl / FormDesign | Property | LabelGuide |  |
| FormControl / FormDesign | Property | LabelHeight LabelHeightMode LabelHeightValue |  |
| FormControl / FormDesign | Property | LabelItalic |  |
| FormControl / FormDesign | Property | LabelUnderline |  |
| FormControl / FormDesign | Property | LabelWidth LabelWidthMode LabelWidthValue |  |
| FormControl / FormDesign | Property | Location |  |
| FormControl / FormDesign | Property | NormalResource |  |
| FormControl / FormDesign | Property | ParentPage |  |
| FormControl / FormDesign | Property | SearchAfterInput SearchMode |  |
| FormControl / FormDesign | Property | SelectControl |  |
| FormControl / FormDesign | Property | SendExternalContext |  |
| FormControl / FormDesign | Property | ShortKey |  |
| FormControl / FormDesign | Property | Underline |  |
| FormDataRow | Class |  |  |
| FormDataSource | Property | autoNotify | **Overview** <br/>Was marked for deprecation in Dynamics AX 2012.<br/>**Reason for deprecation** <br/>N/A<br/>**Migration notes** <br/>Remove usage from your code. |
| FormDataSource | Method | cacheOnlyMode |  |
| FormDataSource | Method | cacheRemoveRecord |  |
| FormDataSource | Method | defaultMark |  |
| FormDataSource |Method |findRecord findValue |**Usage** <br/>The FormDataSource.findRecord( Common record) method finds a specific record in the data source and makes it the current record. The FormDataSource.findValue(FieldId field, str value) method find a specific value in a specific field in the data source and makes the corresponding record the current record. It uses the FormDataSource.findRecord method for this.<br/>**Reason for deprecation** <br/>These methods use linear searching and load a large number of records in memory and negatively impact performance.<br/>**Migration notes** <br/>Replace with new APIs. Replace findRecord with positionToRecord and findValue with positionToRecordByValue. New APIs do not work in some cases, most notably with Temp tables and Views. The framework will throw an exception in those cases. If replacing with new APIs is not possible, recommended replacement is to call **element.args(). lookupRecord(recordToFind)** Followed by **FormDataSource.research(false);** FormDataSource is the data source that contains the record you want to find. Passing in a “false” argument to research causes it to not retain the current position since we want to change the position to the record we found using args.lookupRecord avoids resetting sort order, ranges, etc. |
| FormDataSource | Method | getDataRow |  |
| FormDataSource | Method | markAllLoadedRecords |  |
| FormDataSource | Method | maxPagingRowCountValue pagingEnabled startRowIndex setPagingParameters totalNumberOfRows |**Overview** <br/>Used in Dynamics AX 2012 with Enterprise Portal<br/>**Reason for deprecation** <br/>Not applicable in the client.<br/>**Migration notes** <br/>Remove calls to these APIs from your code. |
| FormDataSource | Method | print |  |
| FormDesign | Method | cssClass localWebMenu showWebHelp supportReload |**Overview** <br/>Used in Dynamics AX 2012 with Enterprise Portal<br/>**Reason for deprecation** <br/>Not applicable in the client.<br/>**Migration notes** <br/>Remove calls to these APIs from your code. |
| FormObjectSetNotify | Method | onPaging- <br>ParametersChanged |  |
| FormObjectSetPaging- <br>ParamsChangedEvtArgs | Class |  |  |
| Global xInfo |Method |endLengthyOperation startLengthyOperation |**Overview** <br/>These methods were used to show/stop showing a progress indicator during long running operations.<br/>**Reason for deprecation** <br/>In the client, the system automatically takes care of showing/hiding the progress indicator and calls to these APIs are not needed.<br/>**Migration notes** <br/>You can safely remove any calls to these APIs from your code. |
| Image | Method |captureScreen captureWindow clipboardCopy clipboardPaste crop displayImage displayOrign exportBitmap flip getImageDimensionUnits getPixel height imageInfo imageSpotlight promoteColor reduceColorOctree resize rotate saveImage saveType transparent width |  |
| ListPage Page | Method |  activeActionPane- <br>TabNames | **Overview** <br/>This method was used to find the active action pane tab.<br/>**Reason for deprecation** <br/>In the client, Action Pane tabs are handled client-side only, the server is not aware of the state.<h4 ><br/>**Migration notes** <br/>Remove usage of this API from your code. |
| MessageWin | Class |  |  |
| Object | Method | notify notifyAll wait | **Overview** <br/>Used to block and wait for an interaction/operation and notify to unblock.<br/>**Reason for deprecation** <br/>These calls are deprecated for all objects except formRun and it’s derivatives.<br/>**Migration notes** <br/>Calls to these APIs from formRun or it’s derivatives are allowed.  Calls to these APIs from any other object should be removed. |
| Object | Method | objectOnServer | **Overview** <br/>Used to determine whether an object is on the server.<br/>**Reason for deprecation** <br/>This is redundant and no longer required because all objects are on the server.<br/>**Migration notes** <br/>You can safely remove calls to these APIs from you code. It will always evaluate to true. |
| Object | Method | setTimeOut | **Overview** <br/>This method existed on Object, but was non-functional. The implementation on FormRun was used as a timer to delay the execution of a piece of logic.<br/>**Reason for deprecation** <br/>The browser based client no longer supported this implementation.<br/>**Migration notes** <br/>Use the new setTimeOutEx method on the FormRun instead. Note that the setTimeOutEx method expects the callback to accept a parameter of type AsyncTaskResult, example: myCallBack(AsyncTaskResult result). |
| PopupMenu | Class |  | **Overview** <br/>Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.<br/>**Reason for deprecation** <br/>Relied on APIs that are specific to the Dynamics AX 2012 Windows Client and cannot be used with the client.<br/>**Migration notes** <br/>Use ContextMenu instead. |
| SysExcel | Class |  | **Overview** <br/>The SysExcel classes used COM to create and edit Excel workbooks.<br/>**Reason for deprecation** <br/>SysExcel relied on calls to Excel COM objects from the client. Those COM objects are not on the server and COM calls are highly discouraged going forward.<br/>**Migration notes** <br/>Use the OpenXML .NET framework APIs instead. We are investigating the creation of an assembly that wraps OpenXML to make it easier to call from X++. |
| SysINetMai SysMailer SmmOutlook | Class |  | **Overview** <br/>These email related classes used predominantly client-side technologies that are no longer available and/or are highly discouraged.<br/>**Reason for deprecation** <br/>The SysINetMail class is being deprecated because it used client-side MAPI. The SysMailer class is being deprecated because it used CDO (a variant of OLE messaging). The classes beginning with SmmOutlook are being deprecated since they use Outlook COM objects.<br/>**Migration notes** <br/>Sending email via SMTP using the SysMailerNet class will be supported going forward. We are also actively working on client-side interactive email capabilities. |
| SysFormSplitter | Class |  | **Overview** <br/>Used in Dynamics AX 2012 to get splitters that let users change the size of the two parts that are split.<br/>**Reason for deprecation** <br/>No longer needed in the client.<br/>**Migration notes** <br/>Controls automatically provide the functionality. You can safely remove any calls to these APIs from your code. A code upgrade rule may be created in the future to automatically remove the usage. |
| SysListPageHelper | Class |  |  |
| SysSetupFormRun | Class |  | **Overview** <br/>Used to by classes to indirectly extend FormRun.<br/>**Reason for deprecation** <br/>Has been merged with FormRun class.<br/>**Migration notes** <br/>Use the FormRun class instead. |
| TextBuffer | Method | fromFile | Use the .NET StreamReader class instead. |
| TextBuffer | Method | toFile | Use the .NET StreamWriter class instead. |
| Thread | Class |  | **Overview** <br/>N/A<br/>**Reason for deprecation** <br/>Specific to Dynamics AX 2012 Windows client and not compatible with the client.<br/>**Migration notes** <br/>Consider replacing with the new runAsync method or remove usage of these APIs from your code. |
| WinAPI | Class |  | **Overview** <br/>N/A<br/>**Reason for deprecation** <br/>Specific to Dynamics AX 2012 Windows client and not compatible with the client.<br/>**Migration notes** <br/>Remove usage of these APIs from your code. Replace file access APIs, such as WinAPI::getTempPath, WinAPI::fileExists, with the new file APIs. |
| WinAPIServer | Method | cryptProtectData cryptUnprotectData | **Overview** <br/>The WinAPIServer::cryptProtectData( CryptoBlob \_unEncryptedDataBlob) and WinAPIServer::cryptUnProtectData( CryptoBlob \_encryptedDataBlob) methods were used to encrypt and decrypt sensitive data.<br/>**Reason for deprecation** <br/>These methods are best suited to desktop usage and not recommended for web-based application usage. They also have a negative impact on performance.<br/>**Migration notes** <br/>Use the .NET framework APIs and well-known hashing/security algorithms instead. |
| xApplication | Method | runAsync | **Overview** <br/>In Dynamics AX 2012 the xApplication::runAsync method was used to make asynchronous calls to methods.<br/>**Reason for deprecation** <br/>Replaced with methods better suited to the client.<br/>**Migration notes** <br/>Use runAsync methods on the Global or FormRun classes instead. These new versions of runAsync enable the caller to make an async call to a static X++ class method. They leverage the .NET System.Threading.Tasks library to execute an async method in X++.  The use of the System.Threading.Tasks.Task type allows the developer to take advantage of the rich set of features available in .NET. |
| xGlobal | Method | clientKind | **Overview** <br/>Most commonly used to detect presence of client, such as an interactive session.<br/>**Reason for deprecation** <br/>Replaced with a method better suited to the client.<br/>**Migration notes** <br/>Use global::hasGUI method instead. |
| xGlobal | Method | computerName |  |
| xGlobal | Method | forceFormPreload | **Overview** <br/>Used in Dynamics AX 2012 with preloading.<br/>**Reason for deprecation** <br/>Preloading is not applicable in the client.<br/>**Migration notes** <br/>Remove calls to these APIs from your code. |
| xGlobal | Method | terminalServer |  |
| xInfo | Method | directory |  |
| xInfo | Method | navPane |  |
| XmlDocument | Method | LoadSave |  |
| XmlWriter | Method | CreateNewFile |  |
| XppCompiler | Class |  |  |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
