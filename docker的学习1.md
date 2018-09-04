相关文档
http://blog.csdn.net/tina_ttl/article/details/51372604   安装文档   
http://www.cnblogs.com/dplearning/p/7068891.html      服务自启动  
https://talk.ninghao.net/t/docker-windows/3946       docker 在Windows上修改网页文件不生效（nginx修改nginx.conf）。   
![](https://github.com/zhangyanchong/docker/blob/master/img/docker_6632699440954345236.png)
  
  docker   window上原理(个人见解) 
           docker 在 window 安装一个虚拟机（virtualbox）  虚拟机上有一个最小的的boot2docker.iso 系统 （可以简称宿主机），然后在宿主机上在运行docker 服务，在宿主机上在创建镜像和容器     
              
1  下载     
     https://get.daocloud.io/toolbox/    （支持window7）  
     选择 exe的下载，下载完成后安装 （具体可参考）  
     http://blog.csdn.net/tina_ttl/article/details/51372604  （里面的下载地址支持window10，不支持windows7 ）  
     安装完之后 出现3个图标  （1个为启动图标 2个为虚拟机图标，3 个为 一般用不到）  
 

2    点击 第一个图标 快速启动
    - 打开terminal后，terminal会自动进行一些设置，需要点时间，全部完成后，会出现如下的结果  
 
docker 的学习1（安装） - zhangyanchong - 张艳冲的博客  

 查看docker的版本信息  
  docker info  
3  连接宿主机  （这个比那个快速启动终端，好用 支持vi 还有复制和粘贴 快速终端啥也没有）  
  宿主机装完默认的ip  为 192.168.99.100  
  默认的用户名和密码是： docker/tcuser  
 连接上之后  
 
docker 的学习1（安装） - zhangyanchong - 张艳冲的博客  

4  宿主机操作  (挂载目录 映射到宿主机)  
     1.打开virtualbox 点击设置  
     
docker 的学习1（安装） - zhangyanchong - 张艳冲的博客  

 
 2 添加共享  
 
docker 的学习1（安装） - zhangyanchong - 张艳冲的博客
设置为  自动挂载，固定分配  docker  就是根目录的docker 目录  
 
docker 的学习1（安装） - zhangyanchong - 张艳冲的博客