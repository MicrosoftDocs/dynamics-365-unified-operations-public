# Code and environment update procedures for Retail projects

An environment can be updated by either updating its data or its code.  

There are multiple ways to update the data. For good examples about how to get data into an environment, see [Data Entities and Data Packages](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/dataentities/data-entities-data-packages).  

Moving the entire database should also be considered when updating an environment. It’s a quick and easy way to duplicate the data from one environment to another. 

Other kinds of updates are code updates. The LCS environment page keeps track of which updates have been applied and what updates need to be applied. The following image shows an environment with 79 outstanding X++ fixes and 14 outstanding binary updates and 9 outstanding platform updates. 

[![LCS Environment Page](./media/17-LCS-environment-page.png)](/media/17-LCS-environment-page.png)
 
Platform code is very low-level and there is no Retail-feature that is implemented in the platform. This means, that stand-alone Platform binary updates will not require any Retail-specific code to be retested.  Examples of features that are implemented in the platform are Data Import and Export Framework (DIXF) and the batch framework. 

Binary updates or hotfixes include DLLs, scripts, channel SQL schema changes and more. All channel-side hotfixes are shipped with a binary update/hotfix. Because they are DLLs, binary updates are cumulative. If you download a binary update on Friday, you automatically get all binary hotfixes from Monday – thru Thursday.   

The version of a binary hotfix taken is exactly the version of the Retail Sdk’s Microsoft-version.txt file (assuming the code merging has been done correctly). Binary updates are tied to (usually) the latest platform too. So, you will have to stay up-to-date with the platform when taking binary updates. The platform updates increase stability of the platform, but it impacts build environments and test efforts to some extent.

Application updates or hotfixes delivered in X++ source code. Therefore, they are not for the channel, but for the client side (Retail or non-Retail related).  

Note that some updates require both an application and a binary update. See the next section for hotfix recommendations.  

Third-party packages are similar to application packages but developed by others. More information about ISV package usage can be found [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/dev-tools/manage-runtime-packages).  

The two main ways to update an environment are more detailed below.


### Updating data by restoring the database 

A useful and common operation is to move the entire database from one environment to another. This may be moving the production database to development environments when preparing to develop additional features. It could also be used to move the golden setup database to the production database as part of the go-live process.  

Whatever the reason, every time a database from a different environment is restored there are certain “links” in the database that may be broken.  The Environment reprovisioning tool fixes all these broken links for the default database group. It does not matter what type of environment is used. The general guideline is that if the database comes from a different server, the Reprovisioning tool must be run. 

The details about how to run this are outlined in [Copy Database From Azure SQL to SQL Server](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/database/copy-databasefrom-azure-sql-to-sql-server). 

The Reprovisioning tool should be run when the binary version of the target and destination database is the same. If that is not the case, either a build + dbsync (development environment) or deployment should also be done (sandbox, production).   

In many cases, the Retail scheduler should be reset whenever a database is being updated. 

After restoring the database, follow these steps:  

1. Build + db sync or deployment of the deployable package. 
> Note: If you have table extensions with data, you must have the metadata for these in the environment. If you do not, you may lose data as columns and tables may get dropped.  
2. Make sure batch service is running. 
3. Run the Environment reprovisioning tool (latest from global shared asset library, LCS/Maintain to deploy). 
4. Verify that the tool succeeded, verify that the Retail channel profile is up-to-date with the correct URLs, and that the data sync jobs for the Default data group succeeded.
5. In Finance and Operations, run “Initialize Retail Scheduler” to delete old data. This assumes that all CDX configuration changes are automated with the help of a resource file. If that is not the case, and tables, sub jobs, and jobs are manually created in the Retail channel schema, do not select the deletion of existing configuration. We reccomend that you automate this. See the development section for more details.

### Taking updates frequently  

