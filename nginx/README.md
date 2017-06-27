Commands:
1. build image
docker rmi nginx
docker build -t nginx .

2. show running containers
docker ps

3. start nginx at behind.
docker run -d -p 180:80 -v /var/www/html:/var/www/html -v /etc/nginx/sites-available:/etc/nginx/sites-available -v /etc/nginx/conf.d:/etc/nginx/conf.d nginx


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
1. start the nginx.
2. if you just want to see the htmls, put all your html to /var/www/html folder. and use http://xxxx:180/yourfolderandfilepath to access.
3. if you want to update more configs like proxy reverse for nginx.(only 80 port in the docker(which is 180 outside) can be used now if you don't change the dockerfile). To change /etc/nginx/sites-available/default file on the disk.

