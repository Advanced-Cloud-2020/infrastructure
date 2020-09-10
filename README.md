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

## Instructions to run code

#### [Jenkins setup](#JenkinsSetup)

*   Created [ansible](https://docs.ansible.com/ansible/latest/index.html) playbooks to create infrastructure
*   Hosted [jenkins](https://jenkins.io/doc/) on a custom domain `jenkins.username.com`
*   The ansible playbooks launches the EC2 instances and bootstraps the instance to start a secured jenkins server
*   Secured the jenkins server by enabling SSL and periodically updating the [let’s encrypt](https://letsencrypt.org/) certificates
*   Configured a custom custom domain in [Route53](https://aws.amazon.com/route53/) and updating the Route53 A record with the launched EC2 instances public dns
*   Clone the repo

#### Credentials
1. dockerhub_credentials(Username and Password)
2. github-ssh(SSH) 
3. kubernetes_credentials(Username and Password) -> Username: admin, Password: (~/.kube/config/users:password | base64 )
#### Configure System
1. Manage Jenkins -> Configure System -> Cloud -> Kubernetes:
Kubernetes server certificate key: (~/.kube/config/clusters:certificate-authority-data | base64decode )
Credentials: kubernetes_credentials  

    
#### Plugins to be Installed on Jenking to make CI/CD Work
1. GitHub Integration
2. Kubernetes CLI
3. Kubernetes
4. SSH Agent

### To create vpc and ec2 instance run command 

* AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_setup.yml --extra-var "ec2_instance_size=<instance_size> key_pair=<ec2_key_pair> elastic_ip=<elastic_ip_address> route53_zone_name=<domain_name> route53_record_name=<jenkins.domain_name> letsencrypt_email=<your_email_id> domain_name=<jenkins.domain_name> staging_cert=false"  -vvv



### To teardown vpc and ec2 instance run command

* AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=<elastic_ip_address>"







# Team information

| Team Members        | Github Id            | NUID      |
| ------------------- |:--------------------:|:---------:|
| Suhas Pasricha      | suhas1602            | 001434745 |
| Puneet Tanwar       | puneetneu            | 001409671 |
| Cyril Sebastian     | cyrilsebastian1811   | 001448384 |
| Shubham Sharma      | shubh1646            | 001447366 |
