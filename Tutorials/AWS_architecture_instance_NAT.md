## Tutorial to configurate a network with a private network and a NAT instance on AWS

![Architecture](https://github.com/Cyril-Basquin/AWS/blob/master/Tutorials/Images/VPC_with_NAT_instance_JumpBox_FI.png)


### VPC Architecture
  + 1 VPC
  + 2 Subnet
      + 1 Private
      + 1 Public
  + 2 Route Table (1 for each subnet)
  + 1 Internet Gateway (Attached to the Public Route Table)


### EC2 instance (& NAT instance)
**Create 2 "basic" EC2 instance (ex: ami-00068cd7555f543d5)**  
+ 1 instance in the *Public subnet* with an IP  
+ 1 instance in the *Private subnet* (no IP)  

**Create 1 NAT-instance using an existing AMI (ex: ami-00a9d4a05375b2763)**  
+ In the *Public subnet* with an IP  

Note: for the NAT-instance, select it then actions => Networking => Change source/dest check => Disable


### Security Group
The three security groups (one for each instance) have to be configure according to the schema:  
**Jump-box have to:**
  - receive ssh from internet Gateway (SSH, port 22, 0.0.0.0/0)
  - send ssh to the jump box (SSH, port 22, FI IP: 10.0.11.xxx/32 or FI_SG)


**Final Instance have to:**
  - receive ssh from the jump-box (SSH, port 22, JB IP: 10.0.1.xxx/32 or JB_SG)
  - send http/https request to the NAT instances (HTTP, port 80, ???)


**NAT instance have to:**
  - receive http/https request from the FI (HTTPS, port 443, ???)
  - send http/https request through the Internet Gateway (HTTPS, port 443, 0.0.0.0/0)


Note: When you access to the FI, you are connected to it through the jump-box. If you deactivate the Jump-box, you lose the connection with the FI.

### Access to the Final Instance
**Transfer the access key to the Jump-Box**  
Note: xxx.xxx.xxx.xxx is the (elastic)IP of your EC2  
Note: you can use the full path _c:\Users\Username\your\path_  
or go in the folder where the key is and use the local path

``scp -i key.pem key.pem ec2-user@xxx.xxx.xxx.xxx:key.pem``



**Connection to the Jump-Box**  
``ssh -i key.pem ec2-user@xxx.xxx.xxx.xxx``


**In the Jump-Box, allow readability only of the key**  
``chmod 400 key.pem``


**Connection to the Final instance (from the JB)**  
``ssh -i /home/ec2-user/.ssh/id_rsa/AWS_key_pair.pem ec2-user@10.10.11.35``
