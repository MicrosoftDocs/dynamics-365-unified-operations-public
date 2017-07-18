# Using regular fields to provide counts on the workspace

Using pageLink control for displaying counts on workspaces can be slow as it tries to load the target page and then count the number of rows. Also as we have a limit on total number of rows retrieved this can make the count wrong if the expected number is higher than the threshold.

 ![alt text](media/optimizing-workspace/Tiles_Original.png "Workspace with tiles")


To make mobile workspaces more faster, the recommended approach is to use regular fields to provide the count values and then model the fields as pageLink control in the mobile client. The demo below uses the Fleet Management app.

In the fleet management app we have the workspace that shows counts of total number of customers, reservations and vehicles. Previously these counts were coming from pageLink control that had "AllCustomers", "AllReservations" and "AllVehicles" as their targets respectively and the pageLink control was loading the rows  and doing the count. 

Below are the steps that we have taken to remodel the workspace page to use the new concept.

1. As we need fields on the server that now contain these counts we are creating a new form on the server. 
(You can also use an existing form and add these new fields). 
For the demo we have created a new form "FMMobSummary" with 3 fields that are tied to display method to get the counts.

    ![alt text](media/optimizing-workspace/FMMobSummary.png "Workspace with tiles")
	

2. Create a page using the mobile app designer for the form "FMMobSummary"

	![alt text](media/optimizing-workspace/NewPageInDesigner.png "New page in designer")
	

3. Mobile app business logic needs to be updated to transform the fields into pageLink control, we will use the configureControl api to add a navigation target to the fields (This will remodel the fields as pageLink control)

The arguments for configureControl are page name, control name and ab object of properties to be updated.


	
4. As we are using a custom design for workspace, the design needs to be updated.
We need to embed the summary page as a "part" in the workspace page. We are also referencing the fields are are now modelled as pageLink control and providing a style and setting the property "showCount:true" so that the count is shown on the pageLink control

    ![alt text](media/optimizing-workspace/ChangesToBL.png "Changes to business logic")

	
5. By using this approach you will also get the localized labels for pageLinks

The result is a much faster experience when loading workspaces.

![alt text](media/optimizing-workspace/FinalWorkspaceWithTile.png "Final workspace with optimized tiles")
