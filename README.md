# Automating EntraID User Creation 

This project leverages Power Apps as the front-facing interface for automating EntraID user creation. Designated users can seamlessly input new user information, which is then stored in a SharePoint list. This triggers an Azure Logic Apps workflow, automating the creation of new user profiles within EntraID.

* Azure Services Used
    * EntraID
    * Azure Logic Apps
    * Power Apps

The first step involved creating the sharepoint list and creating the columns necessary for the data fields in PowerApps. To keep it simple, I only required 4 fields: First Name, Last Name, Department and Job Title.
   ![image](https://github.com/zus119/AzureOnboard/assets/51805317/7c73c482-c0f2-4132-973d-ce107bf7228c)

   Next was creating the App. I linked the data to the sharepoint list previously created and got working on creating the necessary screens and logic expressions.
   
   ![image](https://github.com/zus119/AzureOnboard/assets/51805317/743e22c9-cecb-4447-9502-c0ef95f09f5f) ![image](https://github.com/zus119/AzureOnboard/assets/51805317/38fd032b-3a88-4c3e-8f04-e059441d8086)

Main Screen with an animated icon button.
![image](https://github.com/zus119/AzureOnboard/assets/51805317/99f1bef2-6ef3-4b60-adc7-cf6b2388ba55)

Simple User input form.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/5827322e-b8ac-449b-8b3d-e24a83994f77)

Animated "working on it" screen.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/65a3fac6-9640-4e97-bb21-3d9c60ecba87)

Once the new item is created in the sharepoint list, the azure logic app triggers and starts creating the new user. Logic App sits in its own resource group (OnboardAutomator-RG) to track spending.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/438d9048-ded2-4961-800c-da1a6b082fa2)


The sharepoint list is linked via the site address and list name.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/d1e38f87-0ec6-4024-b38c-ed6cc7860f71)


Assign the right data to the fields in the user portion of logic apps.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/89898c5e-4166-4079-9676-30b01229a1c4)

Since I wanted to take the first initial and concatenate it with the user's last name for the Mail Nickname property, I had to use a custom expression.
The same expression can be used for the User Principal Name in the format "CustomExpression"@domain.com

![image](https://github.com/zus119/AzureOnboard/assets/51805317/b1ec99b2-598a-4b31-bccb-0c47b50150c4)

Once the Logic App triggers, a new user is created in EntraID.

![image](https://github.com/zus119/AzureOnboard/assets/51805317/77318639-5645-4247-b11b-b2c7d308135d)

# Future Improvements

* Assign groups based on department
* Automatically assign licenses
* Automatically assign Azure resources
* Leverage Azure Hybrid worker and Azure Automation account to expand user creation to on-prem servers.








