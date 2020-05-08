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
- **Create IAM role** k8s assumes this role to create AWS resources
    - role name **AWSServiceRoleForAmazonEKS**
- **Create ssh key** to be able to ssh our EC2 instances
    - use the one from the previous course ./aws/rig_pluralsign.pep
- **Create Access key + secret** to enable authentication for API access
    - previously created


**Cluster Infrastructure** on eu-west-1

![EKS](img/eks3.png)

CloudFormation template uploading:
![EKS](img/eks5.png)


- Create the infrastructure using CloudFormation
    - upload file 1../eks-course-vpc.yaml
    - EKS-course-stack

- [install & configure](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)  **kubectl**. How it works
    - kubectl config file
        - EKS endpoint
        - User authentication
            - aws-iam-authenticator executable
            - generates an authentication token based on 
                - aws credentials file
    


Check the installed version of kubectl
    
    kubectl version --short --client

- Installing aws-iam-authenticator

- **Configuration file for kubectl**

        mkdir $HOME/.kube && nano $HOME/.kube/kube-config-eks











