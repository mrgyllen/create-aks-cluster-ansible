<div align="center">

![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
  
</div>
  
# Create AKS Cluster

Sample playbooks for deploying a basic Azure kubernetes cluster with Ansible.

## Prerequisites

- You need an Azure Account an if you don't have one, get a [free one](https://azure.microsoft.com/en-us/free/).

- Create a service principal (replace [ServicePrincipalName] with a name and [subscription-id] with your id) and copy the JSON output:

    `az ad sp create-for-rbac -n [ServicePrincipalName] --role Contributor --scopes /subscriptions/[subscription-id] --sdk-auth`

- You need a SSH RSA key to be used as the public key to connect to the cluster.
  
  <code>$ ssh-keygen -t rsa -b 4096</code>
  
  View your public key:
  <code>$ cat ~/.ssh/id_rsa.pub</code>

- Create GitHub secrets (to be used by the github actions and ansible) based on the above JSON output:

    * `AZURE_CREDENTIALS` set to use the entire JSON block.
    * `CLIENT_ID` set to the `clientId` from the JSON block.
    * `CLIENT_SECRET` set to the `clientSecret` from the JSON block.
    * `SSH_KEY` set to single line SSH RSA from the public key output.

- Set GitHub variables, used in: `create-aks.yaml`

```yaml
  vars:
    resource_group: ${{ vars.RESOURCE_GROUP }}
    location: ${{ vars.LOCATION }}
    aks_name: ${{ vars.AKS_NAME }}
    username: ${{ vars.ADMIN_USERNAME }}
    ssh_key: ${{ secrets.SSH_KEY }}
    client_id: ${{ secrets.CLIENT_ID }}
    client_secret: ${{ secrets.CLIENT_SECRET }}
    aks_version: ${{ secrets.AKS_VERSION }}
```


## How to run
  You can manually 


## Resources

[Ansible on Azure](https://learn.microsoft.com/en-us/azure/developer/ansible/overview)

[Get Started with Azure](https://docs.ansible.com/ansible/latest/scenario_guides/guide_azure.html)

[Ansible Playbook](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks.html)

[Ansible role azure_preview_modules](https://galaxy.ansible.com/Azure/azure_preview_modules)

[Ansible Galaxy](http://galaxy.ansible.com) 
