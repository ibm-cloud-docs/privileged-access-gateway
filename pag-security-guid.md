---

copyright:
  years: 2022
lastupdated: "2022-12-09"

kaywords: security, best practices, PAG, using security groups, break glass scenarios, network, operators, gateway endpoint, public load balancer

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}
{:caption: .caption}

# Security best practices and guidelines for {{site.data.keyword.pag_full}}
{: #pag-security-guidelines}

To secure your environment with {{site.data.keyword.pag_full}}, you must ensure that operator access to your {{site.data.keyword.virtualmachinesshort}} (VSIs) and Kubernetes (IKS) clusters are only allowed through the PAG instance.  In other words, you want to prevent operators from being able to directly connect and interact with your Cloud resources. This would negate the security features provided by {{site.data.keyword.pag_short}}, including operator session recordings.
 
The following is an example of how to secure your systems with your {{site.data.keyword.pag_short}} instance.
  
 
In this example, the Operator establishes a connection to the VPC network through a VPN connection.  The VPN Gateway is configured to only connect to the {{site.data.keyword.pag_short}} instance.  Downstream Security Groups are configured to only accept connections from the {{site.data.keyword.pag_short}} instance.  This helps enforce connections to your Cloud resources only accepting connections originating from the {{site.data.keyword.pag_short}} instance.


## Configuration examples:
{: #configuration-examples}

### VPN Security Group
{: #vpn-security-example }

| Route | Allow | Value |
|-----------|------|-------|
| Ingress| All | port 443 (udp/tcp) |
| Egress| `{{site.data.keyword.pag_short}} Security Group` | ports 7200-7202 |
{: caption="Table 1. Configuration example for VPN Security Group}

### {{site.data.keyword.pag_short}} Security Group
{: #pag-security-example }

| Route | Allow | Value |
|-----------|------|-------|
| Ingress| `VPN Security Group`  | ports 7200-7202 |
| Egress| `VSI Security Group` | port 22 |
| | `All TCP` | port 443 |
| | `All UDP` | port 53 |
| | `Kubernetes Service Endpoint Security Group` | ports 30000-32767 |
{: caption="Table 2. Configuration example for {{site.data.keyword.pag_short}} Security Group}

### VSI Security Group
{: #vsi-security-example }

| Route | Allow | Value |
|-----------|------|-------|
| Ingress| `{{site.data.keyword.pag_short}} Security Group` | port 22 |
| Egress| `{{site.data.keyword.pag_short}} Security Group` |  |
{: caption="Table 3. Configuration example for VSI Security Group}

### Kubernetes Service Endpoint
{: #kubernetes-workers-example }

| Route | Allow | Value |
|-----------|------|-------|
| Ingress| `{{site.data.keyword.pag_short}} Security Group` | ports 30000-32767 |
{: caption="Table 4. Configuration example for Kuvernetes Workers}

See this link for more details on securing Kubernetes worker nodes:[Overview of network security options](https://cloud.ibm.com/docs/containers?topic=containers-vpc-network-policy).

### Kubernetes API
{: #kubernetes-api-example }

Kubernetes clusters should have the Public Service Endpoint disabled.  The Private Cloud Service Endpoint should be enabled and configured to only allow connections from the {{site.data.keyword.pag_short}} instance.  For more information about enabling and configuring a Private Cloud Service Endpoint with an allow-list, please see here: [Accessing clusters through the private cloud service endpoint](https://cloud.ibm.com/docs/containers?topic=containers-access_cluster#access_private_se)

You can connect to IBM Cloud resources in other VPC networks by using a Transit Gateway. However, it is your responsibility to secure the network paths in order to prevent unauthorized access to those resources.
{: note}
