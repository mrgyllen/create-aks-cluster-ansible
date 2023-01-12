<div align="center">

![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
  
</div>
  
# Create AKS Cluster

Sample playbooks for deploying a basic Azure kubernetes cluster with Ansible.

## Prerequisites

- You need an Azure account and if you don't have one, get a [free one](https://azure.microsoft.com/en-us/free/).

- Create a service principal (replace [ServicePrincipalName] with a name and [subscription-id] with your id) and copy the JSON output:

    `az ad sp create-for-rbac -n [ServicePrincipalName] --role Contributor --scopes /subscriptions/[subscription-id] --sdk-auth`

- You need an SSH RSA key to be used as the public key to connect to the cluster.
  
  <code>$ ssh-keygen -t rsa -b 4096</code>
  
  View your public key:
  <code>$ cat ~/.ssh/id_rsa.pub</code>

- Create GitHub secrets (to be used by GitHub actions and Ansible) based on the above JSON output:

    * `AZURE_CREDENTIALS` set and use the entire JSON block.
    * `CLIENT_ID` set to the `clientId` from the JSON block.
    * `CLIENT_SECRET` set to the `clientSecret` from the JSON block.
    * `SSH_KEY` set to single line SSH RSA from the public key output.

- Set Ansible variables, used in: `create-aks.yaml`

```yaml
  vars:
    resource_group: gyllencreutz-rg
    location: northeurope
    aks_name: gyllencreutz-aks
    username: azureuser
    aks_version: 1.25.2
```


## How to run
The CI Action `.github/workflows/main.yaml` is set to execute on Push, Pull Request and Manual. Remember to push with all variables set!

You can also execute Delete Action `.github/workflows/delete.yaml` to tear down the AKS cluster
## Resources

[MS-Learn: Using Ansible with Azure](https://learn.microsoft.com/en-us/azure/developer/ansible/overview)

[MS-Learn: Introduction to Kubernetes on Azure](https://learn.microsoft.com/en-us/training/paths/intro-to-kubernetes-on-azure/)

[Ansible: Get Started with Azure](https://docs.ansible.com/ansible/latest/scenario_guides/guide_azure.html)

[Ansible: Ansible Playbook](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks.html)

[Ansible: Ansible role azure_preview_modules](https://galaxy.ansible.com/Azure/azure_preview_modules)

[Ansible Galaxy](http://galaxy.ansible.com) 
