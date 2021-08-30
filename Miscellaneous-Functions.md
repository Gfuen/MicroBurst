This page will document the functions in MicroBurst that don't really rely on a particular PowerShell module or API, but can be used against an Azure environment for testing. Additional auxiliary files (permutations.txt, KeyVaultRunBook.ps1, etc.) also live in this directory.

# Functions Information
## Get-AzureVMExtensionSettings.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Invoke-EnumerateAzureBlobs.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Invoke-EnumerateAzureSubDomains.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Get-AzACR.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## AutomationRunbook-OwnerPersist.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## OwnerPersist-POST.ps1
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Invoke-APIConnectionHijack.ps1
### Description: This script is a generic wrapper that will create a new Logic App with a provided definition. It will fill in several placeholder variables with the target connection details and also grabs any output/errors from the Logic App run. An example Logic App definition for dumping out a Key Vault is included.
### Usage: Invoke-APIConnectionHijack -logicAppRG "my-resource-group" -connectionName "keyvault" -definitionPath ".\payload.json"
### Parameters: 
* logicAppName - The name of the Logic App to be created. Default: Random
* logicAppRG - The resource group to create the Logic App in. This can be any RG that you have the Microsoft.Logic/* permission in.
* connectionName - The name of the API Connection to hijack
* definitionPath - The file containing your JSON Logic App definition
### Considerations: You should replace the name of any connections in your definition with "CONNECTOR_PLACEHOLDER". Additionally, the "connections" key in the "parameters" object should be empty, as it will be replaced by the script. This ensures everything is as generic as possible.
