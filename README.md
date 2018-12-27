## 1.创建网络  
docker network create git  
## 2.启动gitlab  
docker-compose up --build -d 
## 3.修改配置文件
sed -i "s@# external_url 'GENERATED_EXTERNAL_URL'@external_url 'http://192.168.1.96'@g" /usr/local/gitlab/config/gitlab.rb  

## 3.进入重启 停掉gitlab  
docker exec -it git /bin/bash  
gitlab-ctl stop

## 4.编辑 gitlab.rb 改成自己的ip,注意把#号去掉  
vi /etc/gitlab/gitlab.rb  
将 # external_url 'GENERATED_EXTERNAL_URL' 改成   external_url 'http://192.168.1.6'  


## 5.启动gitlab  
gitlab-ctl reconfigure && gitlab-ctl restart && exit  

## 修改第十三行vi /usr/local/gitlab/gitlab-rails/etc/gitlab.yml  
host: 192.168.1.96  

## 6.退出 git 容器  
docker restart git
