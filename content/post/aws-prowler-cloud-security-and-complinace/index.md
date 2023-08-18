---
title: AWS PROWLER - Cloud Security and Complinace
subtitle: AWS PROWLER - Cloud Security and Complinace
date: 2023-08-18T14:46:50.027Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
# Prowler

There are number of ways to install AWS Prowler, for this exercise we can make use of the latest version of python and pip which can be installed from the link : Download Python | Python.org

While installing python we need to make sure that the correct version is downloaded, during the set up I accidentally downloaded the embedded version  . We can also add python to the environment variables in windows by following the link: How to add Python to Windows PATH? - GeeksforGeeks.

We need to add two roles to the user account for Prowler to run as shown below:

```arn:aws:iam::aws:policy/SecurityAudit
arn:aws:iam::aws:policy/job-function/ViewOnlyAccess```

<!-- 
 Moreover, some read-only additional permissions are needed for several checks, 
make sure you attach also the custom policy prowler-additions-policy.json to the role you are using. 
If you want Prowler to send findings to AWS Security Hub, make sure you also attach the custom policy 
prowler-security-hub.json. -->

Following the AWS Prowler Github page we can install prowler by running the command:

```pip install prowler
prowler -v```

If this doesn’t work or if python is not installed in the path then we need to run the command:

```py -m pip install prowler```

Once the installation is done we can run prowler by using the command 

```py -m prowler aws ```

## Resources to optimize and learn about prowler : 

[Optimizing Prowler](About Optimizing for Speed: How to do complete AWS Security&Compliance Scans in 5 minutes | tecRacer Amazon AWS Blog)

[Prowler Appsec](Continuous Compliance Audits against AWS CIS Foundations Benchmark | by Sunesh Govindaraj | Appsecco)

```py -m pip show prowler
To check where prowler is installed```

This link has useful resources to format and use logs from prowler, we can use different flags to include and exclude certain checks in Prowler and output the logs as JSON  : 

[Flags and resources to run prowler] (GitHub - mberger/aws-cis-security-benchmark: Tool based on AWS-CLI commands for AWS account hardening, following guidelines of the CIS Amazon Web Services Foundations Benchmark (https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf))

## To List Complaince Standards

```py -m prowler aws --list-compliance```
```prowler <provider> --compliance <compliance_framework>
With this we can run prowler only for a given complinace framework from the list of compliances available```

## Listing all the services required for prowler to run

```py -m prowler aws --list-services
Here aws can be swapped with gcp or azure```

## Policies required for Prowler to run

arn:aws:iam::aws:policy/SecurityAudit

[Security Audit Role](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/SecurityAudit.html)

[View only access](arn:aws:iam::aws:policy/job-function/ViewOnlyAccess)

## Drawbacks of Prowler:

The filter option in the webpage is very slow !, it takes about a minute to open due to the size of the file, since there are about 18k findings, a workaround could be to store the data in an S3 bucket and use AWS Athena to query or use quicksight to create the dashboards !

By default Prowler will scan all the regions !, hence we can specify the commands: 

```prowler aws --profile custom-profile -f us-east-1 eu-south-2```

## Integrating Prowler into Quicksight:

Under the integrations tab, search for AWS Prowler and then enable the ingestion. Once this is done we have a special command on the console to run Prowler which can send the findings as “asff“ format which can be recognized by Security Hub. 

Command to ingest the logs  into Security Hub. 

-S : Security Hub

-M: Output format

```py -m prowler aws --compliance cis_1.4_aws -M json-asff -S```

To send only failed findings into Security Hub we can use the -f option:

```prowler -S -q```

By default, Prowler archives all its findings in Security Hub that have not appeared in the last scan. You can skip this logic by using the option --skip-sh-update so Prowler will not archive older findings:

```prowler -S --skip-sh-update```

## Working with Docker image of Prowler

We were able to get the docker image and run the same on our local environment as shown below. 

Go to DockerHub and find the official image for prowler as given below

