流程  
1.首先去下载基本用的 centos 需要的版本  
  在此基础上安装nginx 建议用包方式安装   
  安装目录路径为/usr/local/nginx  
  可以安装多个版本的nginx  

2.下载基本centos需要版本  
  在此基础上安装php所需要的版本建议用包方式安装  
  安装路径为/usr/local/php  
  可以安装多个版本的php  

3.基本安装完成之后，可以把做好的镜像传到自己的hub.docker.com 
  
	 上传之前 linux 下面 docker login  输入用户名和密码  
	 //必须修改的跟hub.docker.com  版本库fengdejiyi/nginx  一样才行 才能成功 v1 为标签这个随便  
	 docker tag  9a57660eb300 fengdejiyi/nginx:v1   
	 //提交到版本库  
	 docker push  fengdejiyi/nginx:v1     
	 最后 docker logout
  

4.可能的命令为  

//容器变为镜像  614122c0aabb 容器id  nginx:v1 镜像名称  
docker commit -m 'A new image' -a 'zyc' 614122c0aabb nginx:v1   把容器做成镜像
     
 //容器拷贝文件到宿主机上 . 指的的当前目录下所有文件，否则会直接拷贝整个目录 注意 . 很重要  
 docker cp 9c6e771bc33a:/etc/nginx/. /home/docker/nginx/nginx18    

 //宿主机文件拷贝到容器里面  
 docker cp  /home/docker/nginx/nginx18    9c6e771bc33a:/etc/nginx  

//执行完临时容器 试用网完成 立刻消除 什么都不存在  
docker run  -it  --name  tmpnginx --rm c5d48e81b986  /bin/bash    


5.核心步骤  
 nginx 容器里面  

	容器nginx   
	安装文件在/zyc/src   
	安装nginx 目录 /usr/local/nginx/  配置文件在 /usr/local/nginx/conf  
	启动文件  
	/zyc/start.sh  给最大权限  
	 #!/bin/bash  
	/usr/local/nginx/sbin/nginx  
	while (true)  
	do
	 sleep  2
	done
	
	
	/zyc 还有个 www  放nginx 执行文件的地方 
	
	要放出来的目录      给最大权限
	/usr/local/nginx  
	/zyc/www


php 容器类似

	宿主机  
	/home/docker/php/php71      对应不同版本7.1   
	/home/docker/php/php72      对应不同版本7.2  
	/home/docker/php/php73      对应不同版本7.3  
	
	/home/docker/nginx/nginx18    对应不同版本1.8  
	/home/docker/nginx/nginx19     对应不同版本1.9  
	
	/home/docker/www    所有网站根目录
	
	
	注意nginx 配置  还有就是  nginx 访问目录 必须和php访问目录一样  -v /home/docker/www:/zyc/www   否则会出错   
	nginx 启动  
	docker run   --link php71  --name nginx18 -p 7780:80 -d    -v /home/docker/www:/zyc/www -v /home/docker/nginx/nginx18:/usr/local/nginx    648f53ae2a5e   /zyc/start.sh
	
	php 启动  
	docker run --name php71 -p 7790:9000 -d    -v /home/docker/www:/zyc/www  -v  /home/docker/php71:/home/docker/php/php71   17546bfe95dd   /zyc/start.sh  