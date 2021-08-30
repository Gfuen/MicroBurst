This page will document the functions in MicroBurst that don't really rely on a particular PowerShell module or API, but can be used against an Azure environment for testing. Additional auxiliary files (permutations.txt, KeyVaultRunBook.ps1, etc.) also live in this directory.

# Functions Information
## Get-AzureVMExtensionSettings.ps1
### Description:
This script will find and decrypt the private settings from any previously run VM Extensions. These settings may contain passwords or other sensitive information. 
### Usage:
(From an elevated prompt) Get-AzureVMExtensionSettings
### Parameters: N/A
### Considerations:
Only the most recently ran version of the extension can be decrypted and shown.

***
## Invoke-EnumerateAzureBlobs.ps1
### Description:
This script takes a base word and prefixes/suffixes it with a list of words to identify any storage blobs associated with a target. It will also attempt to enumerate any containers in the blob.
### Usage:
Invoke-EnumerateAzureBlobs -Base "netspi" -Permutations ".\permutations.txt"
### Parameters:
* Base - The base word to use
* OutputFile - Where to save the results
* Permutations - A path to a permutation wordlist
* Bing API Key - The API key to dork Bing with.
### Considerations:
The presence of the base word in a blob name does not indicate that it belongs to a given entity. Ensure that you are only testing resources that you have permission to test.

***
## Invoke-EnumerateAzureSubDomains.ps1
### Description:
This script takes a base word and a list of permutations and enumerates several Azure services for potential targets.
### Usage:
Invoke-EnumerateAzureSubDomains -Base "netspi" -Permutations ".\permutations.txt"
### Parameters:
* Base - The base word to use
* Permutations - A path to a permutation wordlist
### Considerations:
The presence of the base word in a subdomain does not indicate that it belongs to a given entity. Ensure that you are only testing resources that you have permission to test.

***
## Get-AzACR.ps1
### Description:
This script enumerates available ACR Container images in a given repository and returns "docker pull" commands to download each one.
### Usage:
Get-AzACR -username "netspi" -password "password" -registry "netspiacr.azurecr.io"
### Parameters:
* username - The username to authenticate with
* password - The password to authenticate with
* registry - The registry to authenticate to
* all - If included, all image tags will be dumped. By default, only the first is dumped.
### Considerations:

***
## AutomationRunbook-OwnerPersist.ps1
### Description:
This is a runbook that can be configured with a webhook for persistence. If your access is terminated, you can send a POST request (as specified in OwnerPersist-POST.ps1) to reestablish access.
### Usage:
Import this runbook into an Automation Account and configure it with a webhook. Make sure that you save the webhook token.
### Parameters:
### Considerations:

***
## OwnerPersist-POST.ps1
### Description:
This script specifies the format for the request to be used with AutomationRunbook-OwnerPersist.ps1. The specified username and password will be used by the runbook to create the new account.
### Usage:
### Parameters:
### Considerations:

***
## Invoke-APIConnectionHijack.ps1
### Description: 
This script is a generic wrapper that will create a new Logic App with a provided definition. It will fill in several placeholder variables with the target connection details and also grabs any output/errors from the Logic App run. An example Logic App definition for dumping out a Key Vault is included.
### Usage: 
Invoke-APIConnectionHijack -logicAppRG "my-resource-group" -connectionName "keyvault" -definitionPath ".\payload.json"
### Parameters: 
* logicAppName - The name of the Logic App to be created. Default: Random
* logicAppRG - The resource group to create the Logic App in. This can be any RG that you have the Microsoft.Logic/* permission in.
* connectionName - The name of the API Connection to hijack
* definitionPath - The file containing your JSON Logic App definition
### Considerations: 
You should replace the name of any connections in your definition with "CONNECTOR_PLACEHOLDER". Additionally, the "connections" key in the "parameters" object should be empty, as it will be replaced by the script. This ensures everything is as generic as possible.
