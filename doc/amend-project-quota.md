# Amend Project Quota

* [Back to index](../README.md)

## Description

## Behaviour

**Feature:** Amend Project Quota

>As a service user
>I want to amend the quota of a project
>So I can have the correct amount of resources for development project

**Scenario:** Change OCP project quota

* **Given** the name of the application is known.
* **Given** the name of cluster is specified
* **Given** the name of the environment to amend is specified.
* **Given** the new T-Shirt size for resource quotas is specified
* **When** the Amend Quota is requested
* **Then** the specified OCP project is changed to the new T-Shirt size quota.

## Variables

| Variable        | Description                                                                                                     | Example                  |
| --------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------ |
| **ocp_uri**     | The URI of the OCP master server associated with the desired cluster, including port.                           | https://127.0.0.1:8443   |
| **ocp_token**   | The token used to authenticate with the OCP server. It should be for a service account with cluster-admin role. | "account-token-89si3"    |
| **tenant_name** | The name of the tenant to be created. This name is used to name the projects in a CD the pipeline.              | MyApp                    |
| **project**     | The name of the OCP project to be altered                                                                       | See example below        |
| **cluster**     | The cluster ID of the OCP. This would be either prod or nonprod                                                 | prod                     |

| **qutoa**       | The size of the of new desire quota         | large, medium, and small |

## Example Meta-data Structure

```yaml
ocp_uri: 'https://127.0.0.1:8443'
ocp_token: ''
cluster: 'nonprod'
tenant_name: 'Tenant_A'
project:
  - name: 'DEV'
  - quota: 'large'
```
