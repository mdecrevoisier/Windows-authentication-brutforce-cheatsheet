# Windows-authentication-brutforce-cheatsheet

## Project purpose
**Windows authentication cheat sheet** provides key elements to assist threat hunters, SOC and forensic analysts during logs investigation tasks or threat detection conception.

It covers the following indicators:
Authentication type | Outcome | Event IDs
|:-------------|:--------|:--------|
Login | Success | 4624
Login | Failure | 4625
Kerberos request | Success | 4768
Kerberos request | Failure | 4768, 4771
Explicit credentials | Both | 4648

## Windows source information (ID 4624 & ID 4625)
These event IDs are generated on the host where an authentication action is performed. However, one of the most painful point when dealing with these events is the inconsistency of the data they provide. More precisely, two fields requires our attention:
* *Workstation*: usually contains the Hostname of the source performing the authentication
* *IpAddress*: usually contains the IP address of host performing the authentication

Based on my personal experience while working with business customers, I have encountered multiple situations where the content of these fields:
* is not the one we expect or is announced by Microsoft documentation
* drive to misleading information about the source host
* contains invalid information
* is empty
* contains randomly generated data
* requires data manipulation to correctly parse and normalize source information

For these reasons, I am providing at the following a schema which summarizes all these "unexpected behaviors" to limit or understand their impact during logs exploitation.
![](/source_info-ID4624-2625/source_information_4624-2625_schema.png)

## Windows brutforce (ID 4625 & ID 4776)
The following mindmap provides an overview of the different elements that may help to design, identify or assess a potential brutforce.
![](/brutforce-mindmap/windows-brutforce-mindmap.png)