### Protocol to install and start python3 with virtual environnement on an EC2-instance


**\# At the creation of your EC2 instance, launch this script**    

\#!/bin/bash  
sudo yum update -y  
sudo yum install python3 -y   


-----------------------------------------  

**\# Connect to you EC-2 instance**   
**\# launch those 4 command lines:**  
pip3 install --user virtualenv  
mkdir venv  
cd venv  
virtualenv -p /usr/bin/python3 python3  

**\# Activate the previously created env**  
source /home/ec2-user/venv/python3/bin/activate

**\# Install boto3 in our python environnement**  
pip install boto3

**\# Start python**  
python  


### With Ubuntu (ami-04b9e92b5572fa0d1)
As it is already install, you don't need to install python3
After the Update:  
sudo apt-get instal virtualenv  

then continue normally