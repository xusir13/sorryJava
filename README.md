思路是参考[sorry](https://github.com/xtyxtyx/sorry)，原作是ruby写的，我就撸了个java 轮子，加了一点新功能，可以生成小一点的图片

优化点：
* 重构首页，方便移动端和PC端访问
* 首页素材全部CDN，加快加载速度
* 增加精简模式，可以生成几百k的用来做表情
* 将文件剥离出程序，可以动态切换


[Demo点击查看](http://118.24.58.55/)

# sorryJava
sorry的java版本


![](http://ww1.sinaimg.cn/large/6efe8aa1ly1fphaxorc98j211i0nywku.jpg)


# 安装步骤

如果没有自己的服务器，可以去[腾讯云](https://cloud.tencent.com/redirect.php?redirect=1005&cps_key=886212e8dd391ab808f37dd99caa8afb)
里面个人可以申请7天的服务器，如果你是学生，会有更大的惊喜。
选用云服务器后，安装的时候选择7，然后按照下面步骤配好centos环境。

基础环境需要[安装java](https://github.com/li24361/centos_install_common_software_toturial/blob/master/Java.md)

centOS7下ffmpeg安装

	yum install epel-release -y
	rpm --import http://li.nux.ro/download/nux/RPM-GPG-KEY-nux.ro
	rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
    yum install ffmpeg ffmpeg-devel -y


~~centOS7 gifsicle 压缩gif~~，暂时不适用，待后续优化

    ~~yum install gifsicle~~

centOS7安装字体,不安装这个，生成时候会报错

	yum groupinstall "fonts"

在服务器上建立文件夹/opt/site/cache//
下载[template.mp4](http://118.24.58.55/sorry/template.mp4)跟[template.ftl](http://118.24.58.55/sorry/template.ftl)放进去

<b>以上都是必须的</b>


可以直接下载[sorry-java-1.0.0.jar](http://118.24.58.55/sorry-java-1.0.0.jar)
然后服务器上运行
	nohup java -jar sorry-java-1.0.0.jar &

访问 http://ip:8888



### windows环境下
自己研究代码的时候，windos下面需要安装jdk&maven&git&ffmpeg
修改application.properties,换成自己电脑的文件夹

	cache.template.tempPath=/opt/site/cache/

在自己的文件夹下建立sorry文件夹
下载[template.mp4](http://118.24.58.55/sorry/template.mp4)跟[template.ftl](http://118.24.58.55/sorry/template.ftl)放进去

拉取源码

	git clone https://github.com/li24361/sorryJava.git
	
导入ide
	
打包并运行
	
	mvn package -DskipTests
	java -jar sorry-java-1.0.0.jar
	
访问 http://ip:8888
	




