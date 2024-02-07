# GCP Cloud Shell SDK

## Basics
- Launch anywhere from the GCP web console with the `console icon` in the top right menu.
- Open in a new tab with `open in new window` icon in the top right of the cloud shell sub window terminal. (icon of a square with an arrow pointing to the top right)

- Switch output of commands to table view
  - `gcloud config set accessibility/screen_reader false`

- Get a list of available regions
  - `gcloud computer regions list`

- Get a list of instances
  - `gcloud compute instances list`

- SSH into an instance where `instance-1` is the name of the instance
  - `gcloud compute ssh instance-1`
