# NFS Server Deployment Configuration

This Kubernetes configuration sets up an NFS server using the `gcr.io/google_containers/volume-nfs:0.8` image. It includes a Service, PersistentVolume (PV), and PersistentVolumeClaim (PVC) to make NFS storage accessible to other Pods within the cluster.

## Deployment Configuration

- **Deployment Name:** nfs-server
- **Namespace:** default
- **Replicas:** 1
- **Image:** gcr.io/google_containers/volume-nfs:0.8
- **Ports:** The Deployment exposes NFS ports (2049, 20048, 111) for communication.

  ### Prerequisites

Before you begin, ensure that you have the following tools installed:

- **kubectl:** The Kubernetes command-line tool. If it's not already installed, you can follow the official [kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

- **gcloud CLI:** The Google Cloud command-line tool. You can install it by following the instructions in the [gcloud CLI installation guide](https://cloud.google.com/sdk/docs/install).

### Usage

To deploy the NFS server, follow these steps using `glcoud & kubectl`:

 Step 1: Create a GCP Disk

Create a Google Cloud Platform (GCP) persistent disk with a size of 10GB. Replace `ZONE` with your preferred zone.
Step 1: Create disk in GCP

```bash
gcloud compute disks create --size=10GB --zone=ZONE gce-nfs-disk
```
Step 2: Connect to GKE Cluster
```bash
gcloud container clusters get-credentials CLUSTER_NAME --zone ZONE --project PROJECT_NAME
```
Step 3: Deploy NFS Server
```bash
kubectl apply -f nfs.yaml
```

