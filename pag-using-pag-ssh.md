---

copyright:
  years: 2022
lastupdated: "2022-11-30"

keywords: using PAG with SSH, using SSH, key agent, host name, gateway

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# SSH
{: #pag-using-pag-ssh}

Once you have provisioned a {{site.data.keyword.pag_full}} instance, and your {{site.data.keyword.virtualmachinesshort}} have been prepared as described [here](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-prep-vsi), you are ready to start using it to access your servers.

IBM requires that the SSH key agent is running on your local machine to use {{site.data.keyword.pag_short}} with the CLI. This requirement will go away in future releases.
{: note}

To run the key agent, run:
```sh
$ eval ssh-agent
```


1. Make sure you have the {{site.data.keyword.pag_short}} CLI plug-in installed on your local machine. If you do not have it, you can install by typing `ibmcloud plugin install pag`.

1. Login with the CLI to your IBM cloud account, selecting the us-south region. For example, `ibmcloud login --sso -r us-south`.

1. Make sure you are logged in to the {{site.data.keyword.vpn_short}} you had setup in the VPN Setup section of this [page](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-requirements). If you do not do this, the {{site.data.keyword.pag_short}} hostname will not be accessible, and will time out.

1. Set {{site.data.keyword.pag_short}} to use the gateway hostname of your instance. The gateway hostname is displayed on the Endpoint tab of the {{site.data.keyword.pag_short}} service UI for that instance.

   ```sh
   $ibmcloud pag gateway set <gateway URL>
   ```

## Steps for connecting to an endpoint
{: #pag-connecting-endpoint}

1. Run SSH to a target endpoint by means of {{site.data.keyword.pag_short}}.

   ```sh
   $ ibmcloud pag ssh connect <target-host IP>
     ex.  ibmcloud pag ssh connect 169.59.165.66
   ```

1. Execute the commands on to the target VSI through the interactive terminal.

1. Type `exit` or `logout` to end the session.

## Retrieving and viewing the session recordings
{: #pag-retrieve-recordings}

You can retrieve and view your [session recordings](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-session-recording-playback).
