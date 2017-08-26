# Prerequisite
- Install ``Ansible``
- Install ``apache-libcloud``

```
$ sudo pip install apache-libcloud
```
## Get Compute Engine Default Service Account Keys
- Open GCP Console --> IAM --> Service Account --> "Compute Engine default service account" --> Create Key

![Compute Engine default service account](http://i.imgur.com/wgaBmZW.png)

- Download JSON file

![Compute Engine default service account Credentials](http://i.imgur.com/ShLHvCM.png)

-  Take a look at this JSON file to gather the following details which will be used later
   - client_email
   - project_id


# Managing GCE/GPD using Ansible

- Git clone this repo
```
$ git clone https://github.com/ksingh7/gce_ansible.git
```
- Eport necessary GCE details (don't forget to update this)

```
export GCE_EMAIL=<client_email from JSON file>
export GCE_PROJECT=<project-id from JSON file>
export GCE_CREDENTIALS_FILE_PATH=<path-to-GCE-default-service-account-credentials-downloaded-previously>
```
- Edit ``group_vars/all`` file for your desired changes

- Provision GCP Resources (GCE+GPD)

```
ansible-playbook -i hosts provision-gpc-resources.yml
```

- Destroy GCE

```
ansible-playbook -i hosts destroy-gcp-resources.yml
```

- Destroy GCE + GPD

```
ansible-playbook -i hosts destroy-gcp-resources.yml -e "disk_state=absent"
```
