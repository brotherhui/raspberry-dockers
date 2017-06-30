This is just the mysql55 image, no other technical

Commands:
1. build image
<pre><code>
docker rmi mysql
docker build -t mysql .
</code></pre>

2. show running containers
<pre><code>
docker ps
</code></pre>

3. start nginx at behind.
<pre><code>
docker run --restart=always -d -p 13306:3306 -v /var/lib/mysql:/var/lib/mysql mysql
</code></pre>

4. see logs
<pre><code>
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
1. start the mysql.
2. default username and password--pi/rasperry
Nothing else
