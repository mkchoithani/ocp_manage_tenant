# Create Tenant Space

* [Back to index](../README.md)

## Description

## Behaviour

**Feature:** Create Tenant

>As a service user
>I want to allocate a tenant space on the HCP
>So that I can progress with development for my business project

**Scenario:** Create new tenant space in OCP

* **Given** the name of the application is known.
* **Given** OCP users exists in the Identity Management Server (LDAP).
* **Given** the name of cluster is specified
* **Given** the name of one or more environments is specified.
* **Given** a T-Shirt size for resource quotas used by all environments in the tenant is selected.
* **Given** one or more administrators for each environment (project) in the pipeline are known.
* **Given** one or more basic users for each environment (project) in the pipeline are known.
* **When** the tenant creation is requested.
* **Then** a number of OCP projects are created with a common base name and a different environment suffix with the given T-Shirt size quota.
* **Then** a group for each project / user role is created in the Identity Management Server (LDAP).
* **Then** relevant users are added to the required roles.

## Variables

| Variable        | Description                                                                                                     | Example                  |
| --------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------ |
| **ocp_uri**     | The URI of the OCP master server associated with the desired cluster, including port.                           | https://127.0.0.1:8443   |
| **ocp_token**   | The token used to authenticate with the OCP server. It should be for a service account with cluster-admin role. | "account-token-89si3"    |
| **tenant_name** | The name of the tenant to be created. This name is used to name the projects in a CD the pipeline.              | MyApp                    |
| **projects**    | A list of projects (environments) making up the Tenant.                                                         | See example below        |
| **cluster**     | The cluster ID of the OCP. This would be either prod or nonprod                                                 | production               |
| project.name    | Name of the environment / OCP project                                                                           | e.g. dev, test           |
| project.admins  | List of administrator user name for the OCP project. The user names need to already exist in IDAM.              | e.g. admin      |
| project.users   | List of basic user names for the OCP project. The user names need to already exist in IDAM.                     | e.g. dev1       |
| **qutoa**       | The size of the tenancy. This specifies the maximum number of runtime containers for each environment           | large, medium, and small |

## Example Meta-data Structure

```yaml
ocp_uri: 'https://127.0.0.1:8443'
ocp_token: ''
idm_uri: ''
cluster: 'nonprod'
tenant_name: 'Tenant_A'
projects:
  - name: 'DEV'
    admins:
      - 'devAdmin'
    users:
      - 'dev1'
      - 'dev2'
  - name: 'TEST'
    admins:
      - 'testAdmin'
    users:
      - 'tester1'
      - 'tester2'
  - name: 'DEMO'
    admins:
      - 'demoAdmin'
    users:
      - 'demo1'
      - 'demo2'
```
