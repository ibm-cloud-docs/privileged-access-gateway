---

copyright:
  years: 2022
lastupdated: "2022-12-09"

keywords: PAG features, release, main features, roles, provisioning, Kubernetes, IAM

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# What's in this release?
{: #pag-features}

This release of {{site.data.keyword.pag_full}} includes the following main features:

- Offers service provisioning for single-zone gateway deployments.
- Creating a {{site.data.keyword.pag_short}} instance using the provisioning UI accessible from the catalog.
- Ability to perform Secure Shell (SSH) sessions to a Virtual Server through the {{site.data.keyword.pag_short}} Gateway (CLI only).
- Ability to access Kubernetes clusters through the {{site.data.keyword.pag_short}} gateway (CLI only).
- Virtual Server SSH and Kubernetes `kubectl` sessions through {{site.data.keyword.pag_short}} are recorded and stored in your COS bucket.
- Play back of session recordings using the {{site.data.keyword.pag_short}} CLI.
- IAM integration where you can assign users specific [roles](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-roles) that restrict the role to specific {{site.data.keyword.pag_short}} functionality.
- Ability to list active sessions in progress on a {{site.data.keyword.pag_short}} gateway.
- Host name assigned to {{site.data.keyword.pag_short}} gateway (Initial release permits one zone for `us-south`).
