# platform
Repository to manage development platform resources


## Prerequisites

### GCP Service Account & Key
```
gcloud iam service-accounts create platform-svc \
    --display-name="Terraform Service Account"

gcloud projects add-iam-policy-binding ssw-590-final-378804 \
    --member "serviceAccount:platform-svc@$GCP_PROJECT.iam.gserviceaccount.com" \
	--role=roles/container.admin

gcloud projects add-iam-policy-binding ssw-590-final-378804 \
    --member "serviceAccount:platform-svc@$GCP_PROJECT.iam.gserviceaccount.com" \
	--role=roles/storage.admin

gcloud projects add-iam-policy-binding ssw-590-final-378804 \
    --member "serviceAccount:platform-svc@$GCP_PROJECT.iam.gserviceaccount.com" \
	--role=roles/container.clusterViewer

gcloud iam service-accounts keys create creds.json \
    --iam-account=platform-svc@$GCP_PROJECT.iam.gserviceaccount.com

export GKE_SA_KEY=$(cat creds.json | base64)
```

