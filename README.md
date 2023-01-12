<div align="center">

![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
  
</div>
  
# Create AKS Cluster

Sample playbooks for deploying a basic Azure kubernetes cluster with AnsibleThis repository contains examples and best practices for building Ansible Playbooks for Azure.

## Prerequisites

- Azure Account. If you don't have one, get a [free one](https://azure.microsoft.com/en-us/free/).

- Create a service principal (replace [subscription-id] with your id) and copy the JSON output:

    `az ad sp create-for-rbac -n AzCI_ServicePrincipal --role Contributor --scopes /subscriptions/[subscription-id] --sdk-auth`

  Create project secrets based on above JSON output:

    * `AZURE_CREDENTIALS` set to use the entire JSON block. This is used by the `azure\login` GitHub action to provision the cluster
    * `CLIENT_ID` set to the `clientId` from the JSON block. This is used to allow the SP to connect to the cluster
    * `CLIENT_SECRET` set to the `clientSecret` from the JSON block. This is used to allow the SP to connect to the cluster
    * `SSH_KEY` set to single line SSH RSA from the JSON block. This is used as the public key to connect to the cluster. This can be found in C:\Users\\[username]\\.ssh\id_rsa.pub

## How to run



## Resources

[Ansible on Azure](https://learn.microsoft.com/en-us/azure/developer/ansible/overview)

[Get Started with Azure](https://docs.ansible.com/ansible/latest/scenario_guides/guide_azure.html)

[Ansible Playbook](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks.html)

[Ansible role azure_preview_modules](https://galaxy.ansible.com/Azure/azure_preview_modules)

[Ansible Galaxy](http://galaxy.ansible.com) 
