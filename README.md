# 🚀 Google Maps API Key Rotation Workflow

This GitHub Actions workflow automates the rotation of your Google Maps API key and securely stores the new key in Azure Key Vault. It runs every 90 days or can be triggered manually.

## 📄 Workflow File Location
bash
Copy code
.github/workflows/rotate_google_maps_api_key.yml

## 🔧 How It Works

Creates a New Google Maps API Key:
The workflow uses Google Cloud CLI to generate a new API key with a unique name based on the current timestamp.

Stores the New Key in Azure Key Vault:
The new API key is securely stored as a secret in your Azure Key Vault.

Notifications on Failure:
Sends a Slack notification if the workflow fails.

## 🕒 Schedule
Automatic Rotation: Every 90 days at midnight UTC.
Manual Trigger: You can trigger the workflow manually via the GitHub Actions tab.

## 📋 Prerequisites
Google Cloud Setup:

Enable the Google Maps API in your Google Cloud Project.
Create a service account and download the JSON key.

Azure Setup:

Create an Azure Key Vault.
Set up an Azure Service Principal with permissions to write secrets.


## GitHub Secrets Configuration: 
Add the following secrets to your repository:
	
| Secret Name  |  Description | 
|:-----------------|:-----------------------------------------------------------|
|  GCP_PROJECT_ID |  Your Google Cloud Project ID |
|  GCP_SERVICE_ACCOUNT_KEY |  Base64-encoded Google Cloud service account key |
|  AZURE_KEYVAULT_NAME |  Your Azure Key Vault name |
|  AZURE_CLIENT_ID |  Azure Service Principal Client ID |
|  AZURE_TENANT_ID |  Azure Tenant ID |
|  AZURE_SUBSCRIPTION_ID |  Azure Subscription ID |
|  SECRET_NAME |  Name of the secret in Azure Key Vault |
|  SLACK_WEBHOOK_URL |  Slack webhook URL for notifications (optional) |

## 🛠️ Running the Workflow
Manual Run:
Go to the Actions tab in your GitHub repository, select the Rotate Google Maps API Key workflow, and click Run workflow.

Scheduled Run:
The workflow will automatically execute every 90 days as per the cron schedule.


## ⚠️ Update the token in the Service

After update the token on the Azure secret is necessary Update the service to use the new secret, how in the documentation don't have a reference about it was added only a example in the script about the command to restart a POD.

``` 
kubectl rollout restart deployment maps-service -n production
```

##  AI Tools

I used the AI tools to help me to generate the commands, but the script file was created by me. Still, the entire process and the validation of the code is the responsibility of the engineer that is using the AI, so it help a lot in some tasks that is necessary to create some command or specific resolution. Still, for me the essential is to know how to use the tool and how it can improve my job, but always will be necessary understand in deep how everything works before start to use some tools to help.
