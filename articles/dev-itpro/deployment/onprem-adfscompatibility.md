# Local Agent 2.2.0 ADFS Office 365 Compatibility

[!include banner]

This topic provides information on how to use the same ADFS for Microsoft Dynamics for Finance and Operation On-Premises and Office 365.

## Existing Deployments

1.	Download the new local agent version from LCS. It should be version 2.2.0 or higher.  
2.	Redownload the configuration file as it has additional configuration needed for this functionality. 
3.	Modify the new local agent configuration file and set the office365AdfsCompatibility value to True.
4.	Uninstall the old local agent version from your cluster using the following command:
    ```powershell
    .\LocalAgentCLI.exe Cleanup '<path of localagent-config.json>' 
    ```
5.	Install the new local agent version using:
    ```powershell
    .\LocalAgentCLI.exe Install  '<path of localagent-config.json>' 
    ```
6.	Servicing the environment with PU28 or above will enable this new configuration. For existing environments with PU28 or above, doing any servicing operation will enable this new configuration.

7. After Servicing is complete run the following script:
    ```powershell
    .\Reset-DatabaseUsers.ps1 -DatabaseServer '<FQDN of the SQL server>' -DatabaseName '<AX database name>'. 
    ```
    Otherwise, the primary administrator user won’t be able to login. 	

8. Using the Service Fabric Explorer [Restart an AOS node](troubleshoot-on-prem.md#restartapplications)

9.	Additionally, it will be necessary to run a SQL query on the USERINFO table to modify the NETWORKDOMAIN field. If your old configuration was https://ax.contoso.com/adfs then you should change all your users entries to http://ax.contoso.com/adfs/services/trust 

## New Deployments

1.	Run through the LocalAgent Installation instructions in the [Setup and Deploy On-Premises](setup-deploy-on-premises-pu12.md#configureconnector) guide. However, before installing the LocalAgent do step 2 below. 
2.	Modify the local agent configuration file and set the office365AdfsCompatibility value to True.
3.	Continue going through the [Setup and Deploy On-Premises](setup-deploy-on-premises-pu12.md#configureconnector) guide and deploy a base version that contains PU28 or greater. If there is no base PU28 version, deploy the highest base version available. Then service with PU28 on top.


