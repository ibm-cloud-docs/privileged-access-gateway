---

copyright:
  years: 2022
lastupdated: "2022-09-09"

keywords: PAG features, release, main features, roles, provisioning, Kubernetes, IAM

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# What's in this release?
{: #pag-features}

This release of {{site.data.keyword.pag_full}} (PAG) includes the following main features:

- Offers service provisioning for single-zone gateway deployments.
- Creating a PAG instance using the PAG provisioning UI accessible from the catalog.
- Ability to perform Secure Shell (SSH) sessions to a Virtual Server through the PAG Gateway (CLI only).
- Ability to access Kubernetes clusters through the PAG gateway (CLI only).
- Virtual Server SSH and Kubernetes `kubectl` sessions through PAG are recorded and stored in your COS bucket.
- Play back of session recordings using the PAG CLI.
- IAM integration where you can assign users specific [PAG roles](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-roles) that restrict the role to specific PAG functionality.
- Ability to list active sessions in progress on a PAG gateway.
- Host name assigned to PAG gateway (Initial release permits one zone for `us-south`).



