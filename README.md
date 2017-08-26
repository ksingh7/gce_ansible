# Prequisites
- Install ``Ansible``
- Install ``apache-libcloud``

```
$ sudo pip install apache-libcloud
```
## Get Compute Engine Default Service Account Keys
- Open GCP Console > IAM > Service Account > "Compute Engine default service account" > Create Key > Download JSON file

```
export GCE_EMAIL=<your-service-account-email>
export GCE_PROJECT=<your-project-id>
export GCE_CREDENTIALS_FILE_PATH=/Users/karasing/.config/gcloud/application_default_credentials.json
```
- Provision GCP Resources

```
ansible-playbook -i hosts provision-gpc-resources.yml
```

- Destroy GCP Resources

```
ansible-playbook -i hosts destroy-gcp-resources.yml -e "disk_state=absent"
```
