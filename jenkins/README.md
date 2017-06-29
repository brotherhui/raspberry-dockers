please notice that, you should first setup the permission for this folder, otherwise, an FileNotFoundException will thrown when starting 
sudo -s
chmod 777 /var/jenkins_home


This is just the jenkins image, no other technical

Commands:
1. build image
docker stop containerID
docker rm containerID
docker rmi jenkins
docker build -t jenkins .

2. show running containers
docker ps

3. start nginx at behind.
docker run -d -p 18080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home jenkins



4. see logs
docker logs {continerid}

5. see docker images so that you can start
docker images

6. stop docker
docker stop {continerid}

7. stop all running dockers
docker stop $(docker ps -a -q)

#In order to delete all the images with container id <None>
docker stop $(docker ps -a | grep "Exited" | awk '{print $1 }')
docker rm $(docker ps -a | grep "Exited" | awk '{print $1 }')
docker rmi $(docker images | grep "none" | awk '{print $3}')

8. See last 1000 line logs
docker logs -f --tail=1000 {continerid}

9. enter docker
docker exec -it {continerid} /bin/bash

10. exit docker
ctrl+p ctrl+q / exit

How to easily use it:
1. start the jenkins.
2. http://xxxx:18080 access it. follow the instruciton to use it.
3. after that change the password to admin/raspberry
Nothing else
