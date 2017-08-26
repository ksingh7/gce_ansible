# Ansible Prequisites
- Install Ansible
- Install ``apache-libcloud``

```
$ sudo pip install apache-libcloud
```

- Open GCP Console > IAM > Service Account > "Compute Engine default service account" > Create Key > Download JSON file

```
export GCE_EMAIL=<your-service-account-email>
export GCE_PROJECT=<your-project-id>
export GCE_CREDENTIALS_FILE_PATH=/Users/karasing/.config/gcloud/application_default_credentials.json
```

```
export GCE_PROJECT=scogo-test-env
export GCE_EMAIL=151602902460-compute@developer.gserviceaccount.com
export GCE_CREDENTIALS_FILE_PATH=/Users/karasing/.ssh/scogo-test-env-854dcbcadd76.json
```
- Provision GCP Resources

```
ansible-playbook -i hosts provision-gpc-resources.yml
```

- Destroy GCP Resources

```
ansible-playbook -i hosts destroy-gcp-resources.yml -e "disk_state=absent"
```
