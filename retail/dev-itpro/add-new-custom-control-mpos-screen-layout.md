---
# required metadata

title: Add a custom control to an MPOS screen layout
description: This topic explains how to add a new custom control to a Modern POS (MPOS) screen layout.
author: josaw1
manager: AnnBe
ms.date: 2016-03-17 18 - 11 - 06
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 65801
ms.assetid: 99079d81-fde2-4432-8cee-82bbcc3bd57e
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Add a custom control to an MPOS screen layout

This topic explains how to add a new custom control to a Modern POS (MPOS) screen layout.

Scenario
--------

You want to provide the cashier and manager more information about sales. For example, you want to add information to the transaction page, such as the total quantity that was purchased and the number of voided lines in the transaction. You can use a custom control to add this information.

## Add the custom control
1.  Start Microsoft Visual Studio as an administrator.
2.  Open the Modern POS (MPOS) solution. The location of the folder for the solution depends on your solution topology.
3.  In the POS.App project, in the Views\\Controls folder, add a new HTML page, and name it **CustomControl.html**.
4.  In the POS.App project, in the Views\\Controls folder, add new TypeScript file, and name it **CustomControl.ts**.
5.  Open the CustomControl.html file, and replace the existing code with the following code. This code adds two new properties and binds them to the **CustomControlOptions** class.

        <!DOCTYPE html>
            <html>
                <head>
                    <meta charset="utf-8" />
                    <title>CustomControl</title>
                </head>
                <body>
                    <div data-bind="customControlInternal: 'CustomControlOptions'">
                        <div class="panel marginBottom1 marginTop05 primaryPanelBackgroundColor highContrastBorderThin height01">
                            <div class="row padTop1 padBottom0">
                                <div class="secondaryFontColor"><h4>Total quantities:</h4></div>
                                <div class="textRight"><h4 data-bind="text: _quantities" class="wrapText"></h4></div>
                            </div>
                            <div class="row padTop1 padBottom0">
                                <div class="secondaryFontColor"><h4>Voided lines:</h4></div>
                                <div class="textRight"><h4 data-bind="text: _voidedLines" class="wrapText"></h4></div>
                            </div>
                        </div>
                    </div>
                </body>
            </html>

6.  Open the CustomControl.ts file, and add the following code. There are two methods. One method retrieves the total quantities, and the other retrieves the voided quantities. The values are assigned to private variables that are bound to the user interface on the HTML page.

        ///<reference path='K:\RainMainStab\7.0.1265.3014\retail\Services\RetailSDK\Code\POS\SharedApp\Views\Controls\UserControl.ts'/>
        module Commerce.Controls {
            "use strict";
            /**
            * Options passed to the custom control.
            * To pass more variables, change here and at the caller CartView.html (options: { data: ... })
            */
            export interface ICustomControlOptions {
                data: Proxy.Entities.Cart;
            }
            /*** User control for rendering custom control. */
            export class CustomControl extends UserControl {
                // Observable that is binded to the control's UI
                // See ExtraControl.html (data-bind="text: _quantities")
                private _quantities: Observable<number>;
                private _voidedLines: Observable<number>;
                /*** Initializes a new instance of the ExtraControlOptions class.  This is called every time the cart is changed.  */
                constructor(options: ICustomControlOptions) {
                super();
                options = options || { data: undefined };
                // Calculate the total quantities at lines and set to the observable.
                this._quantities = ko.observable(this.getTotalQuantity(options.data));
                this._voidedLines = ko.observable(this.getVoidedQuantity(options.data));
            }
            private getTotalQuantity(cart: Proxy.Entities.Cart): number {
                var totalQuantity: number = 0;
                if (ObjectExtensions.isNullOrUndefined(cart) || !ArrayExtensions.hasElements(cart.CartLines)) {
                    return totalQuantity;
                }
                cart.CartLines.forEach((cartLine: Proxy.Entities.CartLine) => {
                    if (!cartLine.IsVoided) {
                        totalQuantity = totalQuantity + cartLine.Quantity;
                } });
                return totalQuantity;
            }
            private getVoidedQuantity(cart: Proxy.Entities.Cart): number {
                var voidedQuantity: number = 0;
                if (ObjectExtensions.isNullOrUndefined(cart) || !ArrayExtensions.hasElements(cart.CartLines)) {
                    return voidedQuantity;
                }
                cart.CartLines.forEach((cartLine: Proxy.Entities.CartLine) => {
                    if (cartLine.IsVoided) {
                        voidedQuantity = voidedQuantity + 1;
                }});
                return voidedQuantity;
            }  }
        }

7.  Compile the project.
8.  Before you deploy MPOS, you must add the new custom control in the screen layout designer and set the relative URL. Sign in to the client, and go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS** &gt; **Screen layouts**.
9.  Select the **F2MP16:9M** screen layout, and then, on the Action Pane, click the **Designer** button.
10. If you're prompted to install the designer tool, click **Open**, and follow the installation instructions.
11. After the installation is completed, you're prompted for your Microsoft Azure Active Directory (Azure AD) credentials. Provide them to start the designer.
12. In the designer, drag the custom control to the transaction page.
13. Right-click the custom control on the transaction page, and then click **Customize**.
14. Set the relative URI to **Views/Controls/CustomControl.html**, and then click **OK**.
15. In the designer, click the **Close** button.
16. When you're prompted to save your changes, click **Yes**.
17. Go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
18. Select the **Registers** (**1090**) job, and then click **Run now**.
19. After the job has finished running, deploy MPOS from Visual Studio by clicking the **Deploy** button.

## Validate the customization
1.  Sign in to MPOS by using **000160** as the operator ID and **123** as the password.
2.  On the welcome screen, click the **Current transaction** button.
3.  Add any item to the transaction, and verify that the total quantity is shown correctly in the custom control.
4.  Void any line in the transaction, and verify that the voided line count is shown correctly in the custom control.


