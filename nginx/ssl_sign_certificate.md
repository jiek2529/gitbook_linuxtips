# ssl私签证书

```
Mac nginx install
https://kevinworthington.com/nginx-for-mac-os-x-el-capitan-in-2-minutes/
http://www.codepool.biz/how-to-configure-and-install-nginx-on-mac-os-x.html
http://nginx.org/download/
ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/
http://www.pcre.org/
http://nginx.org/en/docs/configure.html
```

------
Automatically enable HTTPS on your website with EFF's Certbot, deploying Let's Encrypt certificates.
ref: https://certbot.eff.org/

```
> wget https://dl.eff.org/certbot-auto  # 下载到本目录
> chmod a+x ./certbot-auto              # 改权限带execute
> ./certbot-auto --help                 # 查看帮助
> ./certbot-auto certonly --standalone -d jiek.gao.com -d gao.jiek.com -m jiek@icitsoft.com  # 自动启用-d的letsencrypt证书，绑定邮箱为-m
```

------