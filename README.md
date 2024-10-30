# Automating-Infrasturcture-Deployment-With-CloudFormation

This project demonstrates my ability to deploy multiple layers of infrastructure with AWS CloudFormation, update a CloudFormation stack and delete a stack (while retaining some resources).
I leveraged AWS CloudFormation to:

i.	deploy a virtual private cloud (VPC) networking layer

ii.	deploy an application layer that references the networking layer

iii.	explore templates with AWS CloudFormation Designer

iv.	delete a stack that has a deletion policy


Task1: Deploying A Networking Layer

1.	Created stack in CloudFormation Service in the AWS management console
   
•	Specified a template

![image](https://github.com/user-attachments/assets/839b9726-b15f-4a98-975b-86a6a8d28afc)


•	I uploaded my YAML template named “lab-network.yaml”

![image](https://github.com/user-attachments/assets/5619ae77-6f86-439f-987b-d48dbb42a942)




2.	Created a stack
   
•	Stack name: lab-network

![image](https://github.com/user-attachments/assets/6d770371-aa89-4ece-a577-7d5d202194d6)


4.	Configured Stack options
   
•	In the Tags section, I entered these values:

Key: Application

Value: Inventory

![image](https://github.com/user-attachments/assets/0e209a9a-59a4-4406-b1d2-16a763607286)

 

4.	I reviewed, clicked submit and waited for the creation to complete.
   
![image](https://github.com/user-attachments/assets/2f47c465-5f0c-4c19-82d5-9ada0a555101)



Task 2: Deploying an application layer

•	Created an EC2 instance and a security group

1.	Specified and uploaded a new template file
   
![image](https://github.com/user-attachments/assets/8f0016a4-34df-434f-8dd6-838aeb126182)

                 
3.	Created a stack

Stack name: lab-application

NetworkStackName: lab-network

![image](https://github.com/user-attachments/assets/c7030ae4-91fe-4248-9c2d-c6b1e1664d58)


3.	Configured Stack Options

•	In the Tags section, I entered the following values

Key: application

Value: inventory

![image](https://github.com/user-attachments/assets/31a36d73-0454-4935-9a3d-2b08a7d7a269)


4.	Reviewed and Created the new stack

![image](https://github.com/user-attachments/assets/9bdfc4fa-8c65-48fb-be7e-757499f69fec)


5.	I copied the URL form the output tab and pasted it a new browser tab.

![image](https://github.com/user-attachments/assets/8f0cb616-1ea8-4d85-90c7-c90f1044b2b9)


6.	The link opens the application which is running on the web server that this new CloudFormation stack created.

![image](https://github.com/user-attachments/assets/d7d3133d-7403-4e66-a39c-4563127e13fa)



Task 3: Updating the lab-application stack to modify a setting in the security group

i.	I navigated to EC2 services and selected security groups to check the current settings of the WebServerSecurityGroup.

ii.	I selected the inbound tap and this had only one rule

-	The rule permitted HTTP traffic 

![image](https://github.com/user-attachments/assets/1ce2a04d-f41d-4e3b-a0ea-5fa273540811)


iii.	I navigated back to the CloudFormation page to modify the lab-application template.

iv.	The new template had an additional configuration to permit inbound SSH traffic on port 22.

![image](https://github.com/user-attachments/assets/bdffab3b-5d6b-4e0e-9c72-902d4e7cf5e6)

 

v.	In the stacks, I selected the lab-application and clicked on the update tab

![image](https://github.com/user-attachments/assets/7f23977f-1053-4ff8-b820-d4cd17630116)


vi.	I uploaded the new file

![image](https://github.com/user-attachments/assets/6b8b5485-5272-43b6-b9dd-c25081bcf0f4)


vii.	I left everything as it was, submitted the new file and waited for the update to complete.

![image](https://github.com/user-attachments/assets/f18b64f0-d6e5-4a97-a73f-d855b54eb27b)


viii.	I navigated back to the Webserver security group to verify that an additional inbound rule has been added.

![image](https://github.com/user-attachments/assets/ef7d1f94-917e-41d8-b1d3-376bc04c7298)

Conclusion

•	This demonstration shows how changes can be deployed in a repeatable, documented process.

•	The AWS CloudFormation templates can be stored in a source code repository (such as AWS CodeCommit).

•	Versions and history of the templates and the infrastructure that was deployed can be maintained.
  


Task 4: Exploring templates with AWS CloudFormation Designer

i.	I navigated to the designer section of CloudFormation

ii. I uploaded the second lab-application file to show the interrelationship between the templates resources.

![image](https://github.com/user-attachments/assets/dd60f1c1-4318-4795-a3cb-5d4575990ba9)



               
 






