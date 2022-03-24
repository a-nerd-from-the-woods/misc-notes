# What is Mimikatz: The Beginner's Guide
[Article Link](https://www.varonis.com/blog/what-is-mimikatz)

Mimikatz is an open-source application that allows users to view and save authentication credentials. 

[Mimikatz Download Link](https://github.com/gentilkiwi/mimikatz/releases)

## Capabilities
* Pass-the-Hash
  * Windows used to store passwords in an [NTLM hash](https://www.crowdstrike.com/cybersecurity-101/ntlm-windows-new-technology-lan-manager/), Mimikatz would be used to pass the extracted hash string to the target computer login.
* Pass-the-ticket
  * Newer versions of Windows store password data in construct called a ticket, Mimicatz can be used to pass a [Kerbose ticket](https://en.wikipedia.org/wiki/Kerberos_(protocol)) to another computer login. Similar to the Pass-the-hash.
* Over-Pass the Hash (Pass the Key)
  * Also similar to Pass-the-Hash except this method passes a unique key inorder to impersonate a user you can obtain from a domain controller.
* Kerbose Golden Ticket
  * This is essentially the same as Pass-the-Hash, but for a specific account named `KRBTGT`, which is the account that encrypts all of the other tickets. A golden ticket gives you domain admin creds to any computer on the network
* Kerbose Silver Ticket
  * Again, smimilar to Pass-the-Hash but this methods uses a Windows feature that makes it easier to use services on the network. Kerbose grants a user a TGS Ticket, which can be used to login to said network services. Microsoft does frequently check this ticket after it has been issued, making it exploitable. 
* Pass-the-Cache
  * An attack similar to pass-the-ticket, but using save & encrypted data on *nix systems.

## Usage

*\~Always run Mimikatz as Administrator, even if logged into an Administrator account\~*

### Extracting Clear Text Passowrds From Memory

The module `sekurlsa` in Mimikatz allows you to dump passwords from RAM.

#### Command Steps
1. `mimikatz # privilege::debug` - This command checks to make sure you have the required permissions.
2. `mimikatz # log name_log_file.log` - This command is used create a log of what you do, so you can save your work.
3. `mimikatz # sekurlsa::logonpasswords` - This command will output all of the clear text passowrds on the host system. 
