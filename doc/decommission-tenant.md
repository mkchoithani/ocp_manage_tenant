# Decommission Tenant Space

* [Back to index](../README.md)

## Description

This task removes all the OCP projects associated with a particular the tenant space within a specific cluster such as production and non-production.

## Behaviour

This is the reverse of create tenant and removes all artefacts associated with a particular tenant in particular cluster.  For example, removes tenant space from non-prod but not the prod cluster.

:pencil: *NOTE* CMDB update not required for R1

**Feature:** Decommission Tenant

As a tenant owner service user 
I want to decommission a tenant after the end of a business project
So that I do not incur any unnecessary cost

**Scenario** Remove OCP projects for tenants 

* **Given** the name of the tenant is known.
* **Given** the url of the OCP cluster is known
* **When** the tenant decommission is requested
* **Then** all projects associated with the tenant are removed from the cluster
* **Then** all groups that are associated with the tenant are removed from IDAM 
* **Then** all artefacts for each associated with the tenant are removed from **CMDB**.

## Variables

| Variable        | Description                                                                                                     | Example                             |
| --------------- | --------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| **ocp_uri**     | The URI of the OCP master server associated with the desired cluster, including port.                           | https://127.0.0.1:8443              |
| **ocp_token**   | The token used to authenticate with the OCP server. It should be for a service account with cluster-admin role. | "account-token-89si3"               |
| **tenant_name** | The name of the tenant to be created. This name is used to name the projects in a CD the pipeline.              | MyApp                               |

## Example Metadata Structure

```yaml
ocp_uri: 'https://127.0.0.1:8443'
ocp_token: ''
idm_uri: ''
idm_token: ''
tenant_name: 'Tenant_A'
