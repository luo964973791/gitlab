## 1.创建网络  
docker network create git  
## 2.启动gitlab  
docker-compose up --build -d 


## 3.进入重启 停掉gitlab  
docker exec -it git /bin/bash  
gitlab-ctl stop

## 4.编辑 gitlab.rb 改成自己的ip,注意把#号去掉  
vi /etc/gitlab/gitlab.rb  
将 # external_url 'GENERATED_EXTERNAL_URL' 改成   external_url 'http://192.168.1.6'  


## 5.启动gitlab  
gitlab-ctl reconfigure && gitlab-ctl restart   

## 6.退出 git 容器  
docker restart git
