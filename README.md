# Active Directory: OUs, Users and PCs

For this part of our project, we will focus on user management and Group Policies. These steps will pave the way for us to effectively manage user accounts, delegate rights, join PCs to the domain, and utilize Group Policy Objects (GPOs) to enforce consistent settings across our domain.

## Organizational Units

We will start by creating OUs, so we may establish a logical structure within our Active Directory that reflects our organization's departments and hierarchy. This allows for more efficient management of user accounts, delegation of administrative tasks, and application of Group Policies.

We will first create the Montreal OU for our main office then create Sub-OUs for our departments: Finance, HR, IT and R&D.

1. Creating the Montreal office OU:
   - In Server Manager under Tools: open Active Directory Users and Computers.
   - Right-click on the domain name "acme.com" and select "New" -> "Organizational Unit".
   - Enter "Montreal" as the name for the OU and click "OK" to create it.
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/1d275b3c-2e39-4ded-bc13-a6b47334a296)

2. Creating Sub-OUs for Montreal:
   - Right-click on the Montreal OU and select "New" -> "Organizational Unit".
   - Create sub-OUs based on our OU structure:
      - Montreal
         - Admins
         - Devices
            - Servers
            - Workstations
         - Employees
            - Finance
            - Human Resources
            - Development
            - IT
            - Sales
         - Service Accounts

![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/134cccc8-3e6a-4dd0-9c1f-15a4fe0ceda7)


## Creating Users

We will create some user accounts to populate the OUs, we will keep it simple for now just to have some users in our departements, a couple of admins account and a service account to join workstations to our domain.

1. Creating Users
   - Still in the Active Directory Users and Computers management console, locate the Organizational Unit (OU) corresponding to the department you want to create a user account for.
   - Right-click on the OU, select "New," and choose "User."
2. Naming Users
   - For employee users's logon we will use their first letter of their first name followed by their last name.
   - We will capitalize their last name to make the distinction.

![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/9852626c-1256-4f86-bd97-9433a35da84e)


3. Admins and Service Accounts
   - We will also create a user account for a domain admin and a workstation account, adding the "da" and "wa" prefix to the logon names to distinguish their roles.
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/1bd8e53a-abef-4e19-b22a-d8fbf8281c8c)

   - We also created in the Service Accounts OU a PC joiner user we will be using to join workstations to the domain with a descriptive name: srvc-pcjoin.
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/49bab1c9-e4ed-4f9b-a9f4-e29cc4f12954)

Currently, all our departments have at least one user and we also have some accounts to administering our domain, further on we will be using powershell scripts to populate our OUs more extensively.

## Delegating "Join a computer to the domain" Task to User "srvc-pcjoin"

To make it easier to add workstations to our domain we've elected to use a single service account "srvc-pcjoin" and delegating it the "Join a computer to the domain" task. This account will have the necessary permissions to join computers to the domain, which will help us control who can add workstations and keeps things organized. 

1. Delegation of Control Wizard
   - Still in Active Directory Users and Computers, right-click on acme.com and select "Delegate Control".
   - The Delegation of Control Wizard will open. Click "Next" to proceed.
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/7a7121ce-76ff-4c5d-bc10-96f5eb93ddd1)

   - On the Users or Groups page, click "Add" to select the user "srvc-pcjoin" from the directory.
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/b8dfba29-e7b7-436d-9cd1-84efa184434f)

   - Click "Next" to proceed.
   - On the Tasks to Delegate page, select "Join a computer to the domain" under "Delegate the following common tasks" and click "Next."
     
![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/de3faa52-b533-4f15-85f8-8f5ff43eb413)

   - Review the settings on the Summary page and click "Finish" to complete the delegation process.










