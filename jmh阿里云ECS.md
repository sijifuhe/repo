# 阿里云-ECS

## 一、简介

### 1.什么是ECS

ECS（Elastic Compute Service）是阿里云提供的一种性能卓越、[稳定可靠](https://www.aliyun.com/why-us/reliability)、弹性扩展的IaaS（Infrastructure as a Service）级别云计算服务

。它免去了您采购和维护物理IT硬件的复杂性，使您可以像使用水、电等公共资源一样便捷地获取和使用计算资源，实现 **即开即用** 和 **弹性伸缩** 。

### 核心特点：

1. 虚拟服务器

   ：ECS实例是云上的虚拟服务器，包含vCPU、内存、操作系统、网络和磁盘等基本组件

2. 多样化计算能力

   ：支持x86和ARM架构，覆盖通用计算、异构计算（如GPU实例）和高性能计算等多种场景

3. 弹性灵活

   ：可根据业务需求随时调整资源配置（如计算、存储、网络带宽），并支持定时或按需自动扩缩容

4. 高可靠性

   ：单实例可用性达99.975%，多可用区多实例可用性达99.995%；云盘采用多副本技术，数据可靠性达99.9999999%

5. **成本优化**：提供按量付费、包年包月、抢占式实例等多种计费方式，并结合节省计划和预留实例券进一步降低成本

### 云服务器ECS具有以下特点和优势：

1. **[产品](https://www.aliyun.com/product/list)丰富**
   - 支持x86和ARM两大主流计算架构，满足不同技术架构需求
   - 提供多种实例规格，包括通用计算、异构计算和高性能计算，适应不同业务场景
   - 多种产品形态，如裸金属服务器和专有宿主机DDH，提供无虚拟化损耗的性能体验或独享物理资源的选择
2. **弹性灵活**
   - 支持全球多地域部署，分钟级扩容10000台实例，快速响应业务高峰需求
   - 纵向弹性：可按需调整实例配置（计算、存储、网络带宽等）
   - 横向弹性：通过弹性伸缩实现定时或按负载扩展和缩减实例数量
3. **稳定可靠**
   - 单实例可用性达99.975%，多可用区多实例可用性达99.995%
   - 云盘采用多副本技术，数据可靠性达99.9999999%
   - 支持宕机自动迁移、快照备份和自动告警，确保数据安全
4. **便捷易用**
   - 提供基于Web的用户界面，操作简单直观，方便实例管理和配置
   - 支持镜像一键部署，快速复制环境并扩展
   - 提供多种运维工具（如Terraform、资源编排等），帮助高效管理云资源
5. **安全保障**
   - 提供DDoS防护、端口入侵检测、漏洞扫描和木马查杀等服务，通过多项国际安全认证
   - 支持可信计算、硬件加密和虚拟化加密计算，确保数据安全
6. **成本优化**
   - 提供包年包月、按量付费和抢占式实例三种计费方式，灵活应对不同场景需求
   - 结合节省计划和预留实例券，进一步优化资源使用成本
   - 支持弹性变换计费方式，根据业务变化灵活调整以降低成本

## 二、部署

![image-20250920095626102](./../ECS/image-20250920095626102.png)

![image-20250920095937381](./../ECS/image-20250920095937381.png)

![image-20250920100034042](./../ECS/image-20250920100034042.png)

![image-20250920100453822](./../ECS/image-20250920100453822.png)

![image-20250920100117289](./../ECS/image-20250920100117289.png)

![image-20250920100233068](./../ECS/image-20250920100233068.png)

![image-20250920100506323](./../ECS/image-20250920100506323.png)

**扩容**

![image-20250920100601081](./../ECS/image-20250920100601081.png)

![image-20250920100624886](./../ECS/image-20250920100624886.png)

![image-20250920100722512](./../ECS/image-20250920100722512.png)

![image-20250920100758500](./../ECS/image-20250920100758500.png)

![image-20250920100830306](./../ECS/image-20250920100830306.png)

![image-20250920101040673](./../ECS/image-20250920101040673.png)

![image-20250920101057288](./../ECS/image-20250920101057288.png)

![image-20250920101129568](./../ECS/image-20250920101129568.png)

![image-20250920101247936](./../ECS/image-20250920101247936.png)

![image-20250920101341997](./../ECS/image-20250920101341997.png)

**扩容成功了**

**创建快照**

![image-20250920101452654](./../ECS/image-20250920101452654.png)

![image-20250920101520156](./../ECS/image-20250920101520156.png)

![image-20250920101608714](./../ECS/image-20250920101608714.png)

![image-20250920101617863](./../ECS/image-20250920101617863.png)

**自定义镜像**

![image-20250920101813477](./../ECS/image-20250920101813477.png)

![image-20250920101857867](./../ECS/image-20250920101857867.png)

![image-20250920102531481](./../ECS/image-20250920102531481.png)

![image-20250920102541525](./../ECS/image-20250920102541525.png)

**弹性伸缩**

![image-20250920102628777](./../ECS/image-20250920102628777.png)

![image-20250920102640542](./../ECS/image-20250920102640542.png)

![image-20250920102922517](./../ECS/image-20250920102922517.png)

![image-20250920102929263](./../ECS/image-20250920102929263.png)

![image-20250920102941610](./../ECS/image-20250920102941610.png)	

**搭建LNMP**

![image-20250920103240834](./../ECS/image-20250920103240834.png)

```bash
[root@iZ0jlea3t89oo2w278ltamZ ~]# hostnamectl set-hostname jmh-lnmp
[root@iZ0jlea3t89oo2w278ltamZ ~]# bash
[root@jmh-lnmp ~]# dnf -y install epel-release
[root@jmh-lnmp ~]# dnf -y install nginx
[root@jmh-lnmp ~]# systemctl enable --now nginx.service
```

![image-20250920103331958](./../ECS/image-20250920103331958.png)

![image-20250920103402148](./../ECS/image-20250920103402148.png)

**安装php和MySQL**

```bash
[root@jmh-lnmp ~]# dnf -y install php php-mysqlnd php-fpm php-cli php-gd php-xml php-mbstring php-json
[root@jmh-lnmp ~]# systemctl enable --now php-fpm.service
[root@jmh-lnmp ~]# wget https://dev.mysql.com/get/mysql80-community-release-el8-3.noarch.rpm
[root@jmh-lnmp ~]# rpm -Uvh mysql80-community-release-el8-3.noarch.rpm
[root@jmh-lnmp ~]# yum install -y mysql
```

**编辑nginx配置文件**

```bash
[root@jmh-lnmp ~]# vim /etc/nginx/nginx.conf
# /etc/nginx/nginx.conf
user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

events {
    worker_connections 1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

    access_log /var/log/nginx/access.log main;

    sendfile        on;
    keepalive_timeout  65;

    # 站点配置
    server {
        listen 80;
        server_name _;

        root /var/www/html/wordpress;
        index index.php index.html index.htm;

        location / {
            try_files $uri $uri/ /index.php?$args;
        }

        location ~ \.php$ {
            include fastcgi.conf;
            fastcgi_pass unix:/run/php-fpm/www.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }

        location ~ /\.ht {
            deny all;
        }

        location ~* wp-config.php {
            deny all;
        }

        location ~* \.(jpg|jpeg|gif|png|css|js|ico|xml|webp|woff|woff2|ttf|eot)$ {
            expires max;
            log_not_found off;
        }
    }

    # 可保留 conf.d 目录
    include /etc/nginx/conf.d/*.conf;
}

[root@jmh-lnmp ~]# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
[root@jmh-lnmp ~]# cd /etc/nginx/conf.d/
[root@jmh-lnmp conf.d]# ls
php-fpm.conf
[root@jmh-lnmp conf.d]# mv php-fpm.conf php-fpm.conf.bak
[root@jmh-lnmp conf.d]# systemctl reload nginx.service 
user = nginx
group = nginx
listen = /run/php-fpm/www.sock
listen.owner = nginx
listen.group = nginx
listen.mode = 0660
```

![image-20250920104533736](./../ECS/image-20250920104533736.png)

![image-20250920104624057](./../ECS/image-20250920104624057.png)

![image-20250920104831178](./../ECS/image-20250920104831178.png)

![image-20250920105129317](./../ECS/image-20250920105129317.png)

![image-20250920105204824](./../ECS/image-20250920105204824.png)

![image-20250920105220061](./../ECS/image-20250920105220061.png)

![image-20250920105321061](./../ECS/image-20250920105321061.png)

![image-20250920105409806](./../ECS/image-20250920105409806.png)

![image-20250920105421367](./../ECS/image-20250920105421367.png)

![image-20250920105448916](./../ECS/image-20250920105448916.png)

![image-20250920105542138](./../ECS/image-20250920105542138.png)

**创建数据库wordpressdb**

![image-20250920105643316](./../ECS/image-20250920105643316.png)

![image-20250920105734318](./../ECS/image-20250920105734318.png)

![image-20250920105819401](./../ECS/image-20250920105819401.png)

![image-20250920105937818](./../ECS/image-20250920105937818.png)

![image-20250920105946246](./../ECS/image-20250920105946246.png)

![image-20250920110012528](./../ECS/image-20250920110012528.png)

![image-20250920110032614](./../ECS/image-20250920110032614.png)

![image-20250920110048902](./../ECS/image-20250920110048902.png)

![image-20250920110756771](./../ECS/image-20250920110756771.png)

![image-20250920110810489](./../ECS/image-20250920110810489.png)

**安装wordpressdb**

```bash
[root@jmh-lnmp php-fpm.d]# cd /var/www/html/
[root@jmh-lnmp html]# wget https://cn.wordpress.org/latest-zh_CN.tar.gz
[root@jmh-lnmp html]# tar xf latest-zh_CN.tar.gz
[root@jmh-lnmp html]# mv wordpress/* /var/www/html/wordpress/
[root@jmh-lnmp html]# cd /var/www/html/wordpress/
[root@jmh-lnmp wordpress]# cp wp-config-sample.php wp-config.php

define( 'DB_NAME', 'wordpressdb' );

/** Database username */
define( 'DB_USER', 'jmh_test' );

/** Database password */
define( 'DB_PASSWORD', 'JMHjmh123' );

/** Database hostname */
define( 'DB_HOST', 'rm-0jlzz10o87d3b7c96.mysql.rds.aliyuncs.com' );

```

![image-20250920110854610](./../ECS/image-20250920110854610.png)

访问公网ip  wordpress测试访问

![image-20250920110939779](./../ECS/image-20250920110939779.png)

![image-20250920111042218](./../ECS/image-20250920111042218.png)

![image-20250920111047396](./../ECS/image-20250920111047396.png)

![image-20250920111328124](./../ECS/image-20250920111328124.png)

![image-20250920111345106](./../ECS/image-20250920111345106.png)
