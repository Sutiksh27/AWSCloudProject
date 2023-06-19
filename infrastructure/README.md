# infrastructure
This repository contains all the infrastructure as code(Cloudformation templates).

## AWS CLI Commands
* Creating a stack 
```
aws cloudformation create-stack --stack-name mystack1 --template-body file://csye6225-infra.yml --parameters ParameterKey=VPCName,ParameterValue=VPC ParameterKey=VPCCIDRBlock,ParameterValue=10.0.0.0/16 ParameterKey=AMIId,ParameterValue=ami-09da6a1180af4c5bc ParameterKey=EnvType,ParameterValue=prod ParameterKey=DNSDomain,ParameterValue=prod.sutiksh27.me. ParameterKey=CodeDeployS3Bucket,ParameterValue=csye6225-codedeploy-sutiksh27-prod ParameterKey=LambdaS3Bucket,ParameterValue=csye6225-lambda-sutiksh27-prod ParameterKey=CertificateArn,ParameterValue=arn:aws:acm:us-east-1:605025718575:certificate/1bdf5744-796f-4953-8b1b-0d1e120310d7 --capabilities CAPABILITY_NAMED_IAM
```
* Updating a stack
```
aws cloudformation update-stack --stack-name mystack1 --template-body file://csye6225-infra.yml --parameters ParameterKey=VPCName,ParameterValue=VPC ParameterKey=VPCCIDRBlock,ParameterValue=10.0.0.0/16 ParameterKey=AMIId,ParameterValue=ami-09da6a1180af4c5bc ParameterKey=EnvType,ParameterValue=prod ParameterKey=DNSDomain,ParameterValue=prod.sutiksh27.me. ParameterKey=CodeDeployS3Bucket,ParameterValue=csye6225-codedeploy-sutiksh27-prod ParameterKey=LambdaS3Bucket,ParameterValue=csye6225-lambda-sutiksh27-prod ParameterKey=CertificateArn,ParameterValue=arn:aws:acm:us-east-1:605025718575:certificate/1bdf5744-796f-4953-8b1b-0d1e120310d7 --capabilities CAPABILITY_NAMED_IAM
```

* Creating a new stack with different parameters
```
aws cloudformation create-stack --stack-name mystack1 --template-body file://csye6225-infra.yml --parameters ParameterKey=VPCName,ParameterValue=VPC ParameterKey=VPCCIDRBlock,ParameterValue=10.0.0.0/16 ParameterKey=AMIId,ParameterValue=ami-08ae2ba64fc1f9464 ParameterKey=EnvType,ParameterValue=prod ParameterKey=DNSDomain,ParameterValue=prod.sutiksh27.me. ParameterKey=CodeDeployS3Bucket,ParameterValue=csye6225-codedeploy-sutiksh27 ParameterKey=CertificateArn,ParameterValue=arn:aws:acm:us-east-1:605025718575:certificate/1bdf5744-796f-4953-8b1b-0d1e120310d7 --capabilities CAPABILITY_NAMED_IAM
```
* Deleting a stack
```
aws cloudformation delete-stack --stack-name mystack1
```
* Creating policies for ghactions-app
```
aws cloudformation create-stack --stack-name policystack --template-body file://csye6225-policy.yml --parameters ParameterKey=CodeDeployS3Bucket,ParameterValue=csye6225-codedeploy-sutiksh27-prod --capabilities CAPABILITY_NAMED_IAM
```

* Updating policies for ghactions-app
```
aws cloudformation update-stack --stack-name policystack --template-body file://csye6225-policy.yml --parameters ParameterKey=CodeDeployS3Bucket,ParameterValue=csye6225-codedeploy-sutiksh27-prod --capabilities CAPABILITY_NAMED_IAM
```

* Deleting policies for ghactions-app
```
aws cloudformation delete-stack --stack-name policystack
```

* Command to import certificate to aws certificate manager
```
aws acm import-certificate --private-key fileb:///Users/jasonpauldarivemula/Downloads/prod-ca/pk.pem --certificate fileb:///Users/jasonpauldarivemula/Downloads/prod-ca/prod_sutiksh27_me.pem --certificate-chain fileb:///Users/jasonpauldarivemula/Downloads/prod-ca/prod_sutiksh27_me.ca-bundle.pem
```
