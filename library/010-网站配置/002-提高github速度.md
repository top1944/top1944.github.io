# 修改HOSTS 提高github速度



首先本文解决的问题是Github网站可以访问，但是由于网络代理商的原因，造成访问速度很慢。Ping www.github.com 时，速度只有200多ms。

手动更改hosts. 本文采取方法2。

关于hosts的作用这里就不做声明了。首先更改hosts之前，你得知道修改什么网址对应的hosts。参考上面给出的链接，我主要修改的hosts地址为：github.com 和 github.global.ssl.fastly.net 。查看网站对应的IP地址的方法为访问ipaddress网站，输入网址则可查阅到对应的IP地址。

ipaddress地址：https://www.ipaddress.com/

当前日期下，我查阅到的IP对应为：

151.101.44.249 github.global.ssl.fastly.net  
192.30.253.113 github.com  

## 打开hosts文件

C:\Windows\System32\drivers\etc 

/etc/hosts




修改的Github对应的完整hosts为：

## Github
151.101.44.249 github.global.ssl.fastly.net  
192.30.253.113 github.com  
103.245.222.133 assets-cdn.github.com  
23.235.47.133 assets-cdn.github.com  
203.208.39.104 assets-cdn.github.com  
204.232.175.78 documentcloud.github.com  
204.232.175.94 gist.github.com  
107.21.116.220 help.github.com  
207.97.227.252 nodeload.github.com  
199.27.76.130 raw.github.com  
107.22.3.110 status.github.com  
204.232.175.78 training.github.com  
207.97.227.243 www.github.com  
185.31.16.184 github.global.ssl.fastly.net  
185.31.18.133 avatars0.githubusercontent.com  
185.31.19.133 avatars1.githubusercontent.com  

## 刷新

修改完hosts还不会立即生效，你需要刷新DNS缓存，告诉电脑我的hosts文件已经修改了。

输入指令：sudo /etc/init.d/networking restart 即可。

然后，你关闭浏览器再访问github就不会出现速度很慢的现象了。（亲测不关闭浏览器直接访问也可）



windows下刷新DNS的方法：

打开CMD

输入ipconfig /flushdns


参考链接：

http://www.jianshu.com/p/a578963f10f0

http://blog.csdn.net/wu__di/article/details/50538916

