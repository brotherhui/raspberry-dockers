This is just the php7 image, no other technical

Commands:
1. build image
docker rmi mysql
docker build -t mysql .

2. show running containers
docker ps

3. start nginx at behind.
docker run --restart=always -d -p 13306:3306 -v /var/lib/mysql:/var/lib/mysql mysql

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
1. start the mysql.
2. default username and password--pi/rasperry
Nothing else
