## Automate Blocking Domains in Cisco Umbrella with Tines
For Security Operations, IOC management is a challenge.  

How does one team with limited time and resources track Indicators of Compromise (IOCs) in all their security solutions and lifecycle them appropriately?  

Tines makes this challenge much easier through their SOAR automation platform.

This past month, we launched a Tines webform, where a security analyst can add IOCs to all our backend security solutions.  In addtion, a ServiceNow incident is logged, along with sharing the IOCs with our partner institutions via [MISP](https://github.com/MISP/MISP), the open-source threat intel sharing platform.

With the IOC blocking webform project, I worked with the Cisco Umbrella API for the first time. 
## A Cisco Umbrella Desitnation 

Cisco Umbrella defines a destination as a :
1. domain, 
2. URL, 
3. or IP address.   

## API Scope
For adding an IOC to the global blocklist, the API key pair needs to have read/write access to Policies/Destination Lists.

## Cannot query the Cisco Umbrella ID

It is straightforward to add a destination to Umbrella, but to remove the IOC is a challenge since there is no way query the Umbrella destinations endpoint for the destination's Umbrella ID.

In order to remove a destination, the workflow needs to build the entire list of Umbrella IDs that are in the block list.  From that array, you can use the following WHERE function to obtain the Umbrella ID:

<img src="./images/WHERE_Function_Umbrella_ID.png">

Under the [tines](story) folder, I include the pagination loop for building the array in order to obtain the destination's Umbrella ID.

In addition, I have a workflow which manages the entire lifecycle of the blocked destination.  The workflow sunsets the blocked destination after 90 days, which can be changed.

Once you start automating, you cannot stop.

Happy Building!

Tom

## Tines Technical Resources
- [FREE Tines Community Edition](https://www.tines.com/pricing/)
- [Tines Documentation](https://www.tines.com/docs/quickstart/)
- [Tines Tutorials](https://www.tines.com/customer-center/#tutorials)
- [Tines Customer Center](https://www.tines.com/customer-center/)
- [Tines University](https://www.tines.com/university/)
- [Tines & AI](https://www.tines.com/product/ai/)
- [Tines WHERE Function](https://www.tines.com/docs/formulas/functions/where/)

## Cisco Technical Resources
- [Cisco Umbrella Sign Up](https://signup.umbrella.com/)
- [Cisco Umbrella API Docs](https://developer.cisco.com/docs/cloud-security/getting-started/)