```docker run -ti --rm -v "Input your local directory -> Copy as path option in windows" \
--name prowler \
--env AWS_ACCESS_KEY_ID=“Input your access key” \
--env AWS_SECRET_ACCESS_KEY=”Input your secret key” \
--env AWS_SESSION_TOKEN =”Input your sessions token” toniblyx/prowler:latest```

## Running Prowler on ECR using Lambda function:


Open ECR in AWS console and create a repository, then tag your docker image and push it to the repository by following the instructions in the console. 

Once the image is pushed to ECR, create a lambda function and choose “Container image“ and add your new container that is created from the ECR console .



## Automating Prowler using CDK 

https://docs.aws.amazon.com/cdk/v2/guide/ecs_example.html


```from aws_cdk import (aws_ec2 as ec2, aws_ecs as ecs,
                     aws_ecs_patterns as ecs_patterns,
                     aws_ecs_patterns,
                     aws_iam as iam,
                     aws_ecr as ecr)
from aws_cdk import (
    # Duration,
    Stack,
    # aws_sqs as sqs,
)
from constructs import Construct

class MyEcsConstructStack(Stack):

    def __init__(self, scope: Construct, construct_id: str, **kwargs) -> None:
        super().__init__(scope, construct_id, **kwargs)
        ecr_repository = ecr.Repository.from_repository_attributes(
            self,
            "ECRRepository",
            repository_name="prowler",
            # Run a command to get the arn of  https://awscli.amazonaws.com/v2/documentation/api/latest/reference/ecr/describe-repositories.html
            repository_arn="arn:aws:ecr:us-east-1:AccountId:repository/prowler"
            
            
            # repository_uri="AccountId.dkr.ecr.us-east-1.amazonaws.com/prowler:latest",
        )
        # The code that defines your stack goes here

        # example resource
        # queue = sqs.Queue(
        #     self, "MyEcsConstructQueue",
        #     visibility_timeout=Duration.seconds(300),
        # )
        vpc = ec2.Vpc(self, "MyVpc", max_azs=2)     # default is all AZs in region

        existing_task_role_arn = "arn:aws:iam::AccountId:role/ecsTaskExecutionRole"
        existing_execution_role_arn = "arn:aws:iam::AccountId:role/ecsTaskExecutionRole"

        # Define a task role using the provided ARN
        task_role = iam.Role.from_role_arn(
            self,
            "ExistingTaskRole",
            role_arn=existing_task_role_arn,
        )
        # ecr_repository.grant_pull(task_role) 
        # Define a task execution role using the provided ARN
        execution_role = iam.Role.from_role_arn(
            self,
            "ExistingExecutionRole",
            role_arn=existing_execution_role_arn,
        )


        cluster = ecs.Cluster(self, "MyCluster", vpc=vpc)

        ecs_patterns.ApplicationLoadBalancedFargateService(self, "MyFargateService",
            cluster=cluster,            # Required
            cpu=512,                    # Default is 256
            desired_count=1,            # Default is 1
            task_image_options=ecs_patterns.ApplicationLoadBalancedTaskImageOptions(
            image=ecs.ContainerImage.from_ecr_repository(repository= ecr_repository, tag="latest"),
            task_role=task_role,  # Assign the existing task role
            execution_role=execution_role,  # Assign the existing execution role
            container_name="prowler"
            ),

            memory_limit_mib=2048,      # Default is 512
            public_load_balancer=True)  # Default is True

# pull image from artifactory -> ```


## Creating a Dockerfile to run Prowler:

```
FROM python:3.11-buster

COPY ./requirements.txt /requirements.txt

RUN --mount=type=secret,id=pip-index-url \
           PIP_INDEX_URL="$(cat /run/secrets/pip-index-url)" pip install --no-cache-dir -r requirements.txt

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
           && unzip awscliv2.zip \
           && ./aws/install
```


## Creating a Jenkins File to push pull prowler and run on Kubernetes Cluster: 

