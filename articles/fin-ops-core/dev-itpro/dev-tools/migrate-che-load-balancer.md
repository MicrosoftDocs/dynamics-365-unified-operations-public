---
title: Migrate a CHE load balancer 
description: 
author: pranavjani
ms.author: pranavjani
ms.topic: how-to 
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Migrate a CHE load balancer

Azure has announced the retirement of classic load balancers. To ensure the continued provisioning of CHE environments, we have implemented following actions:

## Provisioning for New CHE Environments

Starting from March 28th, 2025, all new CHE environments will be configured with load balancer and public IP address utilizing the standard SKU. This transition also helps to enhance the performance and reliability of our cloud infrastructure.

## Migrate existing CHE environments

Before proceeding with the migration, it is crucial to ensure that you have the necessary permissions and contributor access to the subscription. This will allow you to upgrade the load balancer without encountering any permission-related issues. Once you have verified your access, you can proceed with setting the required variables and executing the migration commands.

To migrate existing CHE environments, follow these steps.

1. Set  subscription id, resource group, and load balancer name variables

   ```powershell
   $resourceGroupName = “<resourcegroup-name>”
   $loadBalancerName = “<loadbalancer-name>”
   $subscriptionId = “<subscription-id>”
                    $outboundRuleName= "http-outbound-rule"
                    $backendPoolName = "vm-backend-pool"
   ```
1. Ensure you have selected the correct subscription ID associated with the Basic Load Balancer by executing the following command:

   ```powershell
   Select-AzSubscription –Subscription $subscriptionId
   ```

1. Execute the following commands to initiate the load balancer migration. This command will Install the load balancer upgrade module and upgrades the basic load balancer and IP address to the standard SKU.

   ```powershell
   Install-Module -Name AzureBasicLoadBalancerUpgrade -Scope CurrentUser -   Repository PSGallery -Force
   Start-AzBasicLoadBalancerUpgrade -ResourceGroupName $resourceGroupName -BasicLoadBalancerName $loadBalancerName
   ```

   > [!NOTE]
   > The Basic Load Balancer supports outbound traffic by default, allowing seamless internet access for your virtual machines. However, the Standard SKU Load Balancers do not automatically permit outbound access for backend pool members. Therefore, you need to take additional steps to enable this critical functionality and ensure that your virtual machines can communicate with the internet for updates, data transfer, and other essential operations:

1. Create the backend pool.

   ```powershell
   $loadBalancer = Get-AzLoadBalancer -ResourceGroupName $resourceGroupName -Name $loadBalancerName
   $backendPool = New-AzLoadBalancerBackendAddressPoolConfig -Name $backendPoolName
   ```
 
1. Connect the NIC (network interface) with the backend pool to link all VMs to the Standard Load Balancer.

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

Backend Pool should be created with following configurations:
  
## Notes
- If any of the above commands fail or encounter issues during execution, please refer to this comprehensive guide: [Upgrade a basic load balancer with PowerShell](/azure/load-balancer/upgrade-basic-standard-with-powershell).
- For customers having multiple CHE environments, please ensure the successful migration of one of the CHE environments before proceeding with bulk migrations.
- Learn about Standard sku load balancer related pricing in [Load Balancing pricing](https://azure.microsoft.com/en-in/pricing/details/load-balancer).

