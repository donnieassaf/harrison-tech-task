# Running the Project on Minikube

This project is designed to run in a Kubernetes environment using minikube. It deploys the "hello world" application into a local developlment cluster (minikube)

## Why Minikube Over K3s?
The original task suggested using K3s as a lightweight Kubernetes solution for local development. K3s is an excellent tool, and it can be a great choice for many use cases due to its simplicity and lower resource demands compared to a full Kubernetes installation.

However, for this project, I decided to use Minikube instead for several reasons:

1. Familiarity: I've had a lot of experience working with Minikube, and I find it to be a robust and reliable tool for local Kubernetes development. This familiarity allows me to identify and resolve any issues quickly.

2. Full Kubernetes Experience: While K3s is designed to be a lightweight, stripped-down version of Kubernetes, Minikube provides a full Kubernetes experience out of the box. This can be beneficial when you want to experiment with different Kubernetes features or test the production readiness of your application.

3. Add-ons Support: Minikube's support for enabling and managing Kubernetes add-ons, such as the Ingress controller, simplifies the configuration process. This feature makes it a bit easier to set up complex services and applications.

Note - minikube defiently comes with its painful setup when it comes to the m1 chip

## Prerequisites

Make sure you have the following tools installed on your local machine:

- [Terraform](https://www.terraform.io/downloads.html)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Kubernetes](https://kubernetes.io/docs/setup/)

## Deployment Steps

Follow the steps below to deploy the "hello world" application:

1. Start Minikube: minikube start.

2. Enable necessary addons: minikube addons enable ingress and minikube addons enable ingress-dns.

3. Wait until the ingress-nginx-controller-XXXX is up and running. You can check this by using: kubectl get pods -n ingress-nginx.

4. Initialize Terraform in your project directory: terraform init.

5. Plan your Terraform changes: terraform plan.

6. Apply your Terraform changes: terraform apply.

7. Open your /etc/hosts file and append 127.0.0.1 your-hostname.com at the end (replace your-hostname.com with the actual hostname you have configured in your Ingress resource which for this project is harrsiontask.com).
  - Note: On MacOS, if you are using an M1 chip, you need to use 127.0.0.1 instead of the Minikube IP as a workaround.

8. Run minikube tunnel. This command requires administrative privileges to create network routes, so you will likely need to enter your system password. Once the tunnel is up and running, keep this terminal window open.

9. You should now be able to access the application by entering harrisontask.com (the one you specified in step 7) into a web browser. Your request will be routed to your service via the Ingress.


## Preferred Deployment Method: Helm and ArgoCD on Amazon EKS
While Minikube provides a great local development environment, when it comes to production deployments, I would much prefer the method involving using Helm Charts for packaging the application, ArgoCD for continuous deployment, and provisioning Amazon EKS (Elastic Kubernetes Service) for cluster management in Terraform.

## Additional Notes

- If you encounter any problems, please refer to the Minikube, Terraform, and Kubernetes Ingress documentation.

---