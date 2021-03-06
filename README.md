# ⚡ sherlocky-scripts

自己平时常用的一些好的脚本记录下来~可以更便捷的使用


## qiniu_cdn_ssl_cert_auto_renew.py
> 自动将 Let's Encrypt 免费证书，绑定到七牛CDN域名。

### 使用方法
- 脚本使用前置条件：  
系统需要安装好 certbot 工具，且已经申请了对应子域名的证书。

- 七牛 Access Key 配置：  
将七牛的 Access Key 和 Secret Key 分别配置到环境变量``QINIU_ACCESS_KEY``和``QINIU_SECRET_KEY``。

- 安装 python3 环境

- 脚本使用方式：  
``python3 qiniu_cdn_ssl_cert_auto_renew.py xxx.yyy.com``

- 配合 certbot 自动更新命令：  
``certbot renew --cert-name xxx.yyy.com --manual-auth-hook /usr/bin/certbot-alidns --deploy-hook "python3 /opt/bin/qiniu_cdn_ssl_cert_auto_renew.py xxx.yyy.com"``

> 详细使用方法可参考：[使用七牛云 API 上传 letsencrypt SSL 证书并绑定到 CDN](https://halo.sherlocky.com/archives/qiniu-sslcert)

> certbot-auto.go 编译后就是 certbot-alidns

## lazy_find.sh
> 快速搜索（懒人搜索）

### 自定义命令调用脚本
```bash
vim ~/.bashrc
# alias lfind=/opt/bin/lazy_find.sh
:wq
. ~/.bashrc
# 测试
lfind java
# 大小写敏感
lfind -m java
# 搜索指定目录
lfind -p ~ java
```
