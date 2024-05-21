# Publishing-S3-events-to-SNS-securely-using-Terraform

## Objective 

Create an S3 Bucket event to get SNS Email Notification on Object upload using Terraform

## Architectural Diagram

![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/d9187f7a-e2e5-432e-b8a2-0c476368e469)

## Prerequisites

* AWS account with full administrative rights
* Terraform installed (Version 1.5 or higher recommended)
* A foundational understanding of AWS services and Terraform basics.

## Steps:

## 1. [Setting up Terraform Environment](https://github.com/AnithaPadmanaban04/Getting-Started-with-Terraform.git)

Install Terraform and the AWS Command Line Interface (CLI) on your local machine. Configure your AWS credentials by running aws configure and provide your AWS access key and secret key. Check this [link](https://github.com/AnithaPadmanaban04/Getting-Started-with-Terraform.git) to configure Terraform and AWS CLI

Create a working directory in your local machine and open the folder in MS Visual Code Editor to start the project

## 2. [Initialize your Terraform environment](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/provider.tf)

A provider in Terraform is a plugin that enables interaction with an API. This includes Cloud providers and Software-as-a-service providers.

The providers are specified in the Terraform configuration code. They tell Terraform which services it needs to interact with.

Provider configurations should be declared in the root module of your Terraform project.

Create a file named [providers.tf](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/provider.tf) to configure the specific cloud providers or services that your Terraform configuration will interact with.

## 3. [Create a Variables file](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/variables.tf).

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/42e6742e-53ff-42a4-a0b5-88f09313f816)

## 4. [Create S3 bucket](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/s3.tf)

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/b98c108e-5643-4e98-a39b-1e499b08e9c0)

   Bucket Created

 ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/89773098-c1d1-4fe5-90e4-f79818013909)

## 5. [Add SNS Notification to the bucket](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/s3.tf)

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/bf904074-f543-4e74-a0d8-da914e0c58e6)

   SNS Topic Created and added to S3 Event Notification

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/2795f274-3488-4bc2-8ec2-d06e0dd6f635)


## 6. [Create SNS Topic](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/sns.tf)

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/a032dafc-4528-4e93-b5a9-c8e687b628ed)

   Check the SNS Topic Creation

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/7a6ee248-85ef-43a3-b9cd-bd6d335b5ee5)

## 7. [Add Policy to the SNS Topic](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/sns.tf)

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/b9d323b9-2f80-4afa-b6af-698c173d71b0)

   Access Policy added

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/83b50c08-67c0-47de-aa55-89f3d7c3f726)


## 8. [Add Subscription to the SNS Topic](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/sns.tf)
      
      /* Do a manual Subscription*/
    
   When you do a terraform apply, an initial webhook event would be sent to your subscriber to confirm that email address's subscription for your topic. You will be able to see your email subscriber under 
   Subscriptions tab in your AWS console. 
   Till you confirm your subscription it would be marked as Pending, once you confirm it, it will be marked as Confirmed and you will events events as emails at your email subscriber. 

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/9c55cfa6-4960-4986-98b8-1f945d743577)

   Subcriptions added and manually confirmed

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/bcb03224-7030-4014-a575-dc5af3208d64)

## 9. [Optionally you can encrypt your message using KMS key](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/blob/main/kms.tf)

  ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/5d3676ee-9466-4087-9100-7f9cd6310909)

## 10. Finally upload an object to check the output

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/3a5066bb-cf58-480c-bf98-04bb57323ac9)

   Received Email Notification

   ![image](https://github.com/AnithaPadmanaban04/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/170385807/82e655f4-008b-4ced-8bfd-16c01da127b6)

## 11. Destroy all resource created

   ```hcl
    terraform destroy -auto-approve
   ```


