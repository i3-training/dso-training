# Nexus Repository OSS Administration

Access your Nexus Repository web dashboard
![](/Chapter-3-Nexus/img/login-nexus-1.png)

Enter your username & password
![](/Chapter-3-Nexus/img/login-nexus-2.png)

You have successfully logged in
![](/Chapter-3-Nexus/img/login-nexus-3.png)

## Manage Roles

In the Nexus Repository, a role is a set of permissions that determine what actions a user can perform within the repository. Roles are used to control access to the repository and the functions that users can perform within the repository. For example, a user with the Deployment role might be able to upload components to the repository, while a user with the Developer role might only be able to view and download components.

The Nexus Repository includes a set of predefined roles, but custom roles can also be created to meet the specific needs of an organization. The roles and permissions in Nexus Repository can be managed through the Nexus Repository web interface, allowing administrators to control access to the repository and the functions that users can perform.

Assigning roles to users helps to ensure that only authorized users have access to the repository and can perform specific actions within the repository, providing security and control over the components and dependencies stored in the repository.

### Create a Roles
To create new role you need to login as administrative privileged account, then go to administration (settings icon), on security go to Roles then select create role, on Role Type select `Nexus Role` then fill all required form. administrator can select Privileges and Roles that already exist to customize new role being created.

Click Create Role 
![](/Chapter-3-Nexus/img/roles-1.png)

Enter some of the required information
![](/Chapter-3-Nexus/img/roles-2.png)

You can add privilleges to a roles you create
![](/Chapter-3-Nexus/img/roles-3.png)

![](/Chapter-3-Nexus/img/roles-4.png)

You can also assign existing roles to the roles you want to create
![](/Chapter-3-Nexus/img/roles-5.png)

Click Save
![](/Chapter-3-Nexus/img/roles-6.png)

You have successfuly create a new roles
![](/Chapter-3-Nexus/img/roles-7.png)


### Edit Role

You cant edit existing role provided by nexus, but you can edit user defined role, To edit a role in the Nexus Repository, follow these steps:

1. Log in to the Nexus Repository web interface as an administrator.
2. Click on the "Security" menu item on the left-hand side of the screen.
3. Click on the "Roles" tab.
    ![](/Chapter-3-Nexus/img/roles-7.png)
4. Find the role you want to edit in the list of roles and click on its name.
5. On the Role Details page, you can edit the name and description of the role and administrator also can edit the permissions associated with the role.
6. Once you have made the desired changes, click on the "Save" button to save the changes to the role.

Note that changes to roles can affect multiple users, so be careful when editing roles to ensure that the changes you make are appropriate for the needs of your organization.

It's also worth mentioning that changes to roles can take some time to take effect, as they may need to be propagated to all users who have been assigned the role.


## Manage Users

Manage user can be done on administration then on security section select Users.

![Nexus User](/Chapter-3-Nexus/img/users-1.png)

### Crete New User

Create user on nexus can be done on administration then on security section select user and Create local user. fill all required form and on Roles section, admin can give new user roles based on roles created on previous section.

![Nexus User](/Chapter-3-Nexus/img/users-2.png)

Enter some of the required information. <br>
You can assign roles to the user you are creating
![Nexus User](/Chapter-3-Nexus/img/users-3.png)

Click Create local user
![Nexus User](/Chapter-3-Nexus/img/users-4.png)

You have succesfully create a new user
![Nexus User](/Chapter-3-Nexus/img/users-5.png)



### Edit User

Editing user work the same as Create new user, admin can select user to edit and will be directed to user edit form, other than edit user details, admin can change user password and delete user account.

![Nexus User](/Chapter-3-Nexus/img/users-6.png)

## Manage Blob

### Create new Blob storage

Before create a new repository its a good idea to create a new blob storage to separate data between repository, in this case we will create a new blob storage to store our images, to create a new blob storage follow steps below.

Login to your nexus web console then open server administration and configuration, on the side bar click Blob stores then select Create Blob Store to create new blob storage, first select type as an file since we will using local storage, then give your blob a name and specify your blob location, you can also create Quota for your blob here after that save the change and new blob storage is created and ready to be use by an repository.

![Nexus User](/Chapter-3-Nexus/img/blob-1.png)

Enter some of the required information. <br>
Click Save
![Nexus User](/Chapter-3-Nexus/img/blob-2.png)

![Nexus User](/Chapter-3-Nexus/img/blob-3.png)

You have successfuly create a new Blob Stores
![Nexus User](/Chapter-3-Nexus/img/blob-4.png)


