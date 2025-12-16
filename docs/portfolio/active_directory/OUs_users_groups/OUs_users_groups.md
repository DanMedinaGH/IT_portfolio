# Organizational Units, Users, & Groups Creation
![Active Directory Banner](../assets/images/active_directory_banner.png)
In this project we will create **organizational units (OUs)** for our domain. We will also create users and groups for our OUs.

## Operating Systems
- Windows 11 (x86-64)
- Windows Server 2022 (x86-64)

## Environments and Technologies Used
- VMware Workstation Pro for Personal Use (Windows)

## OUs, Users, and Groups Creation
### OUs
An **OU** is a container in AD that allows us to organize computers, users, groups, and other objects. It allows adminstrators to logically structure resources in a domain.

#### Setup
To add an OU we select:

```
Windows Key > Windows Administrative Tools > Active Directory Users and Computers
```

This brings the following menu: <br/><br/>
![AD Users and Computers](./assets/images/ad_users_and_computers.png)

As we can see, our domain **DanielIT.local** already has pre-built OUs.

We will then create OUs for the different country departments in our domain:

``` 
Right-click Root Domain > New > Organizational Unit
```

Here, we write a name and select **OK** to create the OU.

![New OU](./assets/images/new_OU.png)

We'll create OUs for each geopgraphical location and each resource type:

![New OU](./assets/images/OUs.png)

### Groups

When that is complete, we'll configure **groups, group scopes, and group types** for our OUs.<br/><br/>

**Groups** are containers are used to control **permissions on resources** and **simplify managment**.

- Instead of assigning permissions to individuals, we assign users to groups.

**Group Scope** defines where a group can be used and who can be a member of it in an AD forest or domain. There are 3 group scopes:

1. Domain Local
    - Purpose: Assign permissions to resources within **a single domain**.
    - Constraints:
        - Members can come from ***any* domain in the same forest or trusted forest**.
        - Permissions assigned to resources in a ***single* domain**.
    - Typical scenario: "Who can access this file server?"
        - Example: ```DL_Fileserver_read```

2. Global
    - Purpose: Group users with the same job role.
    - Constraints:
        - Members come from ***a single* domain**.
        - Permissions assigned to resources in a ***any* domain in a forest or trusting forest**.
    - Typical scenario: "Who are the Help Desk staff?"
        - Example: ```GG_HelpDesk```

3. Universal
    - Purpose: Groups users across multiple domains in the same forest with the same job role.
    - Scope of use: ***Entire* forest**
    - Constraints:
        - Members can come from ***any* domain in the same forest**.
        - Permissions assigned to resources in a ***any* domain in a forest or trusting forest**.
    - Typical scenario: "Users from multiple domains need the same access."
        - Example: ```UG_All_IT_Staff```

**Group type** defines the purpose of the group - whether it's used for **security** or **distribution**:

- Security group
    - Purpose: **Assigns permissions to resources** like files, folders, printer, other groups, etc.
    - Example: Security group ```HR_ReadOnly``` gives access to HR file share.
- Distribution group (Distro List)
    - Purpose: Create **email distributions** for sending emails to a list of users.
    - Example: Distribution group ```AllEmployees``` is used for sending company-wide emails.

#### Setup
```Right-click OU > New > Group```

![New Group](./assets/images/new_group.png)

After clicking OK a new group will be added to the OU.

### Users
**Users** represent individuals in a domain that can **access resources**.

#### Setup
```Right-click OU > New > User```

![New User](./assets/images/new_user.png)

We then fill out their credentials information to complete their creation.