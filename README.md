


## Instructions to run code
### To create vpc and ec2 instance run command 

* AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_setup.yml --extra-var "ec2_instance_size=<instance_size> key_pair=<ec2_key_pair> elastic_ip=<elastic_ip_address> route53_zone_name=<domain_name> route53_record_name=<jenkins.domain_name> letsencrypt_email=<your_email_id> domain_name=<jenkins.domain_name> staging_cert=false"  -vvv



### To teardown vpc and ec2 instance run command

* AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=<elastic_ip_address>"


## Jenkins

### Plugins to be Installed on Jenking to make CI/CD Work
1. GitHub Integration
2. Kubernetes CLI
3. Kubernetes
4. SSH Agent

### Configuration for Pipeline
#### Credentials
1. dockerhub_credentials(Username and Password) --> Username: cyrilsebastian1811, Password: Onepiece181195
2. github-ssh(SSH) --> Username: github, Private Key(contents of cyril_work from local)
3. kubernetes_credentials(Username and Password) --> Username: admin, Password: (~/.kube/config/users:password | base64 )
#### Configure System
1. Manage Jenkins -> Configure System -> Cloud -> Kubernetes:
Kubernetes server certificate key: (~/.kube/config/clusters:certificate-authority-data | base64decode )
Credentials: kubernetes_credentials  




# Team information

| Team Members        | Github Id            | NUID      |
| ------------------- |:--------------------:|:---------:|
| Suhas Pasricha      | suhas1602            | 001434745 |
| Puneet Tanwar       | puneetneu            | 001409671 |
| Cyril Sebastian     | cyrilsebastian1811   | 001448384 |
| Shubham Sharma      | shubh1646            | 001447366 |
