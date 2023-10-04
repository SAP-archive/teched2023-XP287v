# Getting started

## Goal 🎯

In this exercise, you will create your two required trial accounts: one for SAP Landscape Management Cloud and one for the SAP Business Technology Platform

## Create your 30-day trial of SAP Landscape Management Cloud

After completing these steps you will have a trial account of SAP Landscape Management Cloud ready to be explored and to be used in this jump-start session.

1. Open [https://www.sap.com/products/technology-platform/landscape-management.html](https://www.sap.com/products/technology-platform/landscape-management.html)
2. Login with your SAP Account at the right of the page.
3. After logging-in, select `Try SAP Landscape Management Cloud`.
4. On the following page, select `Start your 30-day free trial`.
5. Once you see the "Congratulations" message, select `Click here to start your trial!`

This will create your trial tenant of SAP Landscape Management Cloud and afterwards open the onboarding wizard for the solution. As SAP Landscape Management Cloud is a software-as-a-service (SaaS) solution to manage SAP systems in infrastructure-as-a-service (IaaS) environments, you need to start by onboarding the IaaS account with certain permissions, policies, and credentials. In the trial environment, users can provide any details and no real IaaS account is required. If you plan on using SAP Landscape Management Cloud for your system landscape, the [Onboarding guide](https://help.sap.com/docs/SAP_LANDSCAPE_MANAGEMENT_CLOUD/e89209f1566d4a7aaf0631e1a1755653/fea7f79059bd42e5b6e76bcd9a07ba51.html?locale=en-US) describes all necessary steps and prerequisites.

For now, continue by selecting `Start Trial`. This will open a small survey to better understand your role in the organization. At its end, you can watch a solution overview video or skip it as we will discover the solution as part of the exercises. 

The trial tenant will open with a Guided Tour which you can skip. This will be part of exercise 1.

## Create your 90-day trial of SAP Business Technology Platform

1. Visit [https://www.sap.com/products/technology-platform/pricing.html](https://www.sap.com/products/technology-platform/pricing.html) 
2. Ensure you are still logged-on with your SAP account. If you are not, log on via ![Account icon](/assets/account-icon.png) at the top right. 
3. Select `Start your free 90-day trial`.
4. Select `Click here to start your trial!` in the pop-up.
5. Complete the following wizard which might require you to enter your mobile number.
6. As region, select "Singapore" on Microsoft Azure and wait for the wizard to finalize the setup of your SAP BTP trial account.

In case you accidently didn't create the account in Singapore on Microsoft Azure, but in the United States, you need to delete the existing one and create a new one.

1. In the "Account Explorer"" of the SAP BTP cockpit, select `...` of the subaccount's tile.
2. Select `Delete`.
3. Select the checkbox `I want to force delete this subaccount and all its data`.
4. Select `Delete Subaccount and Data`.
5. After its deletion, select `Create > Subaccount`.
6. Provide a "Display Name", e.g. `Trial`. 
7. Select as "Region" `Singapore`. 
8. On the lest side, select `Entitlements > Entity Assignments`.
9. In "Select Entities", select the icon to the right of the input field. 
10. Select the checkbox next to the name of the created subaccount. 
11. Select `Select`.
12. Select `Configure Entitlements`.
13. Select `Add Service Plans`.
14. From the list of the left, select `Alert Notification` and afterwards the checkbox on the right side next to "standard". 
15. On the left side, select `Cloud Foundry Runtime` and afterwards the checkbox on the right side next to "MEMORY".
16. Select `Add 2 Service Plans`.
17. Select `Save`. 
18. On the left side, select `Account Explorer`.
19. Select the created subaccount, e.g. "Trial".
20. Select `Enable Cloud Foundry`.
21. Select `Create`. 
22. After the creation is done, on the right side, select `Create Space`. 
23. Provide a "Name", e.g. "dev".

## Summary

Now that you have created trial accounts for SAP Landscape Management Cloud and SAP Business Technology Platform, you are ready to explore SAP Landscape Management Cloud. In a later step, you will start combining it with services offered as part of SAP Business Technology Platform. 

> ℹ INFORMATION: Both trial accounts will be deleted automatically at the end of the 30- or 90-days. There is no option to extend these time frames and there are no costs generated.

🎉 Continue to - [Exercise 1 - Get to know SAP Landscape Management Cloud](../ex1/README.md)