```@Library('') _
import 

pipeline {
   agent {
      kubernetes {
         yaml utility.devopsPodYaml(containers: [[imageName: '/python3-prowler:latest',
                                                  containerName: 'prowler',
                                                  repository: 'jfrog repo',
                                                  resources: [requests: [cpu: '2000m', memory: '1000Mi'], limits: [cpu: '4000m', memory: '2000Mi']],
                                                  ]]
                                                  )
      }
   }
   options { buildDiscarder(logRotator(numToKeepStr: '10'))
   disableConcurrentBuilds() 
   timeout(time: 3, unit: 'HOURS')
   }
   
   //  Pipeline with stages, pipeline can create multiple stages based on the Parameters (AWS Account Id's)

   stages {
      stage('Use Docker Image') {
         steps {
            script {
               container('prowler') {
                  // Execute steps inside the '/my-awesome-image' container
                  // Wrap the function calls for AWS credentials
                  // def assumedRole=new Role(roleName: '')
                  //awsFunctions.withTemporaryCredentials(AWSAccount.ROOT.accountID, 'iot-cloud-aws-jenkins-cdk-diff',  "arn:aws:iam::${AWSAccount.ROOT.accountID}:role/jenkins-cdk-diff") {
                   awsFunctions.withTemporaryCredentials(AWSAccount.ROOT.accountID, 'iot-cloud-aws-jenkins-cdk-diff', new Role(roleName: 'jenkins-cdk-diff')) {
                  // Use SH command and run the script
                  sh(label: 'run prowler', script: """
                  prowler aws --role arn:aws:iam::AccountId:role/test-role-prowler --compliance aws_audit_manager_control_tower_guardrails_aws                   
                  """)   
                  }
               }
            }
         }
      }
   }
}
```

## Creating a new Role Using AWS CDK for Prowler to run 


```from .Companyad import CompanyAD
from ..policies import ENFORCE_DYNAMODB_VIEW_ONLY_POLICY


import aws_cdk
from aws_cdk import (
    aws_iam as iam
)

class CompanyAD_SecOps(CompanyAD):
    def __init__(
        self,
        stack,
        sso_principal):
        super().__init__(
            stack=stack,
            sso_principal=sso_principal,
            managed_policies=[

                iam.ManagedPolicy.from_aws_managed_policy_name("job-function/ViewOnlyAccess"),
                iam.ManagedPolicy.from_aws_managed_policy_name("SecurityAudit")
            ],
            inline_policies={
                # adding new custom prowler policy for prowler from the below function 
               **ENFORCE_DYNAMODB_VIEW_ONLY_POLICY,
               **PROWLER_ADDITIONS_POLICY 
            },
            max_session_duration=aws_cdk.Duration.hours(3)
        )

PROWLER_ADDITIONS_POLICY = {
    "prowler-additions-policy": iam.PolicyDocument(
        statements=[
            iam.PolicyStatement(
                effect=iam.Effect.ALLOW,
                actions=[
                    "account:Get*",
                    "appstream:Describe*",
                    "appstream:List*",
                    "backup:List*",
                    "cloudtrail:GetInsightSelectors",
                    "codeartifact:List*",
                    "codebuild:BatchGet*",
                    "drs:Describe*",
                    "ds:Get*",
                    "ds:Describe*",
                    "ds:List*",
                    "ec2:GetEbsEncryptionByDefault",
                    "ecr:Describe*",
                    "ecr:GetRegistryScanningConfiguration",
                    "elasticfilesystem:DescribeBackupPolicy",
                    "glue:GetConnections",
                    "glue:GetSecurityConfiguration*",
                    "glue:SearchTables",
                    "lambda:GetFunction*",
                    "logs:FilterLogEvents",
                    "macie2:GetMacieSession",
                    "s3:GetAccountPublicAccessBlock",
                    "shield:DescribeProtection",
                    "shield:GetSubscriptionState",
                    "securityhub:BatchImportFindings",
                    "securityhub:GetFindings",
                    "ssm:GetDocument",
                    "ssm-incidents:List*",
                    "support:Describe*",
                    "tag:GetTagKeys",
                    "wellarchitected:List*"
                    ],
                resources=["*"],
            )
        ]
    )
}

```

### Add the role to the stack so that it can be accessed in our AD.

```     # === Sec_Ops Team Permission Sets
        sec_ops = Company_SecOps(self, sso_principal)
```