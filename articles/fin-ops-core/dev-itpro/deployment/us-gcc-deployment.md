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


 > [!NOTE]
    > For US government Microsoft Dynamics Lifecycle Services (LCS) projects, only Azure US government–specific Azure subscriptions are supported.
  

## Features not available

Due to certain technical dependencies, the following features listed will not be available for general availability of the Dynamics 365 Services in GCC. For information about feature availability, see [Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).

-   **Azure DevOps Services** will be unavailable in **Goverment cloud**. However, use of Azure DevOps on-premises or public Azure DevOps services will be available.


    
  > [!NOTE]
  > The Lifecycle Services URL for implementations operated by 21Vianet in China is lcs.dynamics.cn.



## Additional resources

- 	[Lifecycle Services (LCS) User guide](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md)  
-  [Cloud deployment overview](../../../fin-ops-core/dev-itpro/deployment/cloud-deployment-overview.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
