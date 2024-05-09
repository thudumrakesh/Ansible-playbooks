
<h1 align="center">Hi 👋, I'm Rakesh</h1>
<h3 align="center">A passionate AWS & DevOps Engineer from India</h3>
<(img align="right" alt="Coding" width="400" src="https://iconscout.com/lottie-animation/devops-8995909">

<p align="left"> <img src="https://komarev.com/ghpvc/?username=thudumrakesh&label=Profile%20views&color=0e75b6&style=flat" alt="thudumrakesh" /> </p>

<p align="left"> <a href="https://github.com/ryo-ma/github-profile-trophy"><img src="https://github-profile-trophy.vercel.app/?username=thudumrakesh" alt="thudumrakesh" /></a> </p>

- 🔭 I’m currently working on **DevOps Projects**

- 🌱 I’m currently learning **AWS & DevOps tools**

- 👯 I’m looking to collaborate on **DevOps Projects**

- 💬 Ask me about **AWS & DevOps tools**

- 📫 How to reach me **thudumrakesh68@gmail.com**

### Blogs posts
<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://dev.to/thudumrakesh/thudumrakesh" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/devto.svg" alt="thudumrakesh/thudumrakesh" height="30" width="40" /></a>
<a href="https://linkedin.com/in/www.linkedin.com/in/thudumrakeshh" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="www.linkedin.com/in/thudumrakeshh" height="30" width="40" /></a>
<a href="https://instagram.com/being_rakesh" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="being_rakesh" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://aws.amazon.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/> </a> <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a> <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a> <a href="https://www.jenkins.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/jenkins/jenkins-icon.svg" alt="jenkins" width="40" height="40"/> </a> <a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40"/> </a> <a href="https://www.linux.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a> <a href="https://www.selenium.dev" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/selenium-logo.svg" alt="selenium" width="40" height="40"/> </a> </p>

<p><img align="left" src="https://github-readme-stats.vercel.app/api/top-langs?username=thudumrakesh&show_icons=true&locale=en&layout=compact" alt="thudumrakesh" /></p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=thudumrakesh&show_icons=true&locale=en" alt="thudumrakesh" /></p>

<p><img align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=thudumrakesh&" alt="thudumrakesh" /></p>

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
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


 
