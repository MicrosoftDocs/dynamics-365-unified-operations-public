---
title: Migrate a CHE load balancer 
description: Learn how to migrate a CHE load balancer for existing CHE environments.
author: pranavjani
ms.author: pranavjani
ms.topic: how-to 
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Migrate a CHE load balancer

[!INCLUDE[banner](../includes/banner.md)]

Microsoft Azure announced the retirement of classic load balancers. To ensure the continued provisioning of CHE environments, Microsoft implemented provisioning for new CHE environments, and migrating existing CHE environments.

## Provision new CHE environments

On March 28, 2025, all new CHE environments are configured with a load balancer and public IP address that utilizes the standard SKU. This transition helps enhance the performance and reliability of our cloud infrastructure.

## Migrate existing CHE environments

Before proceeding with migration, it's crucial to ensure that you have the necessary permissions and contributor access to the subscription. This access allows you to upgrade the load balancer without encountering any permission-related issues. Once you verify your access, you can proceed with setting the required variables and executing the migration commands.

To migrate existing CHE environments, follow these steps.

1. Set  subscription ID, resource group, and load balancer name variables

   ```powershell
   $resourceGroupName = “<resourcegroup-name>”
   $loadBalancerName = “<loadbalancer-name>”
   $subscriptionId = “<subscription-id>”
                    $outboundRuleName= "http-outbound-rule"
                    $backendPoolName = "vm-backend-pool"
   ```
1. Ensure you selected the correct subscription ID associated with the Basic Load Balancer by running the following command:

   ```powershell
   Select-AzSubscription –Subscription $subscriptionId
   ```

1. Run the following commands to initiate the load balancer migration. This command installs the load balancer upgrade module, and upgrades the basic load balancer and IP address to the standard SKU.

   ```powershell
   Install-Module -Name AzureBasicLoadBalancerUpgrade -Scope CurrentUser -   Repository PSGallery -Force
   Start-AzBasicLoadBalancerUpgrade -ResourceGroupName $resourceGroupName -BasicLoadBalancerName $loadBalancerName
   ```

   > [!NOTE]
   > The Basic Load Balancer supports outbound traffic by default, allowing seamless internet access for your virtual machines. However, the standard SKU load balancers don't automatically permit outbound access for backend pool members. Therefore, you need to take other steps to enable this critical functionality and ensure that your virtual machines can communicate with the internet for updates, data transfer, and other essential operations:

1. Create the backend pool.

   ```powershell
   $loadBalancer = Get-AzLoadBalancer -ResourceGroupName $resourceGroupName -Name $loadBalancerName
   $backendPool = New-AzLoadBalancerBackendAddressPoolConfig -Name $backendPoolName
   ```
 
1. To link all virtual machines (VM) to the standard load balancer, connect the NIC (network interface card) with the backend pool.

   ```powershell
   $nic = Get-AzNetworkInterface -ResourceGroupName $resourceGroupName
   $ipConfig = $nic.IpConfigurations | Where-Object { $_.PrivateIpAddress -ne $null }
   $ipConfig.LoadBalancerBackendAddressPools.Add($backendPool)
   ```   

1. Add the backend pool to the load balancer.

   ```powershell
   $loadBalancer.BackendAddressPools.Add($backendPool)
   $frontendIPConfig = $loadBalancer.FrontendIpConfigurations
   $outboundRule = New-AzLoadBalancerOutboundRuleConfig -Name $outboundRuleName -BackendAddressPool $backendPool -FrontendIpConfiguration $frontendIPConfig -Protocol All - 
   IdleTimeoutInMinutes 4 -AllocatedOutboundPort 1000
   $loadBalancer.OutboundRules.Add($outboundRule)
   Set-AzLoadBalancer -LoadBalancer $loadBalancer
   Set-AzNetworkInterface -NetworkInterface $nic
   ```

The backend pool should be created with following configurations:

  
## More information

- If any of the above commands fail or encounter an issue, refer to this comprehensive guide: [Upgrade a basic load balancer with PowerShell](/azure/load-balancer/upgrade-basic-standard-with-powershell).
- If you have multiple CHE environments, ensure the successful migration of one of the CHE environments before proceeding with bulk migrations.
- Learn about standard sku load balancer pricing in [Load Balancing pricing](https://azure.microsoft.com/pricing/details/load-balancer).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
