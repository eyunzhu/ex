# 积分墙(通过Safari浏览器获取iOS设备UDID) 
### 本文基于在线安装Profile来实现获取UDID 
演示：[用Safari浏览器打开 获取iOS设备UDID ](https://ex.eyunzhu.com/jfq/getUDID)
###### 通过苹果Safari浏览器获取iOS设备UDID步骤 
- 1、在你的Web服务器上创建一个.mobileconfig的XML格式的描述文件； 
- 2、用户在所有操作之前必须通过某个点击操作完成.mobileconfig描述文件的安装； 
- 3、服务器需要的数据，比如：UDID，需要在.mobileconfig描述文件中配置好，以及服务器接收数据的URL地址； 
- 4、当用户设备完成数据的手机后，返回提示给客户端用户
