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

<!-- Cyril -->
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
echo $AWS_PROFILE $AWS_REGION
ansible-playbook -i development aws_vpc_ec2_setup.yml --extra-var "ec2_instance_size=t2.micro key_pair=csye7374 elastic_ip=52.205.47.211 route53_zone_name=jenkins.dev.cyril-sebastian.com route53_record_name=jenkins.dev.cyril-sebastian.com letsencrypt_email=a@a.com domain_name=jenkins.dev.cyril-sebastian.com staging_cert=false" -vvv

### To teardown vpc and ec2 instance run command

AWS_PROFILE=<profile_name> AWS_REGION=<region> ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=<elastic_ip_address>"

<!-- Cyril -->
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
echo $AWS_PROFILE $AWS_REGION
ansible-playbook -i development aws_vpc_ec2_teardown.yml --extra-var "key=app value=jenkins elastic_ip=52.205.47.211"