If your project is further than a few weeks from go-live or the final UAT, we reccomend that you take all hotfixes (binary, X++ and platform) on a regular schedule. Doing this once a month is reccomended. In fact, the more often that you do this, the less issues occur as the code churn of the hotfixes is smaller. It will take substantially less time than 8 hours if you do this frequently. 

We do not suggest trying to pick and choose hotfixes, as this is more error-prone and likely not worth your time. If you have a count of 1000 or even 500, you should ask yourself if you are ready to go-live. You will get a more quality product if your LCS update tile count is very low (application fixes < 100, binary fixes < 10).   

After taking new hotfixes, the results of a previous UAT become less meaningful. It would be beneficial to retest, as this is dependent on the number of files that changed.  However, if hotfixes are being taken often, especially during the implementation phase, the number of new files is not too large.   

Another possible approach is to take all hotfixes frequently and only run part of all UATs.  The next time that new hotfixes are taken, a different part of UAT is run, in a circular fashion.  Before going live, a full UAT should be run. 

### Change propagation process through branches and environments

Just like the branching strategy is dictated by project, team or other constraints your project has the flexibility how the changes propagate through these branches. The process shown here can be used as an example. For some projects, it may be too simple. For others it may be too complex.  The important point is, a project should have a plan. Different persons in the team will have different responsibilities (dev, deployment, code merges, sign off, etc.) and the role ownership should be clearly decided.
 
#### Steps 1 – 3: Obtaining and applying updates

