---

copyright:
  years: 2022
lastupdated: "2022-9-12"

keywords: PAG roles, IAM role, custom roles, set permissions, platform roles, IAM resource attributes, viewer, administrator, SSH user, Kubernetes user, operator, editor, Kubernetes, IAM, roles, permissions, SSH, virtual server, CA certificate, privileged access gateway, PAG

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# PAG access management and roles
{: #pag-roles}

You can use the standard {{site.data.keyword.iamlong}} (IAM) UI in the cloud console to create IAM policies for {{site.data.keyword.pag_full}} (PAG) and assign to one or more roles that are described below. Then, you can assign the created policies to IAM user access groups​ [IAM role](/docs/cloud-object-storage?topic=cloud-object-storage-iam).

## Set permissions
{: #pag-roles-permissions}

1. Create IAM user access group.
2. Create a PAG IAM policy for the access groups.
3. Either specify all PAG resources for the policy, or set more fine grained PAG access control by using the PAG IAM attributes.
4. Assign PAG IAM roles to the policy.

## Custom roles
{: #pag-roles-custom-roles}

- `Gateway viewer`, can list active sessions, as well as get the CA certificate needed to set up Virtual Servers for PAG.
- `Gateway administrator`, can list and terminate active sessions​.
- `SSH user`, can initiate SSH sessions.
- `Kubernetes user`, can initiate the {{site.data.keyword.containershort}} through PAG.

## Platform roles
{: #pag-roles-platform-roles}

- `Viewer`, able to list PAG instances.
- `Operator`, adds the ability to view the PAG dashboard for PAG instances​.
- `Editor`, adds the ability to create PAG instances.
- `Administrator`, adds the ability to set permissions on PAG instances.


​
