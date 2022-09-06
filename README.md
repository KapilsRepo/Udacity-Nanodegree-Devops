# Udacity-Nanodegree-Devops
This repository is for the project submission for the Udacity Devops project. 

## High availability web app using CloudFormation
This deploys a webserver for a highly available web app using Cloudformation. For this we would
need a bespoke network as per the specification outlined by the Udacity.As per this project, there 
is a requirement to deploye an instagram like app named as udagram.Deployment begins with the networking 
components, followed by servers,security roles and software. 

### Description
Create a Launch Configuration in order to deploy four servers, two located in each of
your private subnets. The launch configuration will be used by an auto-scaling group. You'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, choose an Instance size and Machine Image (AMI) that best fits this spec. Be sure to allocate at least 10GB of disk space so that you don't run into issues.

### Architecture
Udacity - High Availability Website.png

### Files included:

- network.yml - CloudFormation network infrastructure stack description.
- network.json - Parameters file for the network infrastructure stack
- server.yml  - server configuration 
- server.json - parameter file for the server configuration

### Running the project:

1. Execute network infrastructure stack.

  C> aws cloudformation create-stack --stack-name udaNetwork --region us-east-1 --template-body file://network.yml --parameters file://network.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --profile gannu2
{
    "StackId": "arn:aws:cloudformation:us-east-1:404190891643:stack/udaNetwork/e16f4180-2e11-11ed-ad0f-0e87df064301"
}


2. Upon step 1 successful completion.

C> aws cloudformation create-stack --stack-name udaServers --region us-east-1 --template-body file://servers.yml --parameters file://servers.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --profile gannu2
{
    "StackId": "arn:aws:cloudformation:us-east-1:404190891643:stack/udaServers/e94e6a00-2e13-11ed-b59b-0a87db62bdd5"
}

### Output
http://udase-webap-43ykne3k2ey8-1945455030.us-east-1.elb.amazonaws.com/
