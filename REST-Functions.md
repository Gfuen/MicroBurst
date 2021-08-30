This page will document the functions in MicroBurst that rely on the [Azure REST](https://docs.microsoft.com/en-us/rest/api/azure/) APIs.

## Get-AzDomainInfoREST
### Description:
This script attempts to replicate the functionality of Get-AzDomainInfo. The main purpose is to provide situational awareness about the access that a compromised Managed Identity has. 
### Usage:
Get-AzDomainInfo -managementToken $token -Verbose
### Parameters:
* Verbose - Including this parameter will output a high-level overview of enumerated resources to the console, plus a list of any roles the Managed Identity has.
* managementToken - A Managed Identity token scoped to "https://management.azure.com/"
* SubscriptionId - The subscription to enumerate. If this is not included, then you will be prompted with a list of available subscriptions.
* StorageAccounts - If set to "N", Storage Accounts will not be enumerated
* VMs - If set to "N", Virtual Machines will not be enumerated
* NetworkInfo - If set to "N", Network Information (NSGs, interfaces, etc.) will not be enumerated
* Resources - If set to "N", the complete list of resources will not be enumerated
* RBAC - If set to "N", the roles assigned to the token will not be enumerated
### Considerations:
By default, all information will be collected. The information collected is not 1-to-1 with Get-AzDomainInfo, as certain information cannot be queried in the same manner via the REST API.

***
# Functions Information
## Invoke-AzVMCommandREST
### Description:
This script will run a command on a Virtual Machine using the REST API. It will present a list of potential target VMs for you to choose from.
### Usage:
Invoke-AzVMCommandREST -subscriptionId "insert-subscription-id" -managementToken $token -commandToExecute "cmd.exe /c whoami"
### Parameters:
* subscriptionId - The name of the subscription to enumerate virtual machines for. If not provided, the script will enumerate available subscriptions.
* managementToken - The Managed Identity token that you obtained from the metadata endpoint.
* commandToExecute - The command you'd like to execute on the target VM.
### Considerations:
The output of the command will not be displayed. For that reason, you should either send the output Out-Of-Band or run a command where output does not matter, such as a C2 stager.

***
## Get-AZStorageKeysREST
### Description:
This script uses the REST API to obtain Storage Account Keys for any Storage Accounts in a subscription.
### Usage:
Get-AzStorageKeysREST -token $token
### Parameters:
* SubscriptionId - The target subscription. If not provided, you will be presented with a list of available subscriptions
* token - A Managed Identity token scoped to "https://management.azure.com/"
### Considerations:

***
## Get-AzAutomationAccountCredsREST
### Description:
This script uses the REST API to obtain credentials and RunAs connections from any available Automation Accounts. This emulates the behavior of the Automation Account portion of Get-AzPasswords.
### Usage:
Get-AzAutomationAccountCredsREST -managementToken $token -CertificatePassword "DontUseTheDefaultPassword"
### Parameters:
* SubscriptionId - The target subscription. If not provided, you will be presented with a list of available subscriptions
* managementToken - A Managed Identity token scoped to "https://management.azure.com/"
* CertificatePassword - The password used to decrypt the credentials that are displayed in the job output. Default: "TotallyNotaHardcodedPassword..."
### Considerations:
This script will leave a job in the "Jobs" tab of the target Automation Account. The job will contain the encrypted output of the script. 

***
## Get-AzKeyVaultKeysREST
### Description:
This script uses the REST API to dump out the keys from all available Key Vaults in a subscription.
### Usage:
Get-AzKeyVaultKeysREST -managementToken $mgmtToken -vaultToken $vaultToken
### Parameters:
* managementToken - A Managed Identity token scoped to "https://management.azure.com/"
* vaultToken - A Managed Identity token scoped to "https://vault.azure.net"
* SubscriptionId - The target subscription. If not provided, you will be presented with a list of available subscriptions
### Considerations:

***
## Get-AzKeyVaultSecretsREST
### Description:
This script uses the REST API to dump out the secrets from all available Key Vaults in a subscription.
### Usage:
Get-AzKeyVaultSecretsREST -managementToken $mgmtToken -vaultToken $vaultToken
### Parameters:
* managementToken - A Managed Identity token scoped to "https://management.azure.com/"
* vaultToken - A Managed Identity token scoped to "https://vault.azure.net"
* SubscriptionId - The target subscription. If not provided, you will be presented with a list of available subscriptions
### Considerations:
