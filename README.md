# jenkin
Jenkins is an open source continuous integration (CI) server. It manages and controls several stages of the software delivery process, including build, documentation, automated testing, packaging, and static code analysis. Jenkins is a highly popular DevOps tool used by thousands of development teams.

# Local lab setup
##  creaing virtual machine using **VirtualBox - oracle** for Windows
      - go to url Virtual_box(https://www.virtualbox.org/wiki/Downloads) and download and install it.
      - creating vertual machine wih linux and centos
        - goto url : https://www.centos.org/download/ and click x86_64 iso mirrors. it is huge file arround 7.5 GB()
      - open virtual box and click on new and hen give name(:jenkins), type(:linux), version(:redhat 64 bit) and click next next create.
      - side bar one virtual machine is created. click on setting > nework > select adapter from atached to Bridged Adater. select Name intel(R)-Wifi.
      - click on start it will ask select start up disk window and select file which we downloaded from centos and click on start
      - click insall centos ,  open wellcome age and select language as english and click on coninue.
      - click on user wih user name and password(jenkins/1234) and done. it will insall and takes some time and once done click on reboot.
      - open cmd inside virtual machine and logine as jenkins and password as 1234.
      - enter below cmd to get the it detail.
        ```ip a```
      - download putty from google with 64 bit(https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
      - install and open putty and add ip adress inside the session and click ssh and save and open
      - login as jenkins/1234 which we created during Vm set up.Make sure that ur vm in start mode.
      - download docker for centos use documentation cmd copy paste in to putty window.
      -  cmds
        ``` sudo systemctl enable docker
            docker ps (some permission issue we can see)
            sudo usermod -aG docker jenkins
            whoami (show the usename)
            logout```
          reoen putty and login again
          cmd ``` docker ps``` works fine wih ou ermission issue.
      - insall docker compose for linux from documentation and execute cmd menioned in doc.
      - cmd
        ``` sudo chmod +x /usr/local/bin/docker-compose
            docker compose``` 
         docker compose installed successfully.
      -  goto google and get docker-jenkins image and copy and paste to putty image it will download.
      - cmd
        ```
        docker images
        docker info l gre -i root
        mkdir jenkins
        pwd
        ll
        mv jenkins/ jenkins_data
        cd jenkins_data
        mkdir jenkins_home```
    - create docker-compose.yml file
        ```
        version: '3'
        services:
          jenkins:
            container_name: jenkins
            image: jenkins/jenkins
            ports:
              - "8080:8080"
            volumes:
              - "$PWD/jenkins_home:/var/jenkins_home"
            networks:
              -net:
        networks:
          net:
          ```
    - cmd
      ```
      id (observer id as 1000)
      sudo chown 1000:1000 jenkins_home -R  (o give root permission to write data)
      docker-compose up -d (i will create services menioned in the docker-compose.yml)
      docker ps (observe the service is created)
      docker logs -f jenkins (see there is some hash code make a note of it.)
      ```
    - go to browser and hit url as ip:8080(192.168.0.232:8080) i will open jenkin window asking for jenkin admin password, Paste hash code binary in log which we saw in putty.
    - install all Plugin.
    - open a window and ask to create admin user.
    - login wih that wih adimin username and password
    - add ip in the hosts file(c:windows/system32/driver/etc/hots as admin mode) 192.168.0.232 jenkins.local
    - cmd to start and stop server
      ```docker-compose stop
      docker-compose start
      docker-compose restart jenkins (restart the service)
      ```

  ## Getting started with jenkins
      
        
        
      
            
      
      
  
