docker network create git
docker-compose up -d
#-------------------------------------
#进入容器
docker exec -it git /bin/bash
gitlab-ctl stop
gitlab-ctl reconfigure
gitlab-ctl restart
exit
#退出容器
#-------------------------------------
docker restart git 
#登录
http://localhost:8888
