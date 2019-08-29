
# Linux 挂载OSS
## 安装OSSFS
下载安装包: `` wget http://gosspublic.alicdn.com/ossfs/ossfs_1.7.9.3_centos7.0_x86_64.rpm ``
执行命令安装:``yum localinstall ossfs_1.7.9.3_centos7.0_x86_64.rpm -y``

## 使用方法
> 1. 设置bucket name 和 AccessKeyId/Secret信息，将其存放在/etc/passwd-ossfs 文件中，注意这个文件的权限必须正确设置，建议设为640。
语法：`` echo my-bucket:my-access-key-id:my-access-key-secret > /etc/passwd-ossfs
chmod 640 /etc/passwd-ossfs ``
> 2. 创建被挂载文件夹
> 3. 执行挂载

## 挂载示例
> 将`` my-bucket ``这个bucket挂载到`` /tmp/ossfs ``目录下，AccessKeyId是`` faint ``，AccessKeySecret是`` 123 ``，oss endpoint是`` http://oss-cn-hangzhou.aliyuncs.com  ``


`` echo my-bucket:faint:123 > /etc/passwd-ossfs ``（存放bucket信息）
`` chmod 640 /etc/passwd-ossfs ``（设置文件权限）
`` mkdir /tmp/ossfs ``（创建被挂载目录）
`` ossfs my-bucket /tmp/ossfs -ourl=http://oss-cn-hangzhou.aliyuncs.com ``（执行挂载）

---
### 卸载
`` fusermount -u /tmp/ossfs ``

Tips:如果您使用在阿里云购买的云虚拟机主机（ECS）来提供ossfs服务, 您可以使用内网域名，比如在这个例子您可以将oss endpoint 改成oss-cn-hangzhou-internal.aliyuncs.com，这样可以节省带宽方面的费用。

>可能的错误
ossfs: MOUNTPOINT directory /tmp/ossfs is not empty. if you are sure this is safe, can use the 'nonempty' mount option.
意思是：被挂载目录不是空的，里边已经有文件，系统会产生困扰，所以最好避免这种情况的发生。当然如果你确定安全的话就在挂载时加上nonempty命令就可以解决了
命令修改：`` ossfs my-bucket /tmp/ossfs -ourl=http://oss-cn-hangzhou.aliyuncs.com -o nonempty ``
(如果这样强制挂载的话，该目录下原来的文件就会隐藏)
