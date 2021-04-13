# php-docker

## 目录说明

from-official

官方镜像，有全面的脚本安装拓展，但是pecl有时无法访问导致构建失败,为解决该问题使用自定义镜像

customer 

自定义镜像，从alpine仓库安装php以及拓展，没有时再从pecl装或编译安装