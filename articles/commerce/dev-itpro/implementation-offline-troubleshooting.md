---
# required metadata

title: Commerce offline implementation troubleshooting
description: This article provides an overview of Microsoft Dynamics 365 Commerce offline implementation troubleshooting.
author: jashanno
ms.date: 12/29/2022
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

This article is intended for people who implement offline functionality related to the Microsoft Dynamics 365 Commerce Modern POS or Store Commerce applications. This article describes troubleshooting details related to the usage of offline functionality.

## Overview

Proper configuration and synchronization of data is crucial to a correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation. This goes from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS (with or without an offline database) and other in-store components. Commerce Data Exchange (CDX) is the Commerce functionality that replicates and synchronizes data across databases. However, CDX differs from typical data replication functionality because it also allows for filtering. CDX helps minimize data sets by generating only data that is specific to the channels that were specified for selection, filtering specific tables from offline databases, and filtering expired records for data that is no longer used, such as expired discounts. For additional information regarding Commerce offline functionality, see the additional links at the bottom of this article.

## Troubleshooting

If the following table does not list an error that you are receiving, create a support request, so that Microsoft Support can help you fix the issue. This section will be updated over time with additional errors so it is valuable to review this document prior to implementing or updating Modern POS or Store Commerce registers that utilize offline databases. Note that all troubleshooting errors begin with **Microsoft_Dynamics_**. This is omitted for purposes of shortening error codes.

| Error | Description |
|--------------------------------------------|-------------------------------------|
| Commerce_Runtime_AuthenticationFailed Commerce_Runtime_AuthorizationFailed | A logon related issue has occurred. This could be due to data not correctly found or configured in the offline database. |
| Commerce_Runtime_AuthenticationMethodDisabled Commerce_Runtime_ChannelConfigurationNotFound Commerce_Runtime_ChannelNotPublished Commerce_Runtime_ChannelRecordNotFound Commerce_Runtime_EmployeePermissionContextNotFound Commerce_Runtime_InvalidChannel Commerce_Runtime_InvalidChannelConfiguration Commerce_Runtime_StaffIdContextMissing |  Unable to switch to offline mode. The channel information is either not available or not configured correctly. To resolve this issue, run the Channel configuration scheduler job (by default, this is the 1070 scheduler job). Please contact your system administrator. |
| Commerce_Runtime_CredentialsNotConfigured Commerce_Runtime_CredentialsNotFound Commerce_Runtime_InvalidAuthenticationCredentials Commerce_Runtime_LocalLogonFailed Commerce_Runtime_UserBlockedDueToTooManyFailedLogonAttempts | Unable to switch to offline mode. The user information is either not available or not configured correctly. To resolve this issue, run the Staff scheduler job (by default, this is the 1060 scheduler job). Please contact your system administrator. |
| Commerce_Runtime_CriticalStorageError  | To check the status offline db permissions, size, disk space (could use offline dashboard) |
| Commerce_Runtime_ElevatedUserSameAsLoggedOnUser | This error occurs when the same user attempts to perform a manager override. A different user must be used. |
| Commerce_Runtime_RealtimeServiceNotSupported Commerce_Runtime_TransientStorageError | Unable to switch to offline mode. The offline database is either not correctly installed or not configured correctly. Verify that everything has been set up successfully. Please contact your system administrator. |
| Commerce_Runtime_TerminalNotFound Commerce_Runtime_DeviceConfigurationNotFound | To resolve this issue, run the Channel configuration scheduler job (by default, this is the 1070 scheduler job). Please contact your system administrator. |
| Internal_Server_Error Request_Timeout_Error Commerce_Runtime_InvalidFormat | These errors cover a variety of possible scenarios so we recommend to contact support and get assistance directly, where applicable. |

## Additional resources

- [Commerce offline implementation considerations](implementation-considerations-offline.md)
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)
- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)
- [Commerce Data Exchange best practices](CDX-Best-Practices.md)
- [Online and offline point of sale (POS) operations](../pos-operations.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