The full details about steps 1 – 3 (taking updates) is something already documented [here](https://dynamicsnotes.com/dynamics-365-for-finance-and-operations-hotfix-and-deployment-cheat-sheet/).  If you have the branches setup the same way as described above, you should be doing this work in the Dev branch.

#### Step 3.1 – 3.2: Keeping development environments up-to-date

If we do not have a build environment for the Dev branch that is not a big problem. In fact, it is usually not needed. All we need to do is coordinate what packages should be deployed to keep the version correct. 

Download binary updates and platform updates can simply be deployed via LCS’s package deployment.

For the X++ code, developers simply sync the Metadata folder and do a full build and db sync.  

If major new Retail changes have been checked in by others in the team (new files, configuration changes, new Retail sdk) it is not enough to just sync and build the new files. Remember, there are a few web applications installed on the developer machine that will not be simply updated with a compilation. The simplest way is to use LCS’s package deployment to deploy the retail package that can be produced on a MSBuild command prompt. Smaller changes to code do not require new package deployments to keep the dev environments in sync if the incremental changes are dropped to the install locations (more on that in the Retail Sdk section).
 
#### Step 4: Moving changes from Dev to Main

We separated the Dev and Main branches to have the opportunity to “leave some unwanted changes behind”. It is not required, but it’s good to have the option to do so.  The process of moving the code from Dev to Main is simple with Visual Studio. You can pick a range of changes, all or individual changes and merge them. If you want to keep it simple, have some sort of a code freeze in the Dev branch and when you are satisfied with the quality, merge all changes.  There is no reason to treat X++ different from the Retail Sdk. They live next together in each branch because they are dependent on each other.

#### Steps 4.1 – 4.2: Updating test environments

Use your build environment to produce officially built packages from the code in the Main branch. 
 
When the build is finished, find the built packages, download and rename them according your naming conventions.
 
Then, upload them to the LCS asset library. 
 
Finally, deploy them to your test environments.  
 
#### Step 4.3: Deploy to production environment

When all necessary tests pass, we are ready to deploy the same packages to production. The packages must be marked as Release Candidates in the LCS Asset library after they had been deployed and validated in a tier 2 or higher environment. Then the deployment must be planned and submitted via the LCS environment page. 
There are lots of things to consider when updating a production environment. Downtime, downtime mitigation, data migration, store updates, mass deployment and many more. It is very important to have a plan of all steps required for an update, as Retail projects usually require more than just a deployment. Some additional things to consider are listed below in the Tips section.
It is also assumed that the go-live planning has started much earlier. For more details consult [Implementation Lifecycle](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/implementation-lifecycle). 

#### Step 5: Merge the code from Main to ProdRel1

Before any new feature work starts being added to the Main branch and right after we deployed to production, a snapshot should be taken and move dot the ProdRel1 branch. The steps are the same as in step 4. We do not need to pick and choose changes, we simply merge all changes up to the last code change set that was submitted to Main branch.

### Updating build environments 

You should always deploy binary updates and platform updates using LCS’s package deployment. 

Finance and Operations and Retail customization packages should not be deployed to a build environment. 

### Comparing LCS tile counts 

Environments that should be at the same version level, should also have the same LCS tile counts.  If the tile counts are different, this may be caused by any of the following reasons: 

- The same deployable packages have not been deployed/applied and therefore the versions are different. You can troubleshoot by inspecting and comparing the LCS deployment history. 
- The scheduled task that collects the version information from an environment has not run yet. For development environments you can force the schedule task “LCSDiagnosticsCollector” to run. 
- The build environment’s application update counts do not match because X++ packages are not deployed on them. Binary and platform counts should be correct. 
- It may be on purpose. For example, if a developer works with the next version but the rest of the team is still working with a different release. Or, one development environment could have been kept on an older version in case a production hotfix needs to be developed (if the production environment uses older version as current development efforts). 
 

 
Notice that after updating an environment, the tile counts for the available updates are now substantially lower than at the start.  Ideally, these counts match on all environments that work on the same release.



### Moving to a new version 

If you want to upgrade to a new version (such as 7.2 to 7.3, or 7.3 to 8.0), you must deploy a new environment and target the new version.  If applicable, you also need to run a code upgrade and a database upgrade. More details can be found in [Code Migration Home Page](https://docs.microsoft.com/en-us/dynamics365/unifiedoperations/dev-itpro/migration-upgrade/code-migration-home-page). 

### Tips
-	Decide on a good package naming convention (for names in LCS asset library and zip packages when downloaded). The reason is that it will be easier to figure out what package you have deployed and where it came from. Avoid spaces in package names. Here is an example for a convention:
    - Platform update packages: PUXX_MMDDYY (XX is number of PU)
    - Binary update packages: BIN_MMDDYY
    -	X++ update packages: APP_MMDDYY
    -	Built X++ deployable packages: AX_BRANCH_VERSION (with appropriate branch name and VSTS version string)
    -	Built Retail combined package: RET_BRANCH_VERSION
-	Whenever you start a new item of work, use “Get latest” in the VSTS location you are working in
-	Any code submissions should use proper and detailed comments of the change sets
- Production Go-live procedures are important. The list below can serve as a reminder of what should be considered on your Go-live check list. Verify your Go-live checklist in a mock Go-live or UAT environment. This is not a complete list:
    - After deployment, does LCS show the expected deployment history with the correct packages?
    -	After deployment, does the LCS environment page and Dynamics 365 F&O show the correct and expected version numbers?
    -	Can MPOS offline mode be used during downtime of cloud (go offline, deploy, go online, sync offline transactions, update MPOS)?
    -	Does the Environment Reprovisioning tool need to be run (if database has been moved)?
    -	Batch jobs for CDX sync must be re-enabled by setting to “Waiting”
    -	“Initialize Retail scheduler” should be run
    -	Is there other data that needs to be setup in addition to the deployable packages (screen, button, receipt layouts, Azure Active Directory setup, Retail Shared parameters, tax configuration, other batch processes, DIXF recurring jobs, etc.)?
    -	Is a sync of the CDX data jobs required?
    -	Is a full sync of CDX data jobs required?
    -	Does this deployment require an update of store components as well?
    - If the store components had to be updated, do they show the new version numbers?
    -	Are the right experts available during the deployment (partner, ISV, customer, etc.)
    -	And more…

