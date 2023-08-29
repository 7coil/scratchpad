# scratchpad

## Salesforce

### Prefixes

The first three characters of a Salesforce ID relates to the type of object it is.

### Browser Extension

Get the [firefox](https://addons.mozilla.org/en-GB/firefox/addon/salesforce-inspector/) browser extension.
It's pretty good.

## Windows Server

### (Azure Cloud Sync) Synchronise a user in a new forest with existing Azure AD users

If you have deleted your own Windows Server (because I am an idiot), you can
resync users with Azure AD.

> Prerequisite: Install `AzureAD` PowerShell module
> ```
> Install-Module AzureAd
> Connect-AzureAD
> ```

1. Create a new user in `Active Directory Users and Computers`
2. Get the GUID with `$guid = (Get-AdUser -Identity "Leondro").ObjectGUID`
3. Convert the GUID to Base64 with `$immutableid=[System.Convert]::ToBase64String($guid.tobytearray())`
4. (optional) Get a list of all your Azure AD users with `Get-AzureAdUser`
5. Overwrite ImmutableID with `Set-AzureAdUser -UserPrincipalName test@ramenthe.cat -ImmutableId $immutableid`
