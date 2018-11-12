# Kubernetes Azure Module

This module create all required resources for deploy a kubernetes cluster using
rke (Rancher Kubernetes Engine).

## Usage

```bash
module "k8s" {
  source = "https://github.com/walmartdigital/k8s-azure-module.git?ref=1.0.0"

  main_resource_group = "my-resource-group"
  images_resource_group = "my-images-resource-group"
  root_domain = "my-root-domain"
  root_domain_resource_group = "my-root-domain-resource-group"
  environment = "staging"
  k8s_image_name = "k8s-v1.0.0"
  bastion_image_name = "bastion-v1.0.0"
  ssh_public_key = "abc123"
}
```

## Arguments

* **cluster_name**: Name of the cluster (type: string, default: kubernetes).
* **environment**: Environment where the cluster is deployed (type: string, default: labs).
* **main_resource_group**: Resource group where all resources will be provisioned (type: string, required).
* **images_resource_group**: Resource group where to find the custom images (type: string, required).
* **root_domain**: Domain where to write DNS records (type: string, required).
* **root_domain_resource_group**: Resource group where to find the root domain dns zone (type: string, required).
* **environment**: The environment where to deploy (type: string, required).
* **k8s_image_name**: Custom K8s image name (type: string, required).
* **bastion_image_name**: Custom bastion image name (type: string, required).
* **ssh_public_key**: The public ssh key for connect to bastion (type: string, required).
* **default_tags**: Tags assigned to every resource that support it (type: map).
* **worker_count**: Number of workers (type: string, default: 3).

## Outputs

* **worker_ips**: The private IPs of the created worker VMs.
* **manager_ips**: The private IPs of the created manager VMs.
* **etcd_ips**: The private IPs of the created etcd VMs.
* **dns_zone_name**: Zone name generated.