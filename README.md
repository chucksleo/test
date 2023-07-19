# SAIC kubernetes namespace Terraform Module

This Terraform module creates namespace for Kubernetes within SAIC.

## Requirements

| Name      | Version   |
|-----------|-----------|
| terraform | >= 0.15.5 |
| aws       | >= 3.62   |


## Usage
```hcl
module "example_namespace" {
  source        = "./terraform-kubernetes-namespace"
  namespace_name = "namespace"
  labels = {
    environment = "production"
    team        = "devops"
  }
}
```




## Resources

| Name                                             | Type     |
|--------------------------------------------------|----------|
| [namespace](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/namespace_v1) | resource |

## Inputs

| Name             | Type         | Required | Default | Description    |
|------------------|--------------|----------|---------|----------------|
| namespace_name               | string     | yes      |         | Name of the Kubernetes namespace |
| labels        | map(string)       | no      |         | Labels to apply to the namespace |
| annotations | map(string)     | yes      |         | Annotations to apply to the namespace |
| resources       | list(string)       | no      |         | List of resources this resource can access |

## Outputs

| Name               | Description                                  |
|--------------------|----------------------------------------------|
| namespace_name  | The name of the namespace           |      |


-----------------------------------------------------------
output "namespace_name" {
  value = kubernetes_namespace.namespace.metadata.name
}
