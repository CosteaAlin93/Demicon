<details><summary> 1). Create Basic AWS Infrastructure. </summary>
<br>
  
> Already had some written from a Udemy Course

![image](https://user-images.githubusercontent.com/86648102/151950761-d5ff46c3-a06b-423e-b96c-c2a79278bb0c.png)

- Add resources for the AWS App Load Balancer to work: aws_lb, aws_lb_listener, aws_lb_target_group, aws_lb_target_group_attachment (2 attachments, for the 2 EC2 instances launched)
- Configure the instances to be reachable on port 80, so the aws_lb can reach them; did this with an Ansible Playbook, which installs Apache and makes sure that it is started and anabled

![image](https://user-images.githubusercontent.com/86648102/151953150-af93921b-74ed-4a71-8e5a-addb85116b04.png)

- Created an output value "lb_dns" that shows the **dns_name** of the lb once it's creation is completed.

![image](https://user-images.githubusercontent.com/86648102/151953519-b1cde379-bde2-4bd7-9d61-2f07f2f650cc.png)

- Targets are now shown as healthy.

![image](https://user-images.githubusercontent.com/86648102/151953727-8e844d7c-fe5e-4e36-a0a9-0ee8af696032.png)

- Also, the aws_lb dns_name is working and the Apache2 default page is loading.

![image](https://user-images.githubusercontent.com/86648102/151953812-700ae39a-3d49-44a2-aee0-fc2743118ad9.png)

<br>
</details>

<details><summary> 2). Get the **terraform.tfstate** available into an S3 bucket.  </summary>

  For this, I`ve added the terraform block **backend** which changed the default **local-backend** to a **remote-backend** into an S3 bucket, with enabled versioning and a DynamoDB resource where we can store the lock state. Running a **terraform init** will make our local state to be migrated to the remote S3 backend.
  
  ![image](https://user-images.githubusercontent.com/86648102/151958148-cba0eeb1-c77c-45cd-9408-054f968b7d8f.png)

  ![image](https://user-images.githubusercontent.com/86648102/151959643-faa2cc76-44cc-4397-bc64-dab3745e16a7.png)

  
<br>
  
<br>
</details>

<details><summary> 3). Lambda script.  </summary>
  
   This is the part I didn't manage to make. I need to work on my Python or NodeJS skills.
 
  <br>
</details>



<details><summary> 4). Manage it with Couldformation.  </summary>
<br> 
  
  For this, we make a Cloudformation template, in which we add a lambda function as a resource. 
  
  ![image](https://user-images.githubusercontent.com/86648102/152105819-d5b424fd-822a-422d-9e02-675179e6b930.png)

  '''
  ---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'Lambda Function Demicon'

Resources:
  Lambda1:
    Type: "AWS::Lambda::Function"
    DeletionPolicy: Retain
    Properties: 
        Code:
            ZipFile: >
                def lambda_handler(event, context):   
                return 'Hello from Lambda'
        Description: Test with Cloud Formation
        FunctionName: test_lambda_function
        Handler: lambda_function.lambda_handler
        Role: arn:aws:iam::337595255177:role/service-role/S3AccessRole
        Runtime: python3.9
  '''
 
  <br>
</details>

