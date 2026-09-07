Personal technical reference notes from my study of **Microsoft Entra ID**.

These notes are intended to function as a quick-reference guide to help reinforce concepts and provide location reminders of where key features and settings can be found in the Entra admin center.

They cover fundamental concepts including users, groups, identity, authentication, authorisation, security and device management.

> **Note:** These are personal learning notes and are not intended to replace Microsoft's official documentation.


**What is Entra ID?**
Cloud-based identity and access management service for M365 and Azure
No OUs, GPOs, no domains or sites - Just users, groups and devices 
Administrative Units comparable to OUs for delegated administration

![[Pasted image 20260907112153.png]]
**New user** - create/invite user - Enter user principle name (typically email) + Display name
	Properties:
		- Identity (F.name/surname, user type, Authorisation info)
		- Job Information (title, company name, dept, employment ID, office location, etc)
		- Contact Info..
	HR integration systems often populate these fields.

Assignments
	Add administrative Unit/ Add group/ Add role (eg, Global Administrator)
	After selecting the new user, you can assign licences, such as Office E5, which will give the user access to a number of MS features and apps. These can be granularly checked/unchecked.
		 ![[Screenshot 2026-09-07 at 09.52.42.png|492]]
	To delete a user, select the user account by checking the box and clicking delete at the top. The account can be backed up) 
	Deleted users can generally be restored within 30 days

**New Group**
	Group type: 
		***Microsoft 365 (Fully collaborative group)***
			Group name, email and description
			Here an administrative role can be assigned to the group, as with a single user
			Sensitivity label (eg, top secret)
			Select owner/s who can manage members
		***Security group (for permissions)*
			Membership Type:
			- Assigned: Manually choose users to be added to groups.
			- Dynamic User: Choose a property of the user account to add, eg, country/ jobtitle/ department and link it to a value with a selected operator (City = Cape Town), then all users for whom the rule is true will automatically be added to the group. (dynamic membership)
			![[Pasted image 20260907111742.png]]
			- Dynamic Device: Automatically grouping devices based on device properties, with Intune then able to target those groups.

**Securing Users**
	Identity - Overview, properties tab. Scroll down to Security Defaults
		Basic security mechanisms in place by Microsoft
		NB: Security Defaults and Conditional Access policies are different approaches; enabling Security Defaults can conflict with an existing Conditional Access/security configuration
		For new tenants with no existing security configurations, it's good to enable.

**Authentication and Authorisation**
	In EntraID Admin Center, select Protection tab - Authentication methods (List of approved methods, via which, users can authenticate), eg. Passkeys, email & SMS OTP, token, Microsoft Authenticator and certification-based authentication (User requires certificate on device).
	![[Screenshot 2026-09-07 at 11.47.17.png]]
		Microsoft Authenticator - Users can download on their device. Deploy to selected groups or all users.
		Within the Configuration tab, application name and location can be pushed in order to be visible.
		![[Screenshot 2026-09-07 at 11.47.17.png]]
		![[Screenshot 2026-09-07 at 11.44.21.png]]

**Entra Verifiable Credentials**
	Decentralised ID (DID) using a third party for verification
	In the Entra ID Center, select Verifiable credentials on the left-hand drop-down and select setup. Setup process include:
		Define organisation settings
		Register decentralised ID
		Verify domain ownership
	Useful for verifying employee credentials and other information
		Eg. accessing a history of monetary transactions - who and where it occurred
	![[Screenshot 2026-09-07 at 12.48.00.png]]

