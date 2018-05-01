How to add new location roles (aka Address and contact information purpose) and
party relationship types to the system

**\<Add new location roles to the system\>**

 

There are 2 ways to add a new location role:

1.  Add it through address and contact information purpose form. The new role
    will be saved into LogisticsLocationRole table with type = 0, which
    indicating the role is not a system role define in LogisticsLocationRoleType
    enum and its extensions. But user should still be able to use it when
    creating address or contact info.

    ![](media/06ec82de5ea9e75eb24a858bed39c1b8.png)

2.  Add it to LogisticsLocationRoleType enum extension, and let it populate
    through dbsync process.

    1.  Create an extension to LogisticsLocationRoleType enum and add the new
        role in the extension. (Example in core code:
        LogisticsLocationRoleType.Extension)

        ![](media/ba4f3afdede6e0b432ae5f7538231f65.png)

    2.  [./media/image3.png](./media/image3.png)

        Create a new resource file for the new role, and then assign value for
        its properties. (Example in core code:
        LogisticsLocationRoleDataForConsignment\_IN)

    3.  Create data population class and provide a handler method to populate
        the new role. (Example in core code: DirDataPopulation\_IN)

        ![](media/566a9053cfdacd074e44255495cf8c27.png)

    4.  To test, you can create a runnable class, and call
        DirDataPopulation::insertLogisticsLocationRoles() in Main(). After it is
        completed, you should be able to see the new role populated in
        LogisticsLocationRole table with type \> 0, and the new role should show
        up on address and contact information purpose form as well.

        ![](media/0ad346ba9919a4f97e6b8048f744281f.png)

**\<Add new party relationship types to the system\>**

There are 2 ways to add a new relationship type:

1.  Add it through relationship types form. The new relationship will be saved
    to DirRelationshipTypeTable with systemtype = 0.

    ![](media/9fc8639a16ae05c801689da75612377d.png)

2.  Add it to extension of DirSystemRelationshipType enum, and let it populate
    through DB sync process.

    1.  Create an extension to enum DirSystemRelationshipType and add the new
        relationship type in there.

    2.  [./media/image7.png](./media/image7.png)

        Create an initializer to this new type. You can find several examples in
        core code, one of them is DirRelationshipTypeChildInitializer, that is
        an initializer class for party relationship type “Child”. You can start
        with your initializer by copy and paste this code and then update the
        yellow parts accordingly.

    3.  To test, you can create a runnable class, and call
        DirDataPopulation::insertDirRelationshipTypes() in Main(). After it is
        completed, you should be able to see the new relationship type populated
        in DirRelationshipTypeTable, and the new relationship type should show
        up on relationship types form as well.

        ![](media/b7c7b05fd30a64eec9ee324c9ba98442.png)
