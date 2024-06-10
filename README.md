# 解决的问题
宝塔的**Nginx1.18.GMSSL**版本不太行，安装之后SM2、SM3、SM4会报错，提示...too weak。

故障是因为openssl会校验你的加密原理，如果不在白名单中，比如**MD5**、**SHA1**这种已经淘汰的，就会报错。

而SM2、SM3、SM4等国密加密原理并不在openssl 1.x.xx 的支持列表里。

用本脚本安装适配的nginx，可以解决这个问题。让你正常的使用nginx。

# 原理
openssl 3版本已经允许SM2方式，所以我们只需要让nginx引入openssl3.x即可。

# 使用方法

一、先在宝塔面板里面安装一次nginx 1.23。

二、下载nginx.sh（你可以git clone本库，也可以直接下载这个源文件）到**/root**

三、注意关闭网站的运行，执行下面的命令
> wget https://github.com/shhzhang/bt-gmssl-installbash/blob/main/nginx.sh -O nginx.sh
>
> chmod +x nginx.sh
>
> rm -rf /www/server/nginx
>
> sudo bash nginx.sh install 1.23
> 
> rm -rf nginx.sh
>
> reboot

即可。

# 结果
会把你的宝塔的nginx干掉，安装一个1.23版本带GMSSL的新nginx.

Enjoy.

# 参考文献
Linux/Unix openssl 3 使用openssl 3.0 安装nginx nginx-quic【兼容宝塔...  (https://www.bt.cn/bbs/thread-117795-1-1.html)

# 打赏
为了解决这个Bug，肝了13个小时啊草，给我捐一片儿护肝片吧大佬们Orz

只要5.88，就可以给我来一片护肝片Orz

爱发电 (https://afdian.net/a/sayer)
