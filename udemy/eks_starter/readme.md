# AWS EKS , Kubernetes on AWS

[Udemy Course](https://www.udemy.com/course/amazon-eks-starter-kubernetes-on-aws/?couponCode=MAY_20_GET_STARTED)
authors:
- Gerd 
    - [github](https://github.com/gkoenig)
- Stephane
    - [github](https://github.com/simplesteph)
    - [medium](https://medium.com/@stephane.maarek)

## Intro
AWS infrastructure of EKS
![EKS](img/eks_intro.png)

Course Activities:
- Deploy EKS cluster using CloudFormation
- Scale K8s cluster
- Setup kubectl to access cluster
- EKS and integrations with AWS
- K8s Dashboard
- Deploy a stateless app on EKS and expose it with a public ELB
- Deploy a statefull app on EKS and bind it with EBS volumes
- Deploy a statefull app (wordpress) with EFS network drives
- AWS CLI and eksctl CLI

## 1 AWS EKS cluster setup

![eks](img/eks_2.png)

**AWS EKS cluster sut up**
- I am going to use for this course the  to use the **Region=us-east-1** (N. Virgunia)
- **Create IAM role** k8s assumes this role to create AWS resources
    - role name **AWSServiceRoleForAmazonEKS**
- **Create ssh key** to be able to ssh our EC2 instances
    - for us-east-1 is different region and we will use another key
        - rig-virginia-key.pem
- **Create Access key + secret** to enable authentication for API access
    - previously created, check the Region on the .aws/config file


**Cluster Infrastructure** on eu-west-1

![EKS](img/eks3.png)

CloudFormation template uploading:
![EKS](img/eks5.png)


- Create the infrastructure using **CloudFormation**
    - upload file 1../eks-course-vpc.yaml
        - EKS-course-stack

- Configuration of EKS, on AWS dashboard we go to EKS, here is important to check with what account the EKS is created. If there are problems with accessing the cloud form the terminal then i solved it accessing the AWS dashboard with my IAM user and not with my SSO account, because the ARN is different and there are problems in accessing the cluster using kubectl. Once you have access to the cluster then we can give access to other users using the ARN and the below file configuration **aws-auth**
    - EKS-course-cluster-udemy


**Setting up the kubectl**

How it works, executing kubectl commands require:

- kubectl config file
    - EKS endpoint
    - User authentication
        - aws-iam-authenticator executable
            - generates an authentication token based on 
                - aws credentials file
    
- [install & configure](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)  **kubectl**. 


Check the installed version of kubectl
    
    kubectl version --short --client

- Installing aws-iam-authenticator

- configure the credentials file where the aws-aim-authenticator refers to which is the .aws/credentials
    - check if it is working

            aws-iam-authenticator token -i EKS-course-cluster-udemy | python -m json.tool

There are different ways of configuring .kube/config, the aes
- **Configuration file for kubectl**

        mkdir $HOME/.kube && nano $HOME/.kube/kube-config-eks
        export KUBECONFIG=$HOME/.kube/kube-config-eks

There are different ways of configuring .kube/config, but in case of problems with connection to the AWS cluster, [follow this one](https://aws.amazon.com/premiumsupport/knowledge-center/eks-api-server-unauthorized-error/).
For a template of the **aws-auth ConfigMap** to add to the cluster configuration for allowing other IMA users to access the cluster, follow the previous tutorial and use this file for configuring a the [ConfigMap](./1_CloudFormation/aws-auth-configmap.yaml)










