# nod-jenkins
a node-jenkis project  running it on a jenkins server
STEPS TO BUILD A DOCKER FILE USING JENKINS
Now go to manage Jenkins go to plugins 

-Click on available plugins

-Search for nodejs and install

-Go to tools and search nodes installation and add node (in the textbox)

And save



NOW TO CONFIGURE YOUR DOCKER-HUB CREDENTIALS IN JENKINS



-now go back to manage Jenkins and search for credentials

-click on global

-add credentials

Look for the username and password drop down and select secret test

 Now enter your docker hub password in secret

And enter dockerID in the ID section and save. (Leave the description empty)



Once you have done the above  



Now go to github and create a new project call it Node-jenkins

Enter description of your choice and add Readme and create the project 

Now clone the project to your vscode



-Now in vscode change directory to the project 

-create index.js ,Dockerfile, .gitignore , .dockerignore , jenkinsfile (take sample contents from last node project but make sure the its on port 3500 for both Dockerfile and the application index.js)



Edit your jenkinsfile to reflect  the new pipeline for

-gitcheckout

-Build image

 -push to docker hub



#Now run the following commands



node v

npm init -y

npm install express



# check if the application is working

By running the command below



node index.js



Check on the browser

localhost:3500

NOTE: if u dont run the above commands the localhost wont work on the browser



#If it works then 

‘Press control c

And push all files to GitHub





-Now go back to jenkins dashboard



-Click New item

-enter pipeline  project name

-Check github project and 

-Enter project url  you clone from  GitHub the new project you just created

- click on script drop down and select scm

Enter project url  you clone from  GitHub the new project you just created again(put / after the copied url)
Check if the project its on master or main branch
And edit the accordingly
Make. Sure its posting to jenkinsfile(if u type the jenkinsfile it shows u error when you build simply go to github and copy the jenkinsfile path from there)
Click apply and save
build now

NOTE:if you encounter an error when you build and your console output displays 
+ docker build . -t luchi1985/imag3.0
ERROR: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied

SOLUTION
on vscode ssh to your ec2 instance jenkins server and run the following commands

newgrp docker

 #is used to grant full read, write, and execute permissions to all users for the Docker socket file, which allows unrestricted access to the Docker daemon # and is a significant security risk.

sudo chmod 777 /var/run/docker.sock    




