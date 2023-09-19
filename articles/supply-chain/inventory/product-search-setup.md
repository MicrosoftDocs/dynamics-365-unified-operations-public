This article describes how to configure Product Search service using the Inventory Visibility app in Power Apps.

# Feature introduction

The product search solution support attribute-based search, and this feature enabling efficient and user-friendly product discovery. 

## Configure Product Search service


1. Install and update Inventory Visibility add-in in your environment.

   **For new customers**

    Please refer to this documentation for Inventory Visibility add-in setup: https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-setup

   **For existing customers**

   - **Update** your Inventory Visibility solution to latest version(1.2.2.54 or above) first in PPAC and make sure your FnO environment version is above 10.0.36.
     ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/24989b1c-5c93-4011-9fe7-5c0deda1b382)

    - Uninstall Inventory Visibility in your LCS project and then **install** it again.
     ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/1fbb51ed-52d2-4822-814d-cbf303ba188e)

2. Then to enrich attributes based on-hand search, please **enable Dual-write** in your LCS project. This needs System Admin role as following:
   
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/5feed8bc-d92f-48c1-af52-704322b3b9b3)

4. Log onto FnO application and refresh the data entity list first. **System administration -> Data management -> Framework parameters:**
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/78f5760f-5b9b-4c4e-a202-063888dc45a0)

5. Then you should be able to find Dynamics 365 Product Search Core solution and apply it to the table map list. **System administration -> Data management -> Dual write**, Click **Apply Solution**:
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/117fedd9-c228-4ebd-a94a-f28f17c54e2e)
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/80afb1bd-de83-4328-9591-3e7d6b1c68a4)

5.	Then it will process and please wait for it completed.
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/2b70e5a8-8e2e-432d-a46f-1a1e39594b5e)

7.	Once it’s done, **run the initial sync** for all table maps from the solution, check ‘Initial sync’ and select ‘Finance and Operations apps’ for Master for initial sync. Click run:
   ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/21149368-c3d2-4a27-98a9-d6937e96f9a3)







## Troubleshooting

For information about how to set up dual-write, see Guidance for dual-write setup.
If you see some maps won't do initial sync because of a permission issue make sure to go to the Advanced Settings from **Dataverse -> Settings -> Security-> Teams -> Manage Roles**:

![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/03f48f20-6a42-43ab-8381-3f1452712927)


Assign the following roles.
![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/4b789e91-a193-4da0-b12a-e7a41d57847f)


!Note: For more how to setup dual-write security roles: https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/security-roles



