---
title: What's new or changed in the Warehouse Management mobile app
description: This article lists the new and changed features for each released version of the Warehouse Management app for Microsoft Dynamics 365 Supply Chain Management.
author: pefreita
ms.author: pefreita
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 08/25/2026
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# What's new or changed in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management. It lists changes for each version released since the general availability (GA) release of version 4. Notes for older versions are available in [Warehouse Management mobile app release notes archive](warehouse-app-whats-new-archive.md).

Starting with version 4.1.1.0, every V4 and later release is tagged with its publication date. Publication dates determine whether a release is within the rolling 12-month support window that applies to V4 and all later releases. Learn more in [Support policy for the Warehouse Management mobile app](warehouse-app-support-info.md#version-4-and-later-support-policy).

> [!NOTE]
> The publication date listed for each version marks the day the release becomes available in AppCenter and the day progressive rollout to the app stores (Microsoft Store, Google Play, and Apple App Store) begins. Because rollout is gradual, the update might not appear on every device on that exact date. Availability in each store can take several additional days to reach all users.

> [!TIP]
> For upcoming release dates, see [Warehouse Management mobile app release schedule](warehouse-app-control-updates.md). That article also describes optional ways to validate a release before it reaches your warehouse floor.

## Release notes for version 4.1.5.0 (August 25, 2026)

Version 4.1.5.0 is a cumulative update that includes new features, improvements, and a broad set of fixes.

### New features in version 4.1.5.0

- **Camera scanning** – The camera scanner now recognizes more barcode formats. No configuration is required because the additional formats are detected automatically. You can also set the color and thickness of the scan frame that outlines the scanning area.
- **Notification sounds** – You can now select a separate sound for success, failure, and warning notifications. A duplicate re-scan sound setting was also removed.
- **ProGlove arm scanners** – Added the first version of the bridge for ProGlove arm scanners. Scanner input, including image capture, is now connected to the form flow. Learn more in [Advanced bar code scanner configuration](warehouse-app-adv-scanner-config.md).
- **Client settings** – Added an editable **Client settings** option for connections. Use these settings in enterprise environments that have specific requirements, such as environments that require Transport Layer Security (TLS) 1.2 or that require workers to sign in every time they start the app. New connections now use user name and password authentication by default.

### Improvements in version 4.1.5.0

- **App startup** – Reduced the work that the app does while it starts, and reduced the size of the fonts and scripts that it loads. The app now starts faster.
- **Step pages** – Reduced the number of times that a step page redraws itself, so that steps respond faster when values change.
- **Sign-in performance (Android)** – Removed unnecessary authentication token renewals that added delay to routine requests.
- **Network communication** – Improved how the app communicates with the server. Network behavior can now be adjusted centrally, without a new app version.
- **Details cards** – Details cards are now scrollable by default.
- **Android 16** – The app and its native modules now target Android 16 (API level 36), which meets current Google Play requirements.
- **Authentication libraries** – Updated the Microsoft Authentication Library (MSAL) and OneAuth libraries to supported versions.
- **Security** – Applied multiple security fixes and dependency updates.
- **Performance telemetry** – Round-trip telemetry now matches the measurements that Warehouse Management mobile app version 3 reports, so that you can compare performance between the two versions. Telemetry now also measures how long warehouse tasks take, not just how long the server takes to respond.
- **Telemetry quality** – Numeric values are now recorded correctly in flow telemetry, and less irrelevant data is logged. Therefore, meaningful signals are easier to find.
- **Accessibility** – Improved screen reader support and navigation across menus, work cards, the welcome screen, combo boxes, version information, headers, and announcements of selected items.
- **VoiceOver (iOS)** – Improved VoiceOver support, especially in combo box dialog boxes.

### Bug fixes in version 4.1.5.0

#### All platforms

- **Submitted data** – Fixed an issue where values on the current page could be altered when the page was submitted to the server.
- **Duplicate work** – Fixed an issue where the app resent a submitted page after a timeout or a gateway error, without notifying the worker. This behavior could cause warehouse work to be completed twice.
- **Escaped characters** – Fixed an issue where server responses that contained escaped characters were shown incorrectly.
- **Single sign-on (SSO)** – Fixed a *broker no result* error that prevented workers from signing in.
- **App startup** – Fixed an issue where a failure in a single part of the app prevented the whole app from starting.
- **Error messages** – Fixed an issue where the app showed a generic failure message instead of the error message that the server returned.
- **Error page** – Fixed the layout, icon placement, and animation order on the error page. The page now adjusts correctly when the window is resized.
- **Calculator** – Fixed an issue where the calculator dropped digits during fast entry.
- **Spinner control** – Fixed an issue where the spinner didn't respond to tap and drag gestures on desktop devices.
- **Dialog boxes** – Fixed an issue where a dialog box closed when a worker selected the content inside it.
- **Promoted fields** – Fixed the formatting of promoted fields and corrected default values that were outside the allowed range. Both now match version 3 behavior.

#### Windows

- **Network failures** – Fixed an issue where the app couldn't reach the Supply Chain Management server or the Microsoft sign-in pages.
- **Blank page on startup** – Fixed an issue where the app showed a blank white page when it started, including when several RemoteApp sessions ran at the same time.
- **Camera scanning** – Fixed an issue where the camera scanner incorrectly decoded barcodes that contained group separators.
- **Layout and display** – Fixed the position of the app window, corrected rendering in high-contrast mode, and fixed an issue where the read-only spinner control cut off long numbers.

#### Android

- **Sign out** – Fixed an issue where signing out didn't sign the worker out completely. The app now clears both the account and the web session of the identity provider. Therefore, the next sign-in correctly prompts for credentials instead of reusing the previous identity.
- **Barcode scanning** – Fixed an issue where some barcodes couldn't be scanned, because several formats were ignored.
- **Diagnostic files** – Fixed an issue where diagnostic files were saved to a location where [mobile mass deployment (MDM) solutions](warehouse-app-intune-user-based.md) couldn't retrieve them from locked-down kiosk devices.

#### iOS

- **Barcode scanning** – Fixed an issue where some barcodes couldn't be scanned. Barcode detection now uses Apple Vision.
- **Scan frame** – Fixed an issue where the scan frame appeared in the wrong position.

## Release notes for version 4.1.4.0 (May 28, 2026)

Version 4.1.4.0 is a minor update that includes the following features and fixes:

### New features in version 4.1.4.0

- **Camera improvements** – Added support for Code 39 Mod 43 barcodes.

### Bug fixes in version 4.1.4.0

- **Right-to-left (RTL) support** – Corrected layout and formatting issues for right-to-left languages.
- **Submit spinner** – Resolved a UI hang and glitch that occurred when submitting forms.
- **Keyboard focus** – Fixed an issue where the virtual keyboard didn't automatically trigger when typing started.
- **Encoding** – Resolved character rendering and text corruption issues.
- **On-premises** – Fixed issues affecting on-premises deployments on Android and iOS.
- **AppCenter distribution** – Resolved issues experienced by users downloading the `.msixbundle` from AppCenter.

## Release notes for version 4.1.3.0 (May 18, 2026)

Version 4.1.3.0 is a minor update that includes the following fixes and improvements:

### Bug fixes in version 4.1.3.0

- **Label encoding** – Fixed an encoding issue that caused incorrect signs to display on labels.
- **Quantity selector** – Improved performance of the quantity selector and resolved a concurrency issue.
- **Calculator** – Fixed an issue where typing in the calculator reopened the calculator instead of continuing input.

### Improvements in version 4.1.3.0

- **Right-to-left (RTL) support** – Improved support for right-to-left languages.

## Release notes for version 4.1.2.0 (May 6, 2026)

Version 4.1.2.0 is a minor update that includes the following fixes and improvements:

### Bug fixes in version 4.1.2.0

- **Components fields** – Fixed an issue that caused `data=1` to appear in some edge case scenarios.

### Improvements in version 4.1.2.0

- **Diagnostics** – Added the option to clean up authentication data from the **Diagnostics** page.
- **Windows MDM** – Expanded mobile device management (MDM) configuration collection to support a broader range of MDM providers on Windows.

## Release notes for version 4.1.1.0 (April 30, 2026)

Version 4.1.1.0 focuses on performance, small-screen layouts, scanning reliability, and a broad set of platform-specific bug fixes.

> [!IMPORTANT]
> Starting on **May 1, 2027**, version 4 (V4) and every later release of the Warehouse Management mobile app follow a rolling 12-month support window. Microsoft accepts support cases only for releases that were published within the previous 12 months. This policy applies to every release from V4 onward, regardless of whether it's a major, minor, or patch version. The app continues to run on out-of-window releases, but support cases require an in-window version. This policy is critical to maintain the quality, security, and platform compatibility of the app. Learn more in [Support policy for the Warehouse Management mobile app](warehouse-app-support-info.md#version-4-and-later-support-policy).

### Improvements in version 4.1.1.0

- **Performance enhancements** – Faster response times for the calculator, quantity fields, and overall touch interactions.
- **Small-screen optimization** – Improved layout and rendering for displays around 640 px, optimized for truck-mounted devices.
- **Brokered authentication (optional)** – Fixed edge-case issues and updated the technical documentation. This feature remains optional.

### Scanning and input improvements

- **New scanning engine** – A dedicated global listener now handles hardware scans, so you get improved reliability. This change also addresses navigation issues on hardware that uses arrow keys.
- **Dialog support** – Scans work correctly while error, confirmation, or option dialogs are displayed.
- **Duplicate scan protection** – Prevents double actions on devices that send the same barcode through multiple channels.
- **GS1 barcode support** – Batch numbers that contain GS1 separators (`0x1D`) are now handled correctly, resolving previous disconnection issues.
- **Navigation fixes** – Restored arrow-key navigation for processes such as Sales picking, and fixed rescanning during quantity confirmation.

### Bug fixes in version 4.1.1.0

#### Layout and display

- **Pallet building** – The **Done** button is now visible on small or nonmaximized windows. You can access the **Correct**, **Cancel**, and **Done** actions without resizing.
- **Calculator** – Fixed layout problems when using landscape mode on small screens.

#### Windows

- **Spinner control** – Fixed a problem where the spinner could stop between values. It now snaps correctly.
- **Authentication** – Resolved a crash during sign-in caused by an unhandled exception.
- **Clipboard** – Removed the unnecessary *Allow paste* prompt when selecting input fields.
- **MDM** – Implemented mobile device management (MDM) read of configurations for Windows.

#### iOS

- **Calculator** – Fixed a problem where the calculator opened automatically without user interaction.

#### Localization

- **Spanish (ES)** – Fixed a problem where trailing or embedded zeros were removed from production and work quantities. Behavior now matches en-US formatting.

## Release notes for version 4.0.39.0

This update includes critical fixes for authentication workflows, significant battery life optimizations, and expanded hardware support across Android, iOS, and Windows.

### New features in version 4.0.39.0

- **Scrollable details card** – Added the option to turn on scrolling for details cards so workers can view more information on one screen without collapsing sections. The scrollable details card is designed for larger screens; on smaller devices, the feature might not work as expected. On smaller screens, switching to landscape mode might reduce the available space, which could affect scrolling behavior.

### Improvements in version 4.0.39.0

- **Battery consumption** – Optimized background processes and resource management, resulting in an approximate 9% reduction in battery usage during standard operation.
- **Authentication and connectivity** – Resolved a caching issue where the application incorrectly reused legacy connection data. This fix prevents missing connections and the need to restart the app manually.
- **MDM detection** – Improved mobile device management (MDM) detection resilience by extending the polling interval for policy checks.
- **Telemetry** – Corrected a reporting error in connection-performance telemetry. Connection speed and latency data are now accurately measured and logged.
- **Device compatibility** – Relaxed hardware and software requirements to enable installation on a broader range of legacy and modern devices.
- **Windows navigation** – Added support for the Esc key on Windows to facilitate quicker navigation and menu exits.
- **Legacy pages** – Implemented targeted performance enhancements for legacy UI pages to reduce load times and input lag.

### Fixes in version 4.0.39.0

- **Entra brokered authentication** – Resolved a critical issue on Android that prevented Microsoft Entra brokered authentication from completing successfully.
- **iOS scanning** – Fixed a focus-management glitch where success notifications (toast messages) prevented the scanner from immediately returning to a ready state on iOS devices.
- **iOS UI layout** – Corrected a layout issue on the **Edit connection** page where the system keyboard obscured action buttons at the bottom of the screen on iOS devices.
- **Step banner** – Fixed a bug where the step banner displayed a generic *Scan or enter here* placeholder instead of the context-specific value defined in the step.
- **Stability** – Resolved an issue within the animation library that caused intermittent application crashes, particularly on older hardware.
- **Blind cycle counting** – Fixed a logic error that caused duplicate error messages to be displayed consecutively.

## Version 4.0.38.0

Version 4.0.38.0 includes the following fixes and improvements:

- Fixed an issue that caused pages to render incorrectly when users navigated from the **Item inquiry** page to a custom page.
- Fixed an issue where the **Back** button didn't clear previously selected data when navigating between **Item inquiry** pages.
- Fixed an issue where some [mobile mass deployment (MDM) solutions](warehouse-app-intune-user-based.md) couldn't push connection settings, such as those specified in the **ConnectionsJson** field in Microsoft Intune, to the app.
- Fixed an issue where browser shortcuts appeared when users scanned a value.
- Improved the diagnostic file collection flow. Users can now share or save the diagnostic file in a local folder, which is useful when using kiosk mode.
- Fixed an issue where users couldn't scan a license plate on the **Confirm** page when running *Movement* flows. Only the last character of the barcode was shown.
- Fixed an issue in the *Movement* flow where a previous value could be shown in the step banner on the wrong step.
- Fixed a visual issue where **Work list** tile headers that contained special characters weren't displayed correctly.

## Version 4.0.37.0

Version 4.0.37.0 includes the following fix:

- Fixed an issue where users had to enter a complete email address when the domain name was present in the connection configuration.

## Version 4.0.36.0

Version 4.0.36.0 includes the following fixes and improvements:

- Fixed an issue that caused fields on the **Custom legacy** page to display incorrectly.
- Added support for on-premises environments on iOS.
- Fixed an issue where duplicate names in the XML caused connection failures.
- Fixed an issue where the Copilot summary didn't refresh.
- Fixed an issue where popup list item names were parsed incorrectly, causing an error.
- Fixed an issue where spinner values reset incorrectly after an error occurred.
- Fixed an issue where sending multiple requests caused an application error.
- Improved error messages to provide better clarity for users.
- Improved authentication for on-premises environments on Windows. If you experience problems with a previously working on-premises authentication on Windows, edit the connection and set broker No.
- Fixed an issue where the pull-to-refresh gesture on the work list page didn't refresh correctly.  

## Version 4.0.35.0

Version 4.0.35.0 includes the following fixes and improvements:

- Fixed an issue in the Sales picking flow where the corresponding quantity value was selected incorrectly.
  
## Version 4.0.34.0

Version 4.0.34.0 includes the following fixes and improvements:

- Fixed an issue that caused installation failure on Windows devices when using a mobile mass deployment (MDM) solution.

## Version 4.0.33.0

Version 4.0.33.0 includes the following fixes and improvements:

- Corrected the requirements listed on the Google Play store, which previously stated that near-field communication (NFC) and camera hardware were required. You can install and use the app on devices that don't include these features.
- Resolved a calculator issue that caused a process-guide error when users selected the submit button.

## Version 4.0.32.0

Version 4.0.32.0 includes the following fixes and improvements:

- Aligned authentication with Warehouse Management mobile app version 4.0.29.
- Fixed an issue that caused some apps to crash in the previous version.

## Version 4.0.31.0

Version 4.0.31.0 includes the following fixes and improvements:

- Fixed an issue that caused some apps to crash in the previous version.
- Added options to check Wi-Fi status, export HAR files, and view logs.
- The app now sends meaningful Wi-Fi telemetry data to Application Insights.
- Fixed several critical crash scenarios, including a gesture-related crash on older devices.
- Fixed an issue where the *Confirm location* placeholder wasn't visible when scanning with the device camera.
- Fixed a visual issue where the focus indicator on work list cards was invisible in light mode.
- Added a **Diagnostics** button to the main menu to improve accessibility.
- Fixed an issue where losing the internet connection redirected users to the sign-in page instead of the page where the connection was lost.
- Resolved an authentication issue that required users to sign in a second time.

## Version 4.0.30.0

Version 4.0.30.0 includes the following fixes and improvements:

- Fixed an authentication problem on on-premises Windows installations.
- Improved transitions when navigating between pages.
- Fixed an issue where the work list search field wasn't cleared after refreshing the page.
- Fixed an issue where step instructions didn't remember the *Don't show again* selection when two menu items had the same name.
- Improved Wi-Fi diagnostics through better request handling and clearer error reporting.
- Fixed a concurrency-related problem that could cause sign out failures.
- Fixed an issue on custom legacy pages where fields could appear in the wrong order or show incorrect values after edits.
- Added a loading spinner for long-running sign out operations.

## Version 4.0.29.0

Version 4.0.29.0 includes the following fixes and improvements:

- Fixed an authentication failure that occurred when multiple connections used the same client ID. The failure showed an incorrect redirect URL.
- Fixed an issue that affected deployment of the app to iOS devices when using a mobile mass deployment (MDM) solution.
- Improved support for [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Added support for ProGlove devices.
- Added support for [haptic feedback through external wearable devices](warehouse-app-haptic-feedback.md).

## Version 4.0.28.0

Version 4.0.28.0 includes the following fixes and improvements:

- Fixed an issue where pulling down to refresh didn't update the work list cards.
- Enabled brokered authentication for Android, iOS, and Windows, which supports features such as [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Added an option on Android to use a new redirect URI, which is required for [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Improved camera-based barcode scanning by adding camera zoom and augmented-reality assisted barcode focusing.
- Fixed problems with hardware keyboard detection.
- Added support for keycode mapping.
- Fixed an issue that prevented non-numerical placeholders from appearing in the step banner.
- Fixed an issue affecting image setup for product and master variants.
- Corrected case-sensitive redirect URI matching on Android.
- Fixed an issue where entering a large digit in the calculator caused the delete button to move offscreen.
- Improved localization across the app.

## Version 4.0.27.0

Version 4.0.27.0 includes the following fixes and improvements:

- Fixed an issue where pressing Enter on the scanner hardware keyboard didn't submit the value.
- Fixed a bug that added an extra pipe character when submitting a value.
- Fixed an issue where entering a long digit in the calculator caused the backspace to move unexpectedly.
- Implemented security enhancements.
- Fixed a problem where the device token expired one hour after signing in with device code authentication.
- Improved hardware keyboard functionality.
- Fixed an issue where resizing the screen in Windows changed the order of footer action buttons.
- Added the connection name to the worker sign-in page for better usability.
- Fixed an iOS issue where the calculator appeared unexpectedly during the sales picking flow.
- Fixed a crash that occurred when scrolling through a work list with many cards.
- Fixed an issue where signing out as a default user required reentering the device code for authentication.

## Version 4.0.26.0

Version 4.0.26.0 includes the following fixes and improvements:

- Fixed an issue where old values weren't removed after scanning items from a work list.
- Fixed a bug that caused the page to autosubmit when a worker pressed the physical scan button on a device during a summary step.
- Fixed mobile mass deployment (MDM) property retrieval to handle case differences in `connection.json` files.
- Enhanced Windows security.

## Version 4.0.25.0

Version 4.0.25.0 includes the following fixes and improvements:

- Resolved a rendering issue on the **Item Inquiry** page.
- Fixed a server request timeout that occurred after the quantity spinner component reset incorrectly when you navigate between pages.
- Stopped the quantity spinner from flickering when it landed between two values.
- Enhanced diagnostic tools for improved troubleshooting.
- Improved translation quality across the app.
- Refined device code error messages for greater clarity.
- Fixed a synchronization issue between the calculator and quantity spinner when using a comma as the decimal separator.

## Version 4.0.24.0

Version 4.0.24.0 of the Warehouse Management mobile app is the first general availability (GA) release of version 4 for all supported platforms (Microsoft Windows, Google Android, and Apple iOS) in all supported regions. Version 4 introduces many new features and improvements that enhance your warehouse management experience. Learn more at [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md).

## Older versions

Notes for versions older than Version 4 are available in the [Warehouse Management mobile app release notes archive](warehouse-app-whats-new-archive.md).
