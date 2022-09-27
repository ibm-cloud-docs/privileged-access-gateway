---

copyright:
  years: 2022
lastupdated: "2022-08-28"

keywords: PAG session recording playback, session recording, COS, IAM

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# PAG session recording playback​
{: #pag-session-recording-playback}

- The session recordings from both SSH and Kubernetes sessions are stored in the COS bucket that you specified on the provisioning form when creating your {{site.data.keyword.pag_full}} (PAG) instance​
- The customer session auditor must have IAM access to the {{site.data.keyword.cos_full}} (COS) bucket, and will download the recording(s) from the COS bucket to their local machine
- ​Download the recording file from the COS bucket to a local machine
- There is one file in the COS bucket per SSH or Kubernetes session​
- A session file can then be played back on the customers local machine using the PAG CLI as follows:​ `ibmcloud pag play-recording \<path-to-session-file>` ​

1. The session recordings are stored within the COS bucket that was referred to while provisioning the PAG instance.
2. The recordings file name would look something like

   ```sh
   ex .ssh_343b0697-16d4-4751-adf9-47068c2e49c0_IBMid-50AYPQT91D@10.240.64.64_22
   ```

3. Download the file to a local machine.
4. Play the recording with CLI: `ibmcloud pag play <path_to_the_file>`

   ```sh
   ex : ibmcloud pag play /Users/bob/ssh_343b0697-16d4-4751-adf9-47068c2e49c0_IBMid-50AYPQT91D@10.240.64.64_22
   ```
