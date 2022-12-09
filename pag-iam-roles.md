---

copyright:
  years: 2022
lastupdated: "2022-12-07"

keywords: PAG roles, IAM role, service roles, set permissions, platform roles, IAM resource attributes, reader, viewer, administrator, SSH user, Kubernetes user, operator, editor, Kubernetes, IAM, roles, permissions, SSH, virtual server, CA certificate, privileged access gateway, PAG

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Access management and roles
{: #pag-roles}

You can use the standard {{site.data.keyword.iamlong}} (IAM) UI in the cloud console to create IAM policies for {{site.data.keyword.pag_full}} and assign to one or more roles that are described below. Then, you can assign the created policies to IAM user access groups​ [IAM role](/docs/cloud-object-storage?topic=cloud-object-storage-iam).

## Set permissions
{: #pag-roles-permissions}

1. Create IAM user access group.
2. Create a {{site.data.keyword.pag_short}} IAM policy for the access groups.
3. Either specify all {{site.data.keyword.pag_short}} resources for the policy, or set more fine-grained access control by using IAM attributes.
4. Assign {{site.data.keyword.pag_short}} IAM roles to the policy.

## Service roles
{: #pag-roles-service-roles}

- `Reader`, can get the CA key needed to set up Virtual Servers for the {{site.data.keyword.pag_short}}.
- `Writer`, same permission as Reader role with the added ability to create SSH and Kubernetes sessions through the {{site.data.keyword.pag_short}}.
- `Manager`, can list all active sessions​.


## Platform roles
{: #pag-roles-platform-roles}

- `Viewer`, able to list {{site.data.keyword.pag_short}} instances.
- `Operator`, adds the ability to view the dashboard for {{site.data.keyword.pag_short}} instances​.
- `Editor`, adds the ability to create {{site.data.keyword.pag_short}} instances.
- `Administrator`, adds the ability to set permissions on {{site.data.keyword.pag_short}} instances.


​
