This page will document the functions in MicroBurst that rely on the [Az](https://docs.microsoft.com/en-us/powershell/azure/new-azureps-module-az) PowerShell module.

# Functions Information
## Get-AzPasswords
### Description:
This function will collect available credentials from the following services in Azure:
* App Services
    * Connection Strings
    * Publish Profiles
* Storage Accounts
    * Access keys
* Cosmos DB
    * Access Keys
* Container Registries
    * Admin user credentials
* Key Vaults
    * Keys
    * Secrets
    * Certificates
* Automation Accounts
    * Run as Service Principal Account certificates
    * Stored Credentials

### Usage:
Run with all services and all options:

`PS C:\> Get-AzPasswords -ExportCerts Y -ModifyPolicies Y -Verbose`

Run with all services:

`PS C:\> Get-AzPasswords -Verbose`

### Parameters:
Each service will have its own parameter (-StorageAccounts Y). By default, all services are set to 'Y', so disable any by setting the parameter to 'N'
* `-Subscription` - If not specified, the function will prompt you for a subscription to use
* `-ModifyPolicies` - Temporarily adds list and get rights for your current user in the key vault access policies
* `-ExportCerts` - Exports the Key Vault certificates to local files
* `-CertificatePassword` - The password used for exporting the automation account run as certificates

### Considerations:
The automation accounts section will create new runbooks in the automation accounts. These should get deleted by the script, but some times that delete fails. Additionally, the job run records will still show up in job logs, so it is a logged action.

If you have contributor rights, modifying the key vault access policies (not very opsec safe) can be a convenient way to access a vault.

***
## Get-AzDomainInfo
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Get-AzKeyVaultsAutomation
### Description:
### Usage:
### Parameters:
### Considerations:

***
## Invoke-AzVMBulkCMD 
### Description:
### Usage:
### Parameters:
### Considerations:
