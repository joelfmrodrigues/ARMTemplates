# Azure Web App

This ARM template deploys a Web App together with Application Insights, Storage and Key Vault.

The Web App is using Managed Service Identity to access the Key Vault.

The Web App settings contain the required keys to connect to the other resources.

You can find detailed information about the template on [this blog post](https://joelfmrodrigues.wordpress.com/2018/11/19/reusable-arm-template-for-web-app/).

## Requirements

To run the deployment script against a target Azure subscription, we need the subscription Id and object Id (Id of the admin user running the deployment script).
The following PowerShell commands will allow you to retrieve all the required information:

* Connect-AzureRmAccount
* Get-AzureRmSubscription
* Get-AzureRmADUser -Mail '{AzureAdminEmailAddress}'

Additionally, an Azure AD App Registration is required in order to configure Authentication.

## Deployment

To deploy the template, simply use one of the deployment files provided for your platform of choice and provide the required parameters.

The following example demonstrates how to deploy using PowerShell

.\deploy.ps1 -subscriptionId "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX" -resourceGroupName "Demo123AppDev" -resourceGroupLocation "West Europe" -deploymentName "Demo123AppDev" -templateFilePath "template.json" -parametersFilePath "parameters.json"