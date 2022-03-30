# BloodHound

[Documentation Link](https://bloodhound.readthedocs.io/en/latest/index.html)

[Download Link](https://bloodhound.readthedocs.io/en/latest/index.html#install)

Bloodhound a peice of software that uses graph theory to reveal the hidden relationships within an Active Directory environment. Has no data ingest capabilities, and relies on either SharpHound or AzureHound to collect data.

---
Once you have collcted data from either SharpHound or AzureHound both will generate JSON files and place them in a zip folder. Dragging and dropping that zip file on to the BloodHound GUI will import the data.
# SharpHound
[Documentation](https://bloodhound.readthedocs.io/en/latest/data-collection/sharphound.html)

[Download Link](https://github.com/BloodHoundAD/SharpHound)

## Basic Data Collection
Running the SharpHound executable will collect a good amount of data. To do so run:

`C:\> SharpHound.exe`

## In-Depth Data Collection

The more data BloodHound is give, the more likly is it to discorver an attack path. SharpHound has a function called *Session Loop Collection Method* This method of collection is useful when trying to aquire data on User sessions, since this data is quite volatile.

The command for this collection method is:
`C:\> SharpHound.exe --CollectionMethod Session --Loop`

The default run time is 2 hours, if another runtime is preferred if can be specified using: `C:\> SharpHound.exe --CollectionMethod Session --Loop --Loopduration HH:MM:SS`

# AzureHound
[Documentation](https://bloodhound.readthedocs.io/en/latest/data-collection/azurehound.html)

Used to gather data with in [Azure](https://azure.microsoft.com/en-us/overview/what-is-azure/) and Azure AD

## Installation
### Dependencies
* Az 
* Azure AD
* PowerShell 5.1 =<

### Steps

1. Set TLS to 1.2 using `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
2. (Once Az is installed) import AzureHound with `Import-Module C:\path\to\AzureHound.ps1`
3. Login using `Connect-AzAccount` AND `Connect-AzureAD`

## Usage
You can use AzureHound by entering `Invoke-AzureHound`
