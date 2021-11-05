# Dynamics 365 Finance and Dynamics 365 Supply Chain Management in US Government Community Cloud (GCC)

[!include [banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Select Dynamics 365 US Government products are available to qualified government and private entities, limited to (i) United States (US) federal, state, local, tribal, and territorial government entities; (ii) private entities using Dynamics 365 US Government to provide solutions to a government entities or a qualified member of the cloud community; and (iii) private entities with customer data subject to government regulations for which the use of Dynamics 365 US Government is the appropriate service to meet the regulatory requirements.
For information , see [Dynamics 365 US Government](/power-platform/admin/microsoft-dynamics-365-government).

## Onboarding

To perform initial onboarding steps for an implementation project in Lifecycle Services (LCS), follow the instructions detailed at [Onboard an implementation project](../../../fin-ops-core/fin-ops/imp-lifecycle/onboard.md). However, please note the following URL should be used in place of the Lifecycle Services specified there.

 > [!NOTE]
    > The URL to access Lifecycle Services (LCS) for the US Government Community Cloud is [Dynamics Lifecycle Services GCC](https://gov.lcs.microsoftdynamics.us)

Once the initial onboarding steps are complete in Lifecycle Services (LCS), proceed to follow the instructions at [Project onboarding](../../../fin-ops-core/dev-itpro/lifecycle-services/project-onboarding.md). Again, be sure to substitute the URL above for LCS.

## Environment Deployment

After completing project onboarding as described above you may review additonal capabilities of LCS at [Lifecycle Services (LCS) for Finance and Operations apps customers](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs.md) and then proceed to environment deployment. 

- For deployment of Microsoft managed environments via LCS, follow the instructions at [Lifecycle Services (LCS) for Finance and Operations apps customers](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs.md#new-deployment-experience)  

- **For Cloud hosted environment**, see [Deploy and access development environments](../../../fin-ops-core/dev-itpro/dev-tools/access-instances.md).
- You must complete the Resource Manager onboarding process for your connectors, see [Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects](../../../fin-ops-core/dev-itpro/deployment/arm-onbarding-us-goverment).

For information on provisioning environments, see [Create and manage environments in the Power Platform Admin center](/power-platform/admin/create-environment).

 > [!NOTE]
    > For US government Microsoft Dynamics Lifecycle Services (LCS) projects, only Azure US government–specific Azure subscriptions are supported.
  

## Features not available

Due to certain technical dependencies, the following features listed will not be available for general availability of the Dynamics 365 Services in GCC. For information about feature availability, see [Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).

-   **Development, build, and testing of customizations** will be unavailable in **Azure DevOps in Mainland China**. However, use of Azure DevOps on-premises will be available in China in April 2019. Also, Azure DevOps can be used in other regions. For more information, see [Developer guide for Azure China 21Vianet](/azure/china/china-get-started-developer-guide).

-   [Set up and maintain vendor collaboration](../../../supply-chain/procurement/set-up-maintain-vendor-collaboration.md) will be unavailable due to Azure Active Directory limitations.

-   Certain **mobile apps** (e.g., [Install and configure the Warehousing app overview](../../../supply-chain/warehousing/install-configure-warehousing-app.md) and [Project time entry mobile workspace](/dynamics365/project-operations/prod-pma/project-time-entry-mobile-workspace)) will be unavailable due to the Google Play Store not being available in China; however, alternatives are being considered.


    
  > [!NOTE]
  > The Lifecycle Services URL for implementations operated by 21Vianet in China is lcs.dynamics.cn.

-   The following features will not be available due to certain **current Azure Active Directory limitations** in China:

    -   The **System administration \> Setup \> B2B Invitation configuration** page will not be available due to business-to-business (B2B) being unavailable in Azure Active Directory in China. For more information, see [What is guest user access in Azure Active Directory B2B](/azure/active-directory/b2b/what-is-b2b).

-   [Conditional access](/azure/active-directory/conditional-access/technical-reference) is an Azure Active Directory feature that is available for the Azure Active Directory Premium 2 SKU. This is unavailable in China. 
-   The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China.

## Additional resources

- 	[Lifecycle Services (LCS) User guide](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md)  
-  [Cloud deployment overview](../../../fin-ops-core/dev-itpro/deployment/cloud-deployment-overview.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
