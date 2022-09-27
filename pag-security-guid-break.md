---

copyright:
  years: 2022
lastupdated: "2022-09-02"

keywords: security controls, PAG, break glass

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Defining a Break Glass procedure
{: #pag-security-guidelines-break}

Your organization should create a Break Glass procedure to prepare for any outage that may cause your {{site.data.keyword.pag_full}} (PAG) instance to stop functioning.
 
Things to consider in your break glass procedure:
1. Assign an Operator the ability to change the security groups or other firewall / router settings in order to temporarily modify the network policies that enforce traffic coming from the PAG instance.
2. Ensure that {{site.data.keyword.virtualmachinesshort}} have a backup user account created on them that allow authentication by either SSH key or password. By default, a "vpcuser" and "root" user accounts are created on a VSI. SSH keys can be added to these account at the time of the VSI provisioning or manually after.
3. You can allow VNC or Serial console access to users during the outage. This requires setting a password for the Operating System (OS) user prior to the outage. See here for more information: [Accessing virtual server instances by using VNC or serial consoles](https://cloud.ibm.com/docs/vpc?topic=vpc-vsi_is_connecting_console&interface=ui)


