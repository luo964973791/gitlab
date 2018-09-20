1. 启动gitlab
docker run --name='git' -d -p 8090:80 --restart always -v /usr/local/gitlab/config:/etc/gitlab -v /usr/local/gitlab/logs:/var/log/gitlab -v /usr/local/gitlab/gitlab-rails:/var/opt/gitlab/gitlab-rails -v /usr/local/gitlab/data:/var/opt/gitlab -v /usr/share/zoneinfo/Asia/Shanghai:/etc/localtime:ro gitlab/gitlab-ce:latest
2.进入重启 停掉gitlab
docker exec -it git /bin/bash
gitlab-ctl stop

3.编辑 gitlab.rb 改成自己的ip,注意把#号去掉
vi /etc/gitlab/gitlab.rb
将 # external_url 'GENERATED_EXTERNAL_URL' 改成   external_url 'http://192.168.1.6' 
4.启动gitlab
gitlab-ctl reconfigure && gitlab-ctl restart 

5.退出 git 容器
docker restart git
