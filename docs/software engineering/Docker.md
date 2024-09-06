[https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/](https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/)

- [https://docs.docker.com/install/linux/docker-ce/ubuntu/](https://docs.docker.com/install/linux/docker-ce/ubuntu/)  
- [https://docs.docker.com/get-started/part2/](https://docs.docker.com/get-started/part2/)  
- [where are docker images-stored/](http://blog.thoward37.me/articles/where-are-docker-images-stored/)  
- [docker cheatsheet info](https://github.com/wsargent/docker-cheat-sheet\#info)  
- [**Manage Docker as a non-root user**](https://docs.docker.com/install/linux/linux-postinstall/)  
- 

    sudo docker images  
      
sudo curl \-L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname \-s)-$(uname \-m)" \-o /usr/local/bin/docker-compose

sudo chmod \+x /usr/local/bin/docker-compose

sudo docker ps \-s  
sudo docker inspect ContainerID  
to [clean them all](http://stackoverflow.com/a/24277052/274502):   
	docker rm \`docker ps \-aq\`

sudo docker **info**

$ sudo docker **kill** $(sudo docker ps \-aq)

$ sudo docker rm $(sudo docker ps \-aq)

Minimal linux docker \+ autoremove  
$ docker run \-it \--rm [busybox](https://hub.docker.com/\_/busybox)

docker run \-d \-p 8080:80 \--name='myApache' \-v /var/www/html/:/var/www/html httpd  
docker exec \-it myApache bash

docker run \-it busybox  
Ctrl+p \+ ctrl+q  per uscire senza terminarlo 

