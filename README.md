# Hello World Application Deployment

This repository contains the Terraform configuration to deploy a "hello world" application in a local Kubernetes cluster using Minikube.

## Prerequisites

Make sure you have the following tools installed on your local machine:

- [Terraform](https://www.terraform.io/downloads.html)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)

## Deployment Steps

Follow the steps below to deploy the "hello world" application:

1. Start Minikube:
   ```shell
   minikube start
   ```

2. Set the Kubernetes context to Minikube:
   ```shell
   kubectl config use-context minikube
   ```

3. Clone this repository:
   ```shell
   git clone https://github.com/your-username/terraform-hello-world.git
   cd terraform-hello-world
   ```

4. Initialize the Terraform project:
   ```shell
   terraform init
   ```

5. Review the Terraform plan:
   ```shell
   terraform plan
   ```

6. Deploy the application:
   ```shell
   terraform apply
   ```

   When prompted to confirm the changes, type `yes`.

7. Wait for the deployment to complete. Once it's finished, you will see the URL to access the application.

8. Get the service URL:
   ```shell
   minikube service nginx-deployment -n harrison --url
   ```

   This will provide you with the URL to access the "hello world" application in your local browser.

9. Access the application:
   Open the provided URL in your web browser to see the "hello world" page served by the Nginx web server running in the Minikube cluster.

10. To clean up and delete the resources, run the following command:
    ```shell
    terraform destroy
    ```

    When prompted to confirm the destruction of resources, type `yes`.

## Additional Notes

- The Kubernetes cluster is provisioned using Minikube. Make sure you have Minikube installed and configured on your machine.
- The Terraform configuration is set up to use the Minikube context named "minikube". If you have a different context name or want to use a different Kubernetes cluster, modify the `config_context_cluster` value in the Terraform provider block accordingly.

---