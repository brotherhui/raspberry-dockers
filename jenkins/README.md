please notice that, you should first setup the permission for this folder, otherwise, an FileNotFoundException will thrown when starting 
<pre><code>
sudo -s
chmod 777 /var/jenkins_home
</code></pre>


This is just the jenkins image, no other technical

Commands:
1. build image
<pre><code>
docker stop containerID
docker rm containerID
docker rmi jenkins
docker build -t jenkins .
</code></pre>

2. show running containers
<pre><code>
docker ps
</code></pre>

3. start nginx at behind.
<pre><code>
docker run -d -p 18080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home jenkins
</code></pre>

4. see logs
docker logs {continerid}
</code></pre>

5. see docker images so that you can start
<pre><code>
docker images
</code></pre>

6. stop docker
<pre><code>
docker stop {continerid}
</code></pre>

7. stop all running dockers
<pre><code>
docker stop $(docker ps -a -q)
</code></pre>

#In order to delete all the images with container id <None>
<pre><code>
docker stop $(docker ps -a | grep "Exited" | awk '{print $1 }')
docker rm $(docker ps -a | grep "Exited" | awk '{print $1 }')
docker rmi $(docker images | grep "none" | awk '{print $3}')
</code></pre>

8. See last 1000 line logs
<pre><code>
docker logs -f --tail=1000 {continerid}
</code></pre>

9. enter docker
<pre><code>
docker exec -it {continerid} /bin/bash
</code></pre>

10. exit docker
<pre><code>
ctrl+p ctrl+q / exit
</code></pre>

How to easily use it:
1. start the jenkins.
2. http://xxxx:18080 access it. follow the instruciton to use it.
3. after that change the password to admin/raspberry
Nothing else
