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

Create another instance on AWS 
- add port range 27017 with the app_instance public ip

## Install mongod
`wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -`
`echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`
`sudo apt-get update`
`sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20sudo mkdir -p /data/db`
`sudo chown -R mongodb:mongodb /var/lib/mongodb`
`sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mongod.conf`
`sudo systemctl enable mongod`
`sudo service mongod start`

## Default mongod.service
`sudo echo "server {
    listen 80;

    server_name _;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade \$http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host \$host;
        proxy_cache_bypass \$http_upgrade;
    }
}" | sudo tee /etc/nginx/sites-available/default``

