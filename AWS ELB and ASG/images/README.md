# AWS ELB AND ASG
1. launch an EC2 instance
![ec2](1.PNG)
- in your Advance details paste the follwoing bash script in your user data
```
#!/bin/bash

# Variable Declaration
#PACKAGE="httpd wget unzip"
#SVC="httpd"
URL='https://www.tooplate.com/zip-templates/2098_health.zip'
ART_NAME='2098_health'
TEMPDIR="/tmp/webfiles"

yum --help &> /dev/null

if [ $? -eq 0 ]
then
# Set Variables for CentOS
PACKAGE="httpd wget unzip"
SVC="httpd"

echo "Running Setup on CentOS"
# Installing Dependencies
echo "########################################"
echo "Installing packages."
echo "########################################"
sudo yum install $PACKAGE -y > /dev/null
echo

# Start & Enable Service
echo "########################################"
echo "Start & Enable HTTPD Service"
echo "########################################"
sudo systemctl start $SVC
sudo systemctl enable $SVC
echo

# Creating Temp Directory
echo "########################################"
echo "Starting Artifact Deployment"
echo "########################################"
mkdir -p $TEMPDIR
cd $TEMPDIR
echo

wget $URL > /dev/null
unzip $ART_NAME.zip > /dev/null
sudo cp -r $ART_NAME/* /var/www/html/
echo

# Bounce Service
echo "########################################"
echo "Restarting HTTPD service"
echo "########################################"
systemctl restart $SVC
echo

# Clean Up
echo "########################################"
echo "Removing Temporary Files"
echo "########################################"
rm -rf $TEMPDIR
echo

sudo systemctl status $SVC
ls /var/www/html/

else
# Set Variables for Ubuntu
PACKAGE="apache2 wget unzip"
SVC="apache2"

echo "Running Setup on CentOS"
# Installing Dependencies
echo "########################################"
echo "Installing packages."
echo "########################################"
sudo apt update
sudo apt install $PACKAGE -y > /dev/null
echo

# Start & Enable Service
echo "########################################"
echo "Start & Enable HTTPD Service"
echo "########################################"
sudo systemctl start $SVC
sudo systemctl enable $SVC
echo

# Creating Temp Directory
echo "########################################"
echo "Starting Artifact Deployment"
echo "########################################"
mkdir -p $TEMPDIR
cd $TEMPDIR
echo

wget $URL > /dev/null
unzip $ART_NAME.zip > /dev/null
sudo cp -r $ART_NAME/* /var/www/html/
echo

# Bounce Service
echo "########################################"
echo "Restarting HTTPD service"
echo "########################################"
systemctl restart $SVC
echo

# Clean Up
echo "########################################"
echo "Removing Temporary Files"
echo "########################################"
rm -rf $TEMPDIR
echo

sudo systemctl status $SVC
ls /var/www/html/
fi 
```
- copy the public IP address and paste it on a bew browser and you will get something like this page.
![localhost](2.PNG)
2. Launch template
![template](3.PNG)
![template](4.PNG)
![template](5.PNG)
![template](6.PNG)
3. Create Target group
![targetgroup](7.PNG)
- Launch your ELB
![ELB](8.PNG)
![ELB](9.PNG)
![ELB](10.PNG)
3. create and Autoscalling group
![ASG](11.PNG)
![ASG](12.PNG)
![ASG](13.PNG)
![ASG](14.PNG)
![ASG](15.PNG)
![ASG](16.PNG)
![ASG](17.PNG)
![ASG](18.PNG)
# Congratulations

