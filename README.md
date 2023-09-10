# AWS-via-WSL2

Install wsl from Command Promt or PowerShell <br>
restart computer and confirm installation<br>
```
wsl --install
wsl.exe -l -v
```
![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/7f578c50-ec27-45b0-835d-ad841110a0cf)

Follow https://us-east-1.console.aws.amazon.com/iamv2/home#/users/details/${user}?section=security_credentials to create access key<br>
Replace ${user} with the AWS user<br>
Configure aws with access key credentials and suitable region<br>
```php
sudo apt-get update
sudo apt install python3-pip
sudo pip3 install awscli
aws configure
```
For awscliv2, follow the procedure [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) and configure the access credentials

Check users<br>

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/cfe07e67-9dab-462d-b0c8-eb9988b9763c)

WSL2 is now AWS CLI ready<br>

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/1e10a2f0-aeef-44a2-af1b-ea18ff7cb114)

![image](https://github.com/qaswarh/AWS-via-WSL2/assets/47313728/872ad8db-ab7a-41c1-9328-4afadd8aa488)

Install [aws-iam-authenticator](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)<br>
Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)<br>
Install [Terraform](https://developer.hashicorp.com/terraform/downloads?ajs_aid=cf16efbb-6de3-4e7e-88b8-1b2434d684d5&product_intent=terraform)<br>
Provision an [EKS cluster (AWS)](https://developer.hashicorp.com/terraform/tutorials/kubernetes/eks) with ekscluster.tf using:<br>
[aws_eks_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eks_cluster.html) which has dependancy on [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies), [AmazonEKSClusterPolicy](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEKSClusterPolicy.html) and [AmazonEKSServicePolicy](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEKSServicePolicy.html)<br>
[aws_eks_node_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/eks_node_group.html?lang=typescript) which depends on [AmazonEKSWorkerNodePolicy](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEKSWorkerNodePolicy.html), [AmazonEKS_CNI_Policy](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEKS_CNI_Policy.html) and [AmazonEC2ContainerRegistryReadOnly](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEC2ContainerRegistryReadOnly.html)
vpc.tf will use [Provision Instructions](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest) of Terraform AWS VPC Module. vpc_config in ekscluster.tf will use subnets from vpc.tf<br>
desired, max and min sizes all set to 1 in scaling_config to cluster charges minimum<br>
resource, policy_arn and role for eks_cluster & eks_nodes are defined in iam.tf to have assume_role_policy as per [Amazon EKS cluster IAM role](https://docs.aws.amazon.com/eks/latest/userguide/service_IAM_role.html)<br>



