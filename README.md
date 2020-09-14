# gadsproject2020
Google Africa Developper Scholarship. 

this project is for GADS project phase II
Google cloud associate.
here you will find screen captures of received emails from qwiklabs
and translation inside this file.

 LAB 1 - Accessing the GCP Console and Cloud Shell


### Task 0. Lab Setup
### Task 1. Explore the GCP Console

- Verify that your project is selected 

  ```$ gcloud config list project```
  
- STEPS 1-2. Get the project ID

```gcloud config list --format 'value(core.project)' 2>/dev/null```

- Creating_a_bucket

```gsutil mb gs://qwiklabs-gcp-03-1589bd7eb44b```

- Create a virtual machine (VM) instance

```gcloud compute instances create first-vm --zone=central1-c --customcpu=4 --machine-type=n1-standard-2 --tags http-server```

- Explore the VM details

```gcloud compute instances describe first-vm --zone us-central1-c```
```gcloud compute disks describe my-disk --zone=us-east1-a```

- Create an IAM service account

```gcloud iam service-accounts create test-service-account  --description="editor" --display-name="editor" --condition=[key=JSON]```
### Task 2. Explore Cloud Shell

- Creating_environment_variables

```MY_BUCKET_NAME_1=qwiklabs-gcp-03-1589bd7eb44b```

```MY_BUCKET_NAME_2=my_bucket_2```

```MY_REGION=us-central1```

Move the credentials file you created earlier into Cloud

- Uploading_credentials.json_to_first-vm

```gcloud compute scp Desktop/credentials.json first-vm:~```

Create a second Cloud Storage bucket and verify it in the

- creating_a_bucket

```gsutil mb gs://$MY_BUCKET_NAME_2```

- verifying_bucket_creation

```gsutil ls```

Use the gcloud command line to create a second virtual machine
- list_zones in my region

```gcloud compute zones list | grep $MY_REGION```

- Select a zone from the list #us-central1-b

```MY_ZONE=us-central1-b```
```gcloud config set compute/zone $MY_ZONE```

- Environment_virable_for_my_second_vm

```MY_VMNAME=second-vm```

- Create_a_vm_in_a_default_zone

```gcloud compute instances create $MY_VMNAME --machine-type "n1-standard-1" --image-project "debian-cloud" --image-family "debian-9" --subnet "default"```

- Display_instance_list

```gcloud compute instances list```

Copy the first-vm’s external IP
Use the gcloud command line to create a second service
account
- Create_service_account

```gcloud iam service-accounts create test-service-account2 --display-name test-service-account2```

- Bind_roles

```gcloud projects add-iam-policy-binding $GOOGLE_CLOUD_PROJECT --member serviceAccount:test-serviceaccount2@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com --role roles/viewer```

- Copy_a_picture

```gsutil cp gs://cloud-training/ak8s/cat.jpg cat.jpg```

- Copy_the_file_into_the_bucket

```gsutil cp cat.jpg gs://$MY_BUCKET_NAME_1```

- Copy_the_file_from_the_first_bucket_to_the_second_bucket

```gsutil cp gs://$MY_BUCKET_NAME_1/cat.jpg gs://$MY_BUCKET_NAME_2/cat.jpg```

- Set the access control list for a Cloud Storage object
    - Get_the_default_access_list

```gsutil acl get gs://$MY_BUCKET_NAME_1/cat.jpg > acl.txt```

```cat acl.txt```

- Change_the_private_access

```gsutil acl set private gs://$MY_BUCKET_NAME_1/cat.jpg```

- Verify_ACL

```gsutil acl get gs://$MY_BUCKET_NAME_1/cat.jpg > acl-2.txt```
```cat acl-2.txt```

Authenticate as a service account in Cloud Shell
- View_current_configs

```gcloud config list```

- Change_the_authenticated_user

```gcloud auth activate-service-account --key-file credentials.json```

- Verify_current_configs

```gcloud config list```

- Verif_lists_of_authorized_users

```gcloud auth list```

- Verify_access_roles

```gsutil cp gs://$MY_BUCKET_NAME_1/cat.jpg ./cat-copy.jpg```
```gsutil cp gs://$MY_BUCKET_NAME_2/cat.jpg ./cat-copy.jpg```

- Switch_service_account

```gcloud config set account student-03-eb20a744a395@qwiklabs.netv```

- verify_that_you_can_access_the_cat.jpg

```gsutil cp gs://$MY_BUCKET_NAME_1/cat.jpg ./copy2-of-cat.jpg```

- Make_the_first_storage_bucket_readable

```gsutil iam ch allUsers:objectViewer gs://$MY_BUCKET_NAME_1```

Task 4. Explore the Cloud Shell code editor
- clone_a_repository

```git clone https://github.com/googlecodelabs/orchestrate-withkubernetes.git```

- Create_a_directory

```mkdir test```

- Change_directory_and_display_cleanup.sh

```cd orchestrate-with-kubernetes```
```cat cleanup.sh```

- Verify that the output of cat cleanup.sh
- Return_to_home_directory

```cd```

- EDIT_THE_HTML_FILE

```cat index.html```

- ssh into the vm.
- Install_nginx

```sudo apt-get update```
```sudo apt-get install nginx```

- Copy_the_html_file_into_the _vm

```cd orchestrate-with-kubernetes```
```gcloud compute scp index.html first-vm:index.nginx-debian.html --zone=uscentral1-c```

- Copy_the_html_file_into_the_document_root

```sudo cp index.nginx-debian.html /var/www/html```

# End of LAB

LAB 2:
Course: Architecting with Google Kubernetes Engine - Foundations
Module: Kubernetes Architecture

## Task 0. Lab Setup
## Task 1. Deploy GKE clusters
- SET_ENVIRONMENT_VARIABLES

```export my_zone=us-central1-a```
```export my_cluster=standard-cluster-1```

- CREATE_CLUSTERS

```gcloud container clusters create $my_cluster --num-nodes 3 --zone $my_zone --enable-ip-alias```

# Task 2. Modify GKE clusters
- MODIFY_STANDARD-CLUSTER-1

```gcloud container clusters resize $my_cluster --zone $my_zone --size=4```

# Task 3. Deploy a sample workload

 DEPLOYING_WORKLOADS

```kubectl create deployment nginx-1 --image=nginx:latest```

# Task 4. View details about workloads in the

- VIEWING_PODS

```kubectl get pods```

- VIEWING_WORKLOADS

```kubectl get service nginx```
# END OF LAB
