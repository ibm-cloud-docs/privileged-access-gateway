---

copyright:
  years: 2022
lastupdated: "2022-12-01"

keywords: PAG requirements, starting, requirements, VPC, setup, SSH key agent, privileged access gateway, PAG, VPC, COS, gateway, SSH, VPN, CLI, SSH, OpenVPN, host name

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Before starting
{: #pag-requirements}

You need an [IBM Cloud™ Platform account](http://cloud.ibm.com/) to get started with {{site.data.keyword.pag_full}}.

Before provisioning your {{site.data.keyword.pag_short}} instance, you need to create the following resources in your PAG account. You need to have these when provisioning {{site.data.keyword.pag_short}} using the UI or CLI.

- **IAM permissions**
   - {{site.data.keyword.pag_short}} admin role
   - Viewer permission for {{site.data.keyword.vpc_full}}s (VPC) in the account (otherwise they will not be able to specify a VPC)
   - Viewer permission for the {{site.data.keyword.cos_full}} (COS) instances in the account (otherwise they will not be able to specify a COS)
- **VPC** - You need to create a VPC to contain the {{site.data.keyword.pag_short}} instance.
- **VPC Subnet** - Required for the gateway host name to be selected. Subnets are created by default with a VPC, but you can create additional subnets as well. You will be asked during {{site.data.keyword.pag_short}} provisioning to provide the CRN of the subnet that you want the {{site.data.keyword.pag_short}} endpoint to reside.

For this release, you must have a public gateway accessible from the subnet that you select. This is needed for {{site.data.keyword.pag_short}} to be able access the IBM IAM service from your gateway for authorization.
{: note}

- **COS instance and bucket** - An [instance of IBM Cloud Object Storage](http://cloud.ibm.com/catalog/services/cloud-object-storage) and bucket must be created to store your {{site.data.keyword.pag_short}} session recordings. You will need to provide the COS instance and bucket name during {{site.data.keyword.pag_short}} provisioning.
- **Run SSH key agent** - You must have the SSH key agent running on your local machine if you want to run a Secure Shell from the CLI.

## VPN setup
{: #pag-requirements-vpn-setup}

You need to setup your {{site.data.keyword.vpn_vpc_short}} so that you can run {{site.data.keyword.pag_short}} CLI commands on your local machine to access the private gateway endpoint that will be created for you when {{site.data.keyword.pag_short}} is provisioned.

Reference this [document](https://test.cloud.ibm.com/docs/vpc?topic=vpc-vpn-overview) for details of how to set this up. You will be creating a VPN type of Client-to-Site, and for the VPC you had setup yourself in the previous section.

As described in the referenced {{site.data.keyword.vpn_vpc_short}} documentation, you will need to setup the OpenVPN client to connect to the VPC by downloading the client profile from the IBM cloud account's VPN as described [here](https://cloud.ibm.com/docs/vpc?topic=vpc-vpn-client-environment-setup).

You need to ensure that any security group connected to the VPN will pass ports 7200 through 7202. These ports are needed by the {{site.data.keyword.pag_short}} CLI.  See [guidelines](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-security-guidelines) for more information.
{: note}

## SSH Key Agent
{: #pag-requirements-ssh-key-agent}

If you want to run a Secure Shell (SSH) using the CLI, you must start the SSH Key Agent on your local machine by executing the following command:

   ```sh
   $ eval ssh-agent
   ```
   For more information, see [ssh.com](https://www.ssh.com/academy/ssh/agent).
