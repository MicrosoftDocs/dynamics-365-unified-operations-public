---
# required metadata

title: Dynamics 365 Finance and Dynamics 365 Supply Chain Management operated by 21Vianet in China 
description: This topic provides information about Dynamics 365 Finance and Dynamics 365 Supply Chain Management - operated by 21Vianet in China.
author: kfend
ms.date: 04/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version:  

---

# Dynamics 365 Finance and Dynamics 365 Supply Chain Management operated by 21Vianet in China

[!include [banner](../includes/banner.md)]



Microsoft Dynamics 365 online services operated by 21Vianet is designed to comply with regulatory requirements in China. The services are a physically separated instance of cloud services operated and transacted by a local operator, Shanghai Blue Cloud Technology Co., Ltd (“**21Vianet**”). This is a wholly owned subsidiary of Beijing 21Vianet Broadband Data Center Co., Ltd. located in mainland China.

Microsoft strives to maintain functional parity between our commercially available service and Finance and Operations apps operated by 21Vianet in China. However, there are notable exceptions to this, which are affected by dependent service or partner-solution availability, market priorities, or compliance regulations.

## Provisioning

Customers in China have two options from which to select how they want to access Finance and Supply Chain Management apps.

- Services operated by 21Vianet in China - 21Vianet operates and offers Finance and Supply Chain Management services in China. This option provides a consistent application experience that is the same as global offerings. This option also meets the demands of customers who prefer to use online services provided by a local company that stores their data within China. These services are subject to Chinese laws.

- Services operated by Microsoft – This option is for Finance and Supply Chain Management customers that prefer to use services managed and delivered by Microsoft. For all new customers and existing customers, if the customer purchases Microsoft Azure, Dynamics 365, and Office using an Enterprise Agreement, Microsoft 365 and/or Dynamics 365 can co-exist on the tenant.

For information on provisioning environments, see [Create and manage environments in the Power Platform Admin center](/power-platform/admin/create-environment).

## Features not available

Due to certain technical dependencies, the following features listed will not be available for general availability of the Dynamics 365 Services operated by 21Vianet. For information about future feature availability, see [Business applications and platform release plans](/dynamics365/release-plans/).

-   **Development, build, and testing of customizations** will be unavailable in **Azure DevOps in Mainland China**. However, use of Azure DevOps on-premises will be available in China in April 2019. Also, Azure DevOps can be used in other regions. For more information, see [Developer guide for Azure China 21Vianet](/azure/china/china-get-started-developer-guide).

-   [Set up and maintain vendor collaboration](../../../supply-chain/procurement/set-up-maintain-vendor-collaboration.md) will be unavailable due to Azure Active Directory limitations.

-   Certain **mobile apps** (e.g., [Install and configure the Warehousing app overview](../../../supply-chain/warehousing/install-configure-warehousing-app.md) and [Project time entry mobile workspace](/dynamics365/project-operations/prod-pma/project-time-entry-mobile-workspace)) will be unavailable due to the Google Play Store not being available in China; however, alternatives are being considered.

-   The **[mobile platform](../mobile-apps/platform/mobile-platform-home-page.md)** will not be available because certain App store dependencies are unavailable in China.

-  **SharePoint integration** isn't available, because the authentication mechanism that Finance and Operations apps use with SharePoint isn't supported in this configuration.

-   The following **Microsoft Dynamics Lifecycle Services (LCS)** features will have a different experience or will be unavailable due to the dependencies that are not available:

    -   **APQC Business process modeler (BPM) Library** will be unavailable. However, base Business process modeler (BPM) functionality will be available for custom models in April 2019. Search functionality in the BPM will be unavailable in China.

    -   **[Electronic reporting (ER) overview](../analytics/general-electronic-reporting.md?toc=/fin-and-ops/toc.json) assets** will not be available automatically, but can be manually uploaded from the LCS global asset library.

    -   **Code upgrade** will be unavailable for upgrades from Dynamics AX 2012.

    -   **Service and Support requests** will be available through LCS but 21Vianet is the service operator. For more information, see [Support for Dynamics 365 Finance and Operations apps operated by 21Vianet in China](../lifecycle-services/21vianet-support.md).
    
    -   [Extensibility requests](../extensibility/extensibility-requests.md) will be unavailable.
    
    -   Hotfix requests will be unavailable.

    -   [Dynamics 365 Translation Service overview](../lifecycle-services/translation-service-overview.md) will not be available.

    -   [Embedded Power Apps](../../fin-ops/get-started/embed-power-apps.md) and connectivity to Microsoft Power Apps and Microsoft Power Automate will be unavailable.

    -   [Integrate data into Microsoft Dataverse](/power-platform/admin/data-integrator) will be unavailable.
    
  > [!NOTE]
  > The Lifecycle Services URL for implementations operated by 21Vianet in China is lcs.dynamics.cn.

-   The following features will not be available due to certain **current Azure Active Directory limitations** in China:

    -   The **System administration \> Setup \> B2B Invitation configuration** page will not be available due to business-to-business (B2B) being unavailable in Azure Active Directory in China. For more information, see [What is guest user access in Azure Active Directory B2B](/azure/active-directory/b2b/what-is-b2b).

-   [Conditional access](/azure/active-directory/conditional-access/technical-reference) is an Azure Active Directory feature that is available for the Azure Active Directory Premium 1 SKU. 
-   The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China.

## Additional resources

- [Dynamics 365 support site for 21Vianet (Chinese)](https://www.21vbluecloud.com/Dynamics365/)
- [Support for Dynamics 365 Finance and Operations apps operated by 21Vianet in China](../lifecycle-services/21vianet-support.md)
- [Model-driven apps in Dynamics 365 - operated by 21Vianet in China](/dynamics365/customer-engagement/admin/datacenter/about-microsoft-cloud-china)
- [Dynamics 365 Privacy statement (Dynamics 365 隐私声明)](https://www.21vbluecloud.com/Dynamics365/d365-privacy/)
- [Dynamics 365 Service Level agreement (世纪互联在线服务的服务级别协议)](https://www.21vbluecloud.com/Dynamics365/d365-sla/)
- [Dynamics 365 Legal information (Dynamics 365 法律信息)](https://www.21vbluecloud.com/Dynamics365/dynamics365-legal/)
- [Service terms for Dynamics 365 Lifecycle Services](https://www.21vbluecloud.com/dynamics365/d365-lcs/)
- [OSPT of Dynamics 365 (世纪互联在线服务的服务级别协议)](https://www.21vbluecloud.com/ostpt/)
- [Azure Docs (in Chinese)](https://docs.azure.cn/zh-cn/)
- [Azure China 21Vianet](/azure/china/china-welcome)
- [Business applications availability in China – operated by 21Vianet in China](/power-platform/admin/business-applications-availability-china)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
