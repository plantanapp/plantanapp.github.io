---
id: grant-revoke-user-role
title: Grant/Revoke User Role
sidebar_label: Grant/Revoke User Role
---

> Audience: [`Business Users`](/docs/audience#business-users)<br/>
> Skill Prerequisites: `Permission Scheme`

## `Typical Use Cases`

- Assign roles to new users on registration
- Give access to resources for specific users
- Temporary give access to users

## `Don't use it to`

- Prevent users from accessing the system at all. Instead, mark users as deleted or unauthorize them (for Revoke User Role)

## `Related Actions`

| Action Name                                             | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------------ |
| [Load Users](/docs/Actions/load-user.md)                | Can be used to grant roles to a single user or to a list of users. |
| [User Registration](/docs/Actions/user-registration.md) | Can be used to grant roles to a newly created user.                |

## `Input Parameter Reference`

| Parameter        | Description                                                                                    | Supports Variables |
| ---------------- | ---------------------------------------------------------------------------------------------- | ------------------ |
| Role             | Select the security role, from existing roles, to grant/revoke.                                | Yes                |
| Other Role Names | Freely input the role name(s) you want to grant/revoke. Multiple roles are separated by comma. | Yes                |
| Role Validity    | Set a validity period to the granted role.                                                     | No                 |

## `Examples`

### `1. Grant a User Role`

The action below register a new user and grants it the '[Citizen Developers]' Role. [Import it](/docs/Actions/Import-actions) into your application to see it in action.

```json
{
    "Title": "Execute Actions",
    "ActionType": "ExecuteActions",
    "Description": "grant Citizen Developers Role to testuser",
    "Condition": null,
    "Parameters": {
        "ActionList": [
            {
                "Id": -1,
                "$_uid": "action15918664760486108",
                "Parameters": {
                    "UsernameField": {
                        "Expression": "testuser",
                        "Value": "",
                        "IsExpression": true
                    },
                    "RegisterWithEmail": "",
                    "PasswordField": {
                        "Expression": "testpassword",
                        "Value": "",
                        "IsExpression": true
                    },
                    "RandomPass": "",
                    "EmailField": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "FirstName": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "LastName": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "SendDnnMail": "",
                    "LoginIfExists": "",
                    "Authorization": {
                        "Expression": "",
                        "Value": "Authorize",
                        "IsExpression": false,
                        "Parameters": {}
                    }
                },
                "ActionType": "UserManagement_UserRegistration",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "User Management"
                    }
                }
            },
            {
                "Id": -1,
                "$_uid": "action15918664760483872",
                "Parameters": {
                    "RoleId": {
                        "Expression": "",
                        "Value": "6",
                        "IsExpression": false,
                        "Parameters": {}
                    },
                    "RoleNames": "",
                    "DateSelectionMode": {
                        "Expression": "",
                        "IsExpression": false,
                        "Parameters": {}
                    },
                    "ExtensionDays": "",
                    "StartDate": {
                        "Date": ""
                    },
                    "StartDateToken": "",
                    "ExpireDate": {
                        "Date": ""
                    },
                    "ExpireDateToken": "",
                    "RoleExpiration": ""
                },
                "ActionType": "GrantUserRole",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "User"
                    }
                }
            }
        ]
    }
}
```

### `2. Grant a User Role for a period of time`

The action below register a new user and grants it the '[Citizen Developers]' Role just for 30 days. [Import it](/docs/Actions/Import-actions) into your application to see it in action.

```json
{
    "Title": "Execute Actions",
    "ActionType": "ExecuteActions",
    "Description": "grant Citizen Developers Role for 30 days to testuser",
    "Condition": null,
    "Parameters": {
        "ActionList": [
            {
                "Id": -1,
                "$_uid": "action15918671753468384",
                "Parameters": {
                    "UsernameField": {
                        "Expression": "testuser",
                        "Value": "",
                        "IsExpression": true
                    },
                    "RegisterWithEmail": "",
                    "PasswordField": {
                        "Expression": "testpassword",
                        "Value": "",
                        "IsExpression": true
                    },
                    "RandomPass": "",
                    "EmailField": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "FirstName": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "LastName": {
                        "Expression": "",
                        "Value": "",
                        "IsExpression": false
                    },
                    "SendDnnMail": "",
                    "LoginIfExists": "",
                    "Authorization": {
                        "Expression": "",
                        "Value": "Authorize",
                        "IsExpression": false,
                        "Parameters": {}
                    }
                },
                "ActionType": "UserManagement_UserRegistration",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "User Management"
                    }
                }
            },
            {
                "Id": -1,
                "$_uid": "action15918671753464006",
                "Parameters": {
                    "RoleId": {
                        "Expression": "",
                        "Value": "6",
                        "IsExpression": false,
                        "Parameters": {}
                    },
                    "RoleNames": "",
                    "DateSelectionMode": {
                        "Expression": "",
                        "IsExpression": false,
                        "Parameters": {},
                        "Value": "DateWithOffset"
                    },
                    "ExtensionDays": "",
                    "StartDate": {
                        "Date": ""
                    },
                    "StartDateToken": "",
                    "ExpireDate": {
                        "Date": ""
                    },
                    "ExpireDateToken": "",
                    "RoleExpiration": "30"
                },
                "ActionType": "GrantUserRole",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "User"
                    }
                }
            }
        ]
    }
}
```

### `3. Revoke a User Role `

The action below loads current user using [Load User](/docs/Actions/load-user) action and revokes its '[Citizen Developers]' role. [Import it](/docs/Actions/Import-actions) into your application to see it in action.

```json
{
    "Title": "Execute Actions",
    "ActionType": "ExecuteActions",
    "Description": "revoke current Citizen Developers user Role",
    "Condition": null,
    "Parameters": {
        "ActionList": [
            {
                "Id": -1,
                "$_uid": "action1591868419626850",
                "Parameters": {
                    "Id": "[User:UserId]",
                    "Portal": ""
                },
                "ActionType": "LoadUser",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "Context"
                    }
                }
            },
            {
                "Id": -1,
                "$_uid": "action15918684196265931",
                "Parameters": {
                    "RoleId": {
                        "Expression": "",
                        "Value": "6",
                        "IsExpression": false,
                        "Parameters": {}
                    },
                    "RoleNames": ""
                },
                "ActionType": "RevokeUserRole",
                "$_isOpen": false,
                "$_isLoaded": true,
                "$_isFocus": true,
                "Definition": {
                    "IsClientAction": false,
                    "Settings": {
                        "Group": "User"
                    }
                }
            }
        ]
    }
}
```

## `Frequently asked questions`

**What happens when granting a role that the user already has?**

If a role is granted again without any validity period nothing will happen. 

**What happens when grating a role that the user already has, but with a different expiration date?**

If the validity period is set, the old one will reset. For example if a user has only 20 days left, if a 30 days validity period is granted, it will have again 30 days left.

**What about revoking a role that the user doesn't have?**

Nothing will happen if a not assigned role is revoked.

**What happens if the Role is deleted?**

The role will simply be revoked from any user that has it.