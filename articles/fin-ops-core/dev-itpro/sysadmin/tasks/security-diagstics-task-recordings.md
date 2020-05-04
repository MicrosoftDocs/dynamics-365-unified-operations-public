# Security diagnostics for task recordings
[!include [banner](../../includes/banner.md)]

This topic describes how to analyze and manage security permission requirements based on a task recording.

## To diagnose security for a task recording:
1.	A task recording of the user process being analyzed is a prerequisite. To record a business process, see [Task recorder resources](../dev-itpro/user-interface/task-recorder.md)
2.	Go to **System administration > Security > Security diagnostic for task recording**.
3.	Open the task recording from its location, i.e. click **Open from this PC** or **Open from Lifecycle Services**.
4.	Click **Close**.
5.	This will open the Security menu item details form that lists the security objects required for the process.

   > [!NOTE]
    > Menu items of type Action and Output are currently not included in the list.

6.	Finding and selecting a **User ID** will update the Missing permissions field. 
    Yes, will be displayed if the user is missing permissions for menu item(s):

   [[Example of Security Menu Item Details](./media/Security-Menu-Item-Details.png)](./media/Security-Menu-Item-Details.png)

7.	Click **Add Reference**, to see a list of the security objects, i.e. Roles, Duties and Privileges that grant the missing permission.
8.	Select a security object from the list:
	  - If a Role is select click **Add role to user**, to open the [Assign users to roles form](../dev-itpro/sysadmin/media/role-to-user-assignments.png)
	  - If a Duty is selected click **Add duty to role** and then select the role(s) that the duty should be added to and click **OK**.
	  - If a Privilege is selected click **Add privilege to duties** and then select the role(s) that the duty should be added to and click **OK**.
