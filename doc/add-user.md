# Add Users to OCP Project / Tenant Environment

* [Back to index](../README.md)

## Description

This task add one or more users from the IDAM group associated with a given OCP project.

Within the context of a tenancy, the project will correspond to the flatten project name of [tenant_name]-[environment_name] (e.g sometenant-test where sometenant is the name of the tenancy and test is the name of the environment).

## Behaviour

**Feature:** Add user from project

As a service user - tenant owner
I want to be able give new member of my team access to environments in my tenant
So that they can progress with development

* **Given** the specified OCP project exists
* **Given** One or more OCP user names and their roles is specified
* **Given** The users exists in the Identity Management Server
* **When** add users is requested.
* **Then** the given users are added to the specified groups on the IDAM server
* **Then** the given users are assign the correct role binding in OCP

### Variables

| Variable        | Description                                                                                                     | Example                             |
| --------------- | --------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| **ocp_uri**     | The URI of the OCP master server associated with the desired cluster, including port.                           | https://127.0.0.1:8443              |
| **ocp_token**   | The token used to authenticate with the OCP server. It should be for a service account with cluster-admin role. | "account-token-89si3"               |
| **tenant_name** | The name of the tenant to be created. This name is used to name the projects in a CD the pipeline.              | MyApp                               |
| **project**     | A list of projects (environments) making up the Tenant.                                                         | See usage section \* create tenant. |
| project.name    | Name of the environment / OCP project                                                                           | e.g. dev, test                      |
| project.admins  | List of admin user name for the OCP project. The user names need to already exist in idam                       | e.g. devAdmin@acme.com              |
| project.users   | List of user names for the OCP project. The user names need to already exist in idam.                           | e.g. dev1n@acme.com                 |

### Example Metadata Structure

```yaml
 ocp_uri: 'https://127.0.0.1:8443'
 ocp_token: ''
 idm_uri: ''
 idm_token: ''
 tenant_name: 'Tenant_A'
 projects:
   * name: 'DEV'
     admins:
       * devAdmin@acme.com
     users:
       * dev1@acme.com
       * dev2@acme.com

```
