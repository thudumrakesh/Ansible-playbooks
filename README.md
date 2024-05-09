MANUAL METHOD WE MENTION ALL THE CONFIDENTIAL CREDENTIALS LIKE AWS ACCESS KEYS AND AWS SECRET KEY IN THE MAIN FILE AND ALLOW ANSIBLE TO CREATE THE RESOURCES
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Launch the ec2 instance with the given bellow requirements
Connect the instance with the git bash and after that install the ansible with the below command and check version.
Install python library with command <sudo pip3 install boto3 botocore>.
Now copy the pem file to remote server through command <scp -I ansible.pem ansible.pem ec2-user@IP:~>. And  change permissions with command <sudo chmod 400 ansible.pem>.
Now open the inventory file in path <cd /etc/ansible>, <vi hosts>
In hosts file edit as below
[localhost]
ansible ansible_hosts=IP ansible_python_interpertoer=/usr/bin/python3 ansible_ssh_private_key_file+/home/ec2-user/ansible.pem
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	Now creating ansible-playbooks without variables
After that create a wanted resource
1.	VPC
2.	INTERNETGATEWAY
3.	PUBLIC SUBNET
4.	PRIVATE SUBNET
5.	PUBLIC ROUTE TABLE 
6.	PRIVATE ROUTE TABLE
7.	SECURITY GROUP
8.	EC2 INSTANCE
9.	USER DATA FOR HOSTING APPLICATION
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------   
 Give the user data for application hosting
 #!/bin/bash
 sudo yum -y install git httpd
 sudo git clone <URL>
 sudo systemctl start httpd
sudo systemctl status httpd
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
CREATING INFRASTRUCTURE USING INLINE VARIABLES METHOD
Create new file [inline-main.yaml] and write the script using variables in the same script.
We do not need to mention the credentials at each and every resource.
Instead we can use variables and string them.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

CREATING INFRASTRUCTURE USING OUTLINE VARIABLES METHOD
Create a new file [outline-main.yaml] and write the script to create the resources
This method is similar to inline method, the only difference is that we mention the variables and its values in a different file and we mention the path of the variables file in the main file so that it can exactly string them script to create vpc & internet gateway.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -
      
TO DESTROY RESOURCES:
WRITE A SEPARATE SCRIPT [DESTROY.YAML] TO DESTROY THE RESOURCES THAT HAVE BEEN CREATED.
TO DESTROY EC2, SECURITY GROUP, PRIVATE & PUBLIC ROUTE TABLE.
AFTER THE SCRIPT IS DONE, MENTION THE APPROPRIATE ID’s OF THE RESOURCES AND APPLY THE PLAYBOOK

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
COMMANDS USED:
Playbook execution:<ansible-playbook playbook.yml>
Specifying inventory file:<ansible-playbook -i inventory_file playbook.yml>
Syntax check:ansible-playbook --syntax-check playbook.yml
Encrypting a file with Ansible Vault:ansible-vault encrypt filename
Decrypting a file with Ansible Vault:ansible-vault decrypt filename
Edit an encrypted file with Ansible Vault:ansible-vault edit filename
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
![image](https://github.com/thudumrakesh/Ansible-playbooks/assets/144659414/fddb1ec3-2bb5-4b77-b10c-809fab5edabb)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
![image](https://github.com/thudumrakesh/Ansible-playbooks/assets/144659414/6452b956-d436-4faf-9a24-35f1fd454479)


 
