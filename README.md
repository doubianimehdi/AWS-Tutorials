# AWS-Tutorials
This is repository is a knowledge base to help for AWS services

#Install R Server
1. Choose an amazon linux AMI and deploy it
2. Choose an instance type for the machine
3. Configure the instance details with the following script :

#!/bin/bash
#install R
yum install -y R

#install RStudio-Server 1.0.153 (2017-07-20)
wget https://download2.rstudio.org/rstudio-server-rhel-1.0.153-x86_64.rpm
yum install -y --nogpgcheck rstudio-server-rhel-1.0.153-x86_64.rpm
rm rstudio-server-rhel-1.0.153-x86_64.rpm

#install shiny and shiny-server (2017-08-25)
R -e "install.packages('shiny', repos='http://cran.rstudio.com/')"
wget https://download3.rstudio.org/centos5.9/x86_64/shiny-server-1.5.4.869-rh5-x86_64.rpm
yum install -y --nogpgcheck shiny-server-1.5.4.869-rh5-x86_64.rpm
rm shiny-server-1.5.4.869-rh5-x86_64.rpm

#add user(s)
useradd username
echo username:password | chpasswd 

4. Configuring the security group : For your R-based analysis environment, you have to open up port 8787 for RStudio Server and port 3838 for Shiny Server.
5. Accessing your machine : http://ec2-YOUR-IP.compute-1.amazonaws.com:8787
