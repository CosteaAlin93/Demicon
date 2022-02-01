<details><summary>
  
- Create Basic AWS Infrastructure

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

<details><summary>
  
- Create Basic AWS Infrastructure

<br>
  
<br>
</details>
