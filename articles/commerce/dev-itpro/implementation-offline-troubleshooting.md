---
# required metadata

title: Commerce offline implementation troubleshooting
description: This article provides an overview of troubleshooting for offline implementations of Microsoft Dynamics 365 Commerce.
author: jashanno
ms.date: 03/03/2023
ms.topic: article
audience: IT Pro
ms.reviewer: josaw
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2022-12-29

---

# Commerce offline implementation troubleshooting

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This article provides an overview of troubleshooting for offline implementations of Microsoft Dynamics 365 Commerce. It focuses on troubleshooting details that are related to the use of offline functionality. The article is intended for customers who implement offline functionality that's related to the Dynamics 365 Commerce Modern POS or Store Commerce application.

Correct configuration and synchronization of data are crucial to a correct offline implementation of Dynamics 365 Commerce. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synced, the whole environment is effectively useless. Therefore, a top priority is to understand what's required to configure, generate, sync, and verify data across the full implementation. This implementation covers Commerce headquarters through the Commerce Scale Unit (CSU) to the brick-and-mortar stores that use Modern POS (with or without an offline database) and other in-store components.

Commerce Data Exchange (CDX) is the Commerce functionality that replicates and syncs data across databases. However, CDX differs from typical data replication functionality in that it also allows for filtering. CDX helps minimize data sets by generating only data that's specific to the channels that were specified for selection, filtering specific tables from offline databases, and filtering expired records for data that's no longer used (such as expired discounts).

For more information about Commerce offline functionality, see [Additional resources](#additional-resources).

## Troubleshooting

If the following table doesn't list an error that you're receiving, create a support request so that Microsoft Support can help you fix the issue. This section will be updated with additional errors over time. Therefore, you should review this article before you implement or update Store Commerce app registers that use offline databases.

Note that all troubleshooting errors begin with **Microsoft\_Dynamics\_**. However, in the following table, this prepended string is omitted from the error codes to shorten them.

| Error | Description |
|-------|-------------|
| Commerce\_Runtime_AuthenticationFailed<br>Commerce_Runtime_AuthorizationFailed | A sign-in-related issue has occurred. This issue might occur because data isn't found or correctly configured in the offline database. |
| Commerce\_Runtime\_AuthenticationMethodDisabled<br>Commerce\_Runtime\_ChannelConfigurationNotFound<br>Commerce\_Runtime\_ChannelNotPublished<br>Commerce\_Runtime\_ChannelRecordNotFound<br>Commerce\_Runtime\_EmployeePermissionContextNotFound<br>Commerce\_Runtime\_InvalidChannel<br>Commerce\_Runtime\_InvalidChannelConfiguration<br>Commerce\_Runtime\_StaffIdContextMissing<br>Commerce\_Runtime\_LocalDeviceAuthenticationFailed | Unable to switch to offline mode. The channel information is either unavailable or incorrectly configured. To fix this issue, run the **Channel configuration scheduler** job (by default, the **1070** scheduler job). Also, contact your system administrator. |
| Commerce\_Runtime\_CredentialsNotConfigured<br>Commerce\_Runtime\_CredentialsNotFound<br>Commerce\_Runtime\_InvalidAuthenticationCredentials<br>Commerce\_Runtime\_LocalLogonFailed<br>Commerce\_Runtime\_UserBlockedDueToTooManyFailedLogonAttempts | Unable to switch to offline mode. The user information is either unavailable or incorrectly configured. To fix this issue, run the **Staff scheduler** job (by default, the **1060** scheduler job). Also, contact your system administrator. |
| Commerce\_Runtime\_CriticalStorageError | To check the status of offline database permissions, size, and disk space, you can use the offline dashboard. |
| Commerce\_Runtime\_ElevatedUserSameAsLoggedOnUser | This error occurs when the same user tries to perform a manager override. A different user must be used. |
| Commerce\_Runtime\_RealtimeServiceNotSupported<br>Commerce\_Runtime\_TransientStorageError | Unable to switch to offline mode. The offline database is either incorrectly installed or incorrectly configured. Verify that everything has been set up successfully. Also, contact your system administrator. |
| Commerce\_Runtime\_TerminalNotFound<br>Commerce\_Runtime\_DeviceConfigurationNotFound | To fix this issue, run the **Channel configuration scheduler** job (by default, the **1070** scheduler job). Also, contact your system administrator. |
| Internal\_Server\_Error<br>Request\_Timeout\_Error<br>Commerce\_Runtime\_InvalidFormat | These errors cover a variety of possible scenarios. Therefore, Microsoft recommends that you contact Support to get direct assistance (where applicable). |

## Additional resources

[Commerce offline implementation considerations](implementation-considerations-offline.md)

[Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)

[Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)

[Commerce Data Exchange best practices](CDX-Best-Practices.md)

[Online and offline point of sale (POS) operations](../pos-operations.md)

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Select an in-store topology](retail-in-store-topology.md)

[Device management implementation guidance](../implementation-considerations-devices.md)

[Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

<!--[Configure, install, and activate the Store Commerce app](../retail-modern-pos-device-activation.md)-->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
