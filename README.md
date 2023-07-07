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

2. Creating Sub-OUs for the departments:
   - Right-click on the Montreal OU and select "New" -> "Organizational Unit".
   - Create sub-OUs based for each department.
     ![image](https://github.com/gf500/AD-OUs-Users-PCs/assets/121585575/8a18a177-a593-4c93-9360-b4aa1c7b73a6)

