# Example for managing kubernetes with terraform 

https://learn.hashicorp.com/tutorials/terraform/kubernetes-provider?in=terraform/kubernetes

# Steps 

## 1. create kind cluster

```
kind create cluster --name terraform-learn --config kind-config.yaml
```

## 2. configure the provider

```
cd learn-terraform-deploy-nginx-kubernetes
touch kubernetes.tf
```

configure the kubernetes.tf as follow

```
terraform {
  required_providers {
    kubernetes = {
      source = "hashicorp/kubernetes"
    }
  }
}

provider "kubernetes" {

  config_path    = "~/.kube/config"
  config_context = "kind-terraform-learn"
}

```

initialize the terraform workspace with following 

```
terraform init
```

## 3. deploy a deployment

add following to kubernetes.tf file

```
resource "kubernetes_deployment" "nginx" {
  metadata {
    name = "scalable-nginx-example"
    labels = {
      App = "ScalableNginxExample"
    }
  }

  spec {
    replicas = 2
    selector {
      match_labels = {
        App = "ScalableNginxExample"
      }
    }
    template {
      metadata {
        labels = {
          App = "ScalableNginxExample"
        }
      }
      spec {
        container {
          image = "nginx:1.7.8"
          name  = "example"

          port {
            container_port = 80
          }

          resources {
            limits = {
              cpu    = "0.5"
              memory = "512Mi"
            }
            requests = {
              cpu    = "250m"
              memory = "50Mi"
            }
          }
        }
      }
    }
  }
}

```

then apply the new config to create the deployment

```
terraform apply
```

