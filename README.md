# Publishing-S3-events-to-SNS-securely-using-Terraform

## Objective 

Create an S3 Bucket event to get SNS Email Notification on Object upload using Terraform

## Architectural Diagram

![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/97a2af47-ba50-4cb0-b1d5-310a99c0a5a7)

## Prerequisites

* AWS account with full administrative rights
* Terraform installed (Version 1.5 or higher recommended)
* A foundational understanding of AWS services and Terraform basics.

## Steps:

1. [Setting up Terraform Environment](https://github.com/aniwardhan/Host-a-static-website-in-S3-using-Terraform?tab=readme-ov-file#steps)
   
2. [Initialize your Terraform environment](https://github.com/aniwardhan/Host-a-static-website-in-S3-using-Terraform?tab=readme-ov-file#2-initialize-your-terraform-environment)

3. [Create a Variables file]().

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/4cbb1533-b840-47b9-b0ac-ae86c624b28b)

4. [Create S3 bucket]()

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/4c753c2b-71d1-46f9-82e4-306f0a20dcb0)

   Bucket Created

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/35ed3a35-f2b6-4ed1-96fb-0c81d88b28e3)


5. [Add SNS Notification to the bucket]()

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/a1eaf1f4-40a0-48ea-9c69-cbec50c672b6)

   SNS Topic Created and added to S3 Event Notification

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/732a687a-a847-4be7-a945-7ce61aae506d)


6. [Create SNS Topic]()

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/c9656c77-373e-45b0-9813-c63cc50220a7)

   Check the SNS Topic Creation

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/44555f21-608b-4e19-8f0b-9e044e439b2d)


7. [Add Policy to the SNS Topic]()

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/0bbf74cf-5ff0-4c8b-b3b5-6aaf03a9f2ca)

   Access Policy added

   ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/651d3a3c-ebfa-4d26-ba1e-3517deae1ae1)


8. [Add Subscription to the SNS Topic]()

    /* Do a manual Subscription*/
    
    When you do a terraform apply, an initial webhook event would be sent to your subscriber to confirm that email address's subscription for your topic. You will be able to see your email subscriber under Subscriptions tab in your AWS console. 
    Till you confirm your subscription it would be marked as Pending, once you confirm it, it will be marked as Confirmed and you will events events as emails at your email subscriber. 

    ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/20224df1-f991-4180-a21e-acc5aaa16401)

    Subcriptions added and manually confirmed

    ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/c659d848-7c24-48ee-83fd-728b13d4ce2e)

9. [Optionally you can encrypt your message using KMS key]()

    ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/3a38774a-3cae-42f0-9efb-a1ac48257885)

10. Finally upload an object to check the output

    ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/b19e3949-5f7a-4dd6-b6fb-de6081e61ba8)

    Received Email Notification

    ![image](https://github.com/aniwardhan/Publishing-S3-events-to-SNS-securely-using-Terraform/assets/80623694/c7c03cec-979d-4451-9d00-1207ccb55a1c)

11. Destroy all resource created

    ```hcl
    terraform destroy -auto-approve
    ```


