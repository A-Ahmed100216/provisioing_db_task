# VM Provisioning Lab


## Introduction

The developers have indicated that they'll need a mongodb database soon. We need to create a provisioning script that will create this server.

Research the method for installing and configuring a MongoDB server on your server.

Write the steps in to the provisioning script.

Start the machine and run the tests.

## Pre-requisites
1. Vagrant
2. Git
3. Virtual Box

## Acceptance Criteria

* Uses vagrant file
* Create VM and Mongod is working
* MongoDB 3.2.20 is installed
* MongoDB to listen on 0.0.0.0 on port 27017
* Work with command "vagrant up"
* All tests passing
* Documentation exists as README.md file
* Documentation includes: Intro (purpose of repo), Pre Requisites and Instructions
* repo exists on GitHub

## Instructions
1. Clone starter code
2. Add the following commands to the provisioning file
```bash
sudo apt-get update
sudo apt-get install nginx -y
```
3. To install [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/), add the following commands to the provisioning file.
```bash
# Import the public key
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
# Create a list file for MongoDB
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
# Reload package database
sudo apt-get update
# Install MongoDB
sudo apt-get install -y mongodb-org
```
4. Inside the virtual machine, run the following commands to ensure the database is running correctly:
```bash
# Start MongoDB
sudo systemctl start mongod

# Check the status of MongoDB
sudo systemctl status mongod

# Enable MongoDB
sudo systemctl enable mongod
```

5. Run tests
```
cd tests
rake spec
```
All the tests except the version test should pass.
