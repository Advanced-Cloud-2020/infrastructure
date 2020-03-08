# Team information

| Team Members        | Github Id            | NUID      |
| ------------------- |:---------           :|:---------:|
| Suhas Pasricha      | suhas1602            | 001434745 |
| Puneet Tanwar       | puneetneu            | 001409671 |
| Cyril Sebastian     | cyrilsebastian1811   | 001448384 |
| Shubham Sharma      | shubh1646            | 001447366 | 

# Instructions to run code

### To create vpc and ec2 instance run command 

AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_setup.yml --extra-var "ec2_instance_size=<instance_size> key_pair=<ec2_key_pair> elastic_ip=<elastic_ip_address> route53_zone_name=<domain_name> route53_record_name=<jenkins.domain_name> letsencrypt_email=<your_email_id> domain_name=<jenkins.domain_name> staging_cert=false"  -vvv

#### Cyril
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
export IP=52.201.183.194
export INSTANCE_SIZE=t2.samll
echo $AWS_PROFILE $AWS_REGION $IP $INSTANCE_SIZE
ansible-playbook -i development aws_vpc_ec2_setup.yml --extra-var "ec2_instance_size=$INSTANCE_SIZE key_pair=csye7374 elastic_ip=$IP route53_zone_name=jenkins.${AWS_PROFILE}.cyril-sebastian.com route53_record_name=jenkins.${AWS_PROFILE}.cyril-sebastian.com letsencrypt_email=a@a.com domain_name=jenkins.${AWS_PROFILE}.cyril-sebastian.com staging_cert=false" -vvv

### To teardown vpc and ec2 instance run command

AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=<elastic_ip_address>"

#### Cyril
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
echo $AWS_PROFILE $AWS_REGION
ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=<ip>"


## Jenkins

### Plugins to be Installed
1. GitHub Integration
2. Kubernetes CLI
3. SSH Agent

### Configuration for Pipeline
#### Credentials
1. dockerhub_credentials(Username and Password) --> Username: cyrilsebastian1811, Password: Onepiece181195
2. github-ssh(SSH) --> Username: github, Private Key(contents of cyril_work from local)
3. kubernetes_credentials(Username and Password) --> Username: admin, Password: (~/.kube/config/users:password | base64 )
#### Configure System
1. Manage Jenkins -> Configure System -> Cloud -> Kubernetes:
Kubernetes server certificate key: (~/.kube/config/clusters:certificate-authority-data | base64decode )
Credentials: kubernetes_credentials
   