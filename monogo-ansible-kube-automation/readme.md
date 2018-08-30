### MONGO on Kubernetes using Ansible

This repository contains code for deploying MONGO services on Kubernetes using Ansible.

#### Supported environments

 - Existing kubernetes cluster with cloud provider integration ( AWS only )
 - Minikube ( WIP )

##### Deployment types

 - Complete MONGO environment with couchbase on VMs
 - Complete MONGO enviroment minified version with couchbase on containers

##### Analogy

        					                  -----------
        					                 | Kubernetes |
        					                  -----------
        					                      / \
        					                     /   \
        					                    /     \
        					      -----------------  ------------------  
        					     | Non-prod cluster | Pre-Prod cluster |
        					      -----------------  ------------------
        					                /               \
        					               /                 \
        					              /                   \
              			 -------------------------            ----------------------------
              			| dev | feature1 | feature2..        | int | stg | uat |
              			 ---------------------------	     --------------------------------	         
              			               /                                 \
              			 ---------------------------          ----------------------------------
              			 vault-nonprod.yml                       vault-preprod.yml
              			 config_nonprod.yml                      config_preprod.yml
              			 nonprod.yml                             preprod.yml
              			 ---------------------------          -----------------------------------

##### Pre-prod cluster [ us-west-2 ]

  - UAT
  - Stage
  - QA
  - INT
  - Performance

##### Non-prod cluster [ ap-southeast-1 ]

- Development ( dev )
- Feature teams - namespaces

#### Using Ansible-Vault

```shell
ansible-vault edit group_vars/${vault__env_file}
# Provide password and change/add values as desired
```


#### Examples

##### 1. Deploying a namespace
-
```python
ansible-playbook -vv --vault-id @prompt -e "ns_name=mongo-uat env_ver=pre-prod env=uat" site.yml
```
- Provide vault password based on cluster type ( non-prod / pre-prod )
- ns_name -  Name of the environment. Secrets/configuration maps, services etc are based on this parameter
- env_ver - [ pre-prod | non-prod ]
- env - [ feature | dev | int | qa ...]. Passwords are choosen from vault based on this parameter

##### 2. Creating just secrets
-
```python
ansible-playbook -vv --vault-id @prompt -e "ns_name=mongo-uat env_ver=pre-prod env=uat" site.yml --tags secrets
```
- tags are WIP and added to some roles

TODO:
- Minishift provisioning
- Tags
- Route53 and lambda integration
- Integration with cluster creation repo

@OPENSOURCEBOOK
