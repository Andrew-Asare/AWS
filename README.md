# AWS
## Two-tier architecture
![image](https://user-images.githubusercontent.com/26543682/116061106-65425900-a67a-11eb-9679-36dba1a0a4b9.png)
![image](https://user-images.githubusercontent.com/26543682/116061559-e994dc00-a67a-11eb-8885-4b4d15a64755.png)

## 2 Tier app deployment on AWS

## Ec2 instance for our nodeapp

## First iteration
- Launch an ec2 instance with correct version of ubuntu
- ssh into the instance
- update 
- upgrade
- install nginx 
- access nignx page with public IP
- share the IP in the chat

## Second iteration
- copy code from OS to AWS ECS app with scp command
- install required dependencies for nodejs
- launch the nodeapp with public ip

## Third iteration
- create an ec2 instance for db
- install mongodb with required dependencies
- allow access only from the app instance
- connect the app with db to fetch the data
- app to work with reverse proxy without 3000 port, fibu, /posts


# Linux commands

`scp -ri ~/.ssh/DevOpsStudent.pem ~/PycharmProjects/Virtual\ env/ ubuntu@18.202.166.214:/home/ubuntu` copying OS files to AWS ,use whatever ip is being used at the time. 
## dos2unixwget
`
 "http://ftp.de.debian.org/debian/pool/main/d/dos2unix/dos2unix_6.0.4-1_amd64.deb"sudo dpkg -i dos2unix_6.0.4-1_amd64.deb`

`dos2unix filename`
- used if the coppied file needs to be converted 
- 
