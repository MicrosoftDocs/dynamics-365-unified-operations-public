---
title: User-Based authentication
description: This article explains how to configure user-based authentication to use with the Regression suite automation tool (RSAT).
author: FrankDahl
ms.date: 11/23/2023
ms.topic: how-to
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2023-11-15
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 
  - bap-template
---

# User-Based authentication

[!INCLUDE[banner](../../includes/banner.md)]

Certificate-based authentication to Dynamics 365 finance and Operations apps is planned to be removed. The Admin Center that replaces Microsoft Lifecycle Services no longer includes the option to download certificates. Regression suite automation tool (RSAT) usage needs to transition to replace certificates with user-based authentication. Finance and operations apps don't support authentication by a service principal like App Registration or by Managed Identity which means, only user-based authentication exists as option.

The recommendation is to use user-based authentication whenever this is possible. There are some conditions where this isn't possible. User-based authentication requires that a standard Microsoft online identity provider (https://login.microsoftonline.com/) is used to validate user accounts. It also requires that user authentication is configured without multifactor authentication (MFA) for accounts that are used to connect to your finance and operations app test environments. User account authentication times out and fails if a login is attempted with a user account with MFA enabled.

Microsoft recommends access to a finance and operations apps environment requires MFA. Disabling MFA should only be done with test accounts used by RSAT toward the finance and operations apps test environments. This is possible to configure on Microsoft Entra ID by Conditional Access Policies. For details on how this is configured, consult the online documentation. Using the Conditional Access Policies is a premium feature that needs to be subscribed to.

Finance and operations apps on-premises hosted environment aren't supported with ADFS user account identities. This means these environments deployed as Local Business Data can't use user-based authentication.

## How to set up user-based authentication

User-based authentication requires some extra steps to set up, but once it's configured centrally, set up of individual RSAT client environment becomes more seamless without concerns for installing certificates that are granted access to the test environment.

With this set up, access to finance and operations apps test environments happens when a user identified with a user account name and password log in just like how normal users log in.

RSAT requires passwords for test user accounts from parameter files when running tests. Test cases without a test user account in parameter files run using the admin user from RSAT settings, and RSAT then needs a password for this user too.

Passwords need to be maintained safely using an Azure Key vault. Each company must create and grant access for the Key vault to use with RSAT.

The Key vault is created as a resource under a subscription using the Azure portal. Creating this is done by one with technical experience in our organization which has access to this. Creating this Key vault is done centrally once and shared by RSAT client installations.

Use the Key vault to add secrets using the name of test accounts but remove any characters that aren't allowed. For instance, an account named frontname_surname@mydomain.com needs to remove illegal characters and change the name into frontnamesurnamemydomaincom as secret name.

The secret value is where the password is provided. Make sure this is entered exactly like it needs to be entered when logging in. No changes should be made to the password when saved as the secret value.

Consider the best practice and renew the password for test accounts regularly. When new passwords are set, remember to update the matching secret value in the Key vault.

Important, only include test accounts that are used for testing on Sandbox, UAT, or DevBox environments. It is strongly discouraged to use any real user accounts as test accounts because unintended access using these risks exposing access to business data. Also, only grant test accounts access to log into finance and operations apps that are hosted as Sandbox, UAT, or DevBox environments. Avoid granting test accounts access to production environments due to the potential risks this imposes.

RSAT automatically transforms test user accounts and removes illegal characters when looking up passwords. Continue to specify the test user accounts in parameter files and RSAT settings with full account names.

Access needs to be granted to RSAT to access the Key vault. This is done by creating an App registration under Microsoft Entra ID under the same Tenant where the Key vault was created. This is a shared identity used by the Key vault and RSAT.

This App registration is created with an Application (client) ID and has a Secret identified by a Secret ID with a Secret Value that acts as a password for the connection.

Access needs to be granted to the Key vault to the Application Registration. Within the Azure portal look up the Key vault resource and use Access Policies and Create a new policy that grant Get, and List secret permissions to the Application registration as selected Principal.


Information collected from setting Key vault and App registration is needed for completing setup in RSAT. First select the Authentication method **User-Based**, that exposes the new fields for the setup as seen below. Provide the Tenant ID, Key vault URL, Client ID, Secret ID, and Secret Value collected from prior steps.

![RSAT settings](media/rsat-settings.png)

Notice a thumbprint still needs to be selected for a certificate, however this certificate isn't used to gain access but used locally only. You can select **New** that is next to the field to create a new certificate that installs locally to complete this. You don't need to install the certificate to the hostname environment.


The secrets with the App registration or Client ID have an expiry and must be renewed periodically on Microsoft Entra ID. This means the Secret ID and the Secret Value need to be updated periodically. Obtain new updated values from the individual in your company that maintain this.

Settings files saved and loaded from RSAT settings don't include the Client Secret. This is excluded as an extra security precaution. The Client Secret must be entered manually and is saved only in the save storage we use as the Windows vault with Credentials Manager. Keep this in mind when configuring an environment to run RSAT by CLI like by pipelines, that you need to log into the environment with the user account RSAT is started under and manually provide this value in RSAT settings to save the value in the vault, such that this is used during playback.

## How to disable MFA for test accounts

As mentioned before, user-based authentication won't work for accounts that had multifactor authentication (MFA) enabled.

It is possible to configure tenants on Microsoft Entra ID and disable security defaults to disable MFA, but this disables MFA for all accounts and isn't recommended by Microsoft.

The secure approach is to disable MFA only for the test accounts used with running test cases by RSAT and only for environments used in testing.

This is possible by using Conditional Access Policies: [Building a Conditional Access policy](/entra/identity/conditional-access/concept-conditional-access-policies)


