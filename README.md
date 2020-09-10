# Kubernetes (CSYE 7374- Advanced Cloud computing) | Cloud Computing

## Summary

Simulation on production grade kubernetes deployment on AWS

*   Backend application is built on java using spring boot framework
*   Created a minimal frontend application with react
*   Containerized the applications with docker and stored them in private repository
*   Setup the jenkins infrastructure on a custom domain using ansible
*   Created webhooks to Jenkins to create,tagged and pushed docker images on each commit
*   Created a [kubernetes](https://kubernetes.io/docs/concepts/) cluster in HA setup and deployed the microservices
*   Service discovery for frontend and backend
*   Created [helm charts](https://helm.sh/docs/chart_template_guide/getting_started/) to deploy the application


## Information about clusters 

*   Created ansible play-book to launch the cluster in Dev and Prod environments
*   Playbooks handle the number of nodes and sizes of compute and master nodes depending on the type of environment
*   Created kubernetes clustes in HA setup in 3 different availability zones picking the zones automatically in production setup
*   Created the clusters with private topology and has a [bastion](https://github.com/kubernetes/kops/blob/master/docs/bastion.md) host to maintain the compute and master node
*   Used ansible [k8s](https://docs.ansible.com/ansible/latest/modules/k8s_module.html) module to deploy the application on the clusters

## Microservices

### Backend

*   The Recipe Management Web application is developed using Java Spring Boot framework that uses the REST architecture
*   Secured the application with [Spring Security](https://spring.io/projects/spring-security) Basic [authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication) to retrieve user information
*   Storing the images of recipes in S3
*   The data is cached in Redis for 10 minutes for faster IO
*   Containerized the application

### FrontEnd

*   A minimal frontend built on [react](https://reactjs.org/docs/getting-started.html) to view the recipes
*   The frontend app uses a public endpoint exposed by backend
*   Containerized the application



## Instructions to run code

### Jenkins Setup

*   Created [ansible](https://docs.ansible.com/ansible/latest/index.html) playbooks to create infrastructure
*   Hosted [jenkins](https://jenkins.io/doc/) on a custom domain `jenkins.username.com`
*   The ansible playbooks launches the EC2 instances and bootstraps the instance to start a secured jenkins server
*   Secured the jenkins server by enabling SSL and periodically updating the [let’s encrypt](https://letsencrypt.org/) certificates
*   Configured a custom custom domain in [Route53](https://aws.amazon.com/route53/) and updating the Route53 A record with the launched EC2 instances public dns
*   Clone the repo

 ### Credentials needed 
* dockerhub_credentials(Username and Password)
* github-ssh(SSH) 
* kubernetes_credentials(Username and Password) -> Username: admin, Password: (~/.kube/config/users:password | base64 )
### Configure System
* Manage Jenkins -> Configure System -> Cloud -> Kubernetes:
* Kubernetes server certificate key: (~/.kube/config/clusters:certificate-authority-data | base64decode )
* Credentials: kubernetes_credentials  

### Plugins to be Installed on Jenking to make CI/CD Work
1. GitHub Integration
2. Kubernetes CLI
3. Kubernetes
4. SSH Agent











## Team information

| Team Members        | Github Id            | NUID      |
| ------------------- |:--------------------:|:---------:|
| Suhas Pasricha      | suhas1602            | 001434745 |
| Puneet Tanwar       | puneetneu            | 001409671 |
| Cyril Sebastian     | cyrilsebastian1811   | 001448384 |
| Shubham Sharma      | shubh1646            | 001447366 |
