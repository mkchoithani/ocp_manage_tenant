# Remove Users From Project

* [Back to index](../README.md)

## Description

This task remove one or more users from the IDAM group assoicated with a given OCP project.

Within the context of a tenancy, the project will correspond to the flatten project name of [tenant_name]-[environment_name] (e.g sometenant-test where sometenant is the name of the tenancy and test is the name of the environment).

## Behaviour

**Feature:** Remove user from project

As a service user - tenant owner
I want to be able remove users who are no longer part of my team from access to environments in my tenant
So that I can ensjure only the correct people have access to my tenant space

* **Given** the name of the OCP project is available
* **Given** One or more OCP user names is specified
* **Given** The users exists in the Identity Management Server within the specified group
* **When** remove users is requested.
* **Then** the given users are removed from the specified group on the IDAM server

### Variables

| Variable        | Description                                                                                                     | Example                |
| --------------- | --------------------------------------------------------------------------------------------------------------- | ---------------------- |
| **ocp_uri**     | The URI of the OCP master server associated with the desired cluster, including port.                           | https://127.0.0.1:8443 |
| **ocp_token**   | The token used to authenticate with the OCP server. It should be for a service account with cluster-admin role. | "account-token-89si3"  |
| **tenant_name** | The name of the tenant to be created. This name is used to name the projects in a CD the pipeline.              | MyApp                  |
| project.name    | Name of the environment / OCP project                                                                           | dev, test              |
| project.admins  | List of admin user name to be removed.                                                                          | devAdmin               |
| project.users   | List of user names to be removed.                                                                               | dev1                   |

```yaml
ocp_uri: 'https://127.0.0.1:8443'
ocp_token: ''
idm_uri: ''
tenant_name: 'Tenant-A'
projects:
  * name: 'DEV'
    admins:
      * devAdmin
    users:
      * dev1
      * dev2
  * name: 'TEST'
      admins:
        * testAdmin
      users:
        * tester1
        * tester2
  * name: 'DEMO'
      admins:
        * demoAdmin
      users:
        * demo1
        * demo2
```