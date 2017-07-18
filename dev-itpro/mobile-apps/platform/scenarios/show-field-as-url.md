# Customize a field to be shown as URL/email/phone using business logic

Fields shown on Operations mobile app pages can be customized to be shown as an email, telephone or a Url.

## Email field
If you mark a field as email using business logic, clicking on the field will open the mobile default email app with the field value shown as email address in the app.

## Phone field
If you mark a field as phone number using business logic, clicking on the field will open the mobile dialer app with the field value shown as phone number in the app.
Note that in iOS if the phone number is not valid it might not trigger the mobile dialer app.

## URL field
If you mark a field as URL using business logic, clicking on the field will open the url in the mobile default browser with the field value shown in the address bar.

Note that in iOS you need to provide the complete URL (starting from a protocol like http) in order for it to open the browser. Giving a url as www.microsoft.com will not work. You need to provide the url as http://www.microsoft.com

## Example
We would like to mark customer email and phone number field so that they can be clicked and opened in mobile OS default applications. Below is how the screen looks like before any changes are done. Note that the fields are not clickable.

 ![alt text](../../media/workspace-api/FieldAsURLOriginal.png "Customer details page without any changes")

Follow the following steps to mark a field as link.

1. In the business logic for the workspace add the following lines in appInit method. You can call configureControl passing in the page name and control name and then supplying in the LinkType for the control.
Currently we are supporting 'Telephone', 'Email' and 'Url' types.

    ![alt text](../../media/workspace-api/FieldAsURLBusinessLogic.png "Changes done in workspace business logic")

2. Upload the updated business logic file using Operations mobile app designer.

3. Refresh workspace metadata in Operations mobile client.

4. You will now have the fields shown as links.

    ![alt text](../../media/workspace-api/FieldAsURLFinal.png "Customer details page after the changes")


