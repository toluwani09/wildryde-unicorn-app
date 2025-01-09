 # wildryde-unicorn-app
The WildRyde Unicorn Hailing App is a scalable web application hosted on AWS using EC2 instances, an Application Load Balancer, and Auto Scaling. Users can request a ride from a magical unicorn!
This project demonstrates key AWS services such as EC2, Application Load Balancer, Auto Scaling, and Amazon Machine Images (AMIs).

**Architecture**
Amazon EC2 Instances: The app was initially deployed on an EC2 instance. A custom AMI was created from the instance to scale the application horizontally.
Application Load Balancer: The ALB distributes incoming HTTP requests between EC2 instances, ensuring high availability.
Auto Scaling Group: The Auto Scaling group ensures that the number of EC2 instances automatically scales based on load, from a minimum of 2 to a maximum of 4 instances.
Security Groups: Properly configured inbound rules for HTTP, SSH, and TCP access, allowing all traffic from any IP address (0.0.0.0/0) for testing.
Git Integration: The application connects to a Git repository, pulling the latest code updates and deploying them automatically.

**Steps Taken**
**1. EC2 Instance Setup**
Launched a WildRydeWebServer EC2 instance.
Installed Apache on the EC2 instance, ensuring the web server was set up correctly.
Connected to the Git repository on the instance to retrieve the application code.
**2. Creating an AMI Image**
Created an AMI image named WildRydeWebServer2 from the original EC2 instance.
This image was used to launch additional instances to scale the application.
**3. Application Load Balancer Setup**
Created an Application Load Balancer (ALB) to distribute traffic across EC2 instances.
Configured the target group to include both the original EC2 instance and the new instances launched from the AMI.
The ALB DNS name was used to test the application, successfully distributing traffic to both instances.
**4. Auto Scaling Group Setup**
Created an Auto Scaling Group with the desired configuration to scale horizontally from 2 to 4 instances.
Used an existing launch template to automatically launch instances based on the custom AMI.
**5. Security Group Configuration**
Identified and resolved security group issues that caused initial timeouts. Configured proper inbound rules to allow HTTP (port 80), SSH (port 22), and TCP (port 443) traffic from all IPs (CIDR 0.0.0.0/0).
AWS Services Used
Amazon EC2: For running the web application and serving traffic.
Amazon AMI: To create reusable machine images for scaling.
Application Load Balancer (ALB): For distributing traffic across multiple EC2 instances.
Auto Scaling: To automatically scale the number of instances based on load.
Security Groups: To control traffic flow to EC2 instances.
Project Workflow
EC2 Instance Deployment: Launch the EC2 instance, configure Apache, and deploy the app.
Create AMI: Generate a custom AMI to use for scaling out.
Load Balancer: Set up the ALB to balance traffic across multiple EC2 instances.
Scaling Configuration: Configure the Auto Scaling Group to scale instances based on demand.
Security Configurations: Ensure the EC2 instances are properly secured and accessible.

**Demonstration**
**Application Access**
The WildRyde app can be accessed through the following Application Load Balancer DNS name:
http://WildRydeALB-1104021829.us-east-1.elb.amazonaws.com

_**Please note that this application might not be accessible at the time of accessing this file, as the web server may have been terminated due to cost-related reasons.**_

**Future Improvements**
CI/CD Pipeline: Implement a Continuous Integration/Continuous Deployment pipeline to automatically deploy updates to the application.
Database Integration: Integrate a relational database like Amazon RDS for user and ride data storage.
Auto Scaling Policies: Implement more advanced auto-scaling policies based on metrics like CPU utilization or request count.
HTTPS: Configure SSL/TLS for secure communication using Amazon ACM (AWS Certificate Manager).

**Conclusion**
This deployment provides a scalable and highly available infrastructure for the WildRyde unicorn hail-riding application, leveraging AWS services such as EC2, ALB, Auto Scaling, and security groups.
