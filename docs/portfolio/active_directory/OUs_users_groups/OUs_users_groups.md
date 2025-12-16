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

To add an OU we select:

```
Windows Key > Windows Administrative Tools > Active Directory Users and Computers
```

This brings the following menu: <br/><br/>
![AD Users and Computers](./assets/images/ad_users_and_computers.png)

The folders under our root domain **DanielIT.local** are pre-built OUs.

We will then create OUs for the different country departments in our domain:

``` 
Right-click Root Domain > New > Organizational Unit
```

Here, we write a name and select **OK** to create the OU.

![New OU](./assets/images/new_OU.png)

We'll create OUs for each geopgraphical location and each resource type:

![New OU](./assets/images/OUs.png)
