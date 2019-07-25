## Nginx
是一个开源且高性能、可靠的 HTTP 中间件、代理服务。
高效（支持海量并发请求）、可靠的web服务和代理中间件
- 基础篇
  - 快速安装
  - 配置语法
  - 默认模块
  - Nginx 的 log
  - 访问限制
    - HTTP 的请求和连接
    - 请求限制与连接限制
    - access 模块配置语法
    - 请求限制局限性
    - 基本安全认证
    - auth 模块配置语法
    - 安全认证局限性
- 场景实践篇
  - 静态资源 WEB 服务
    - 什么是静态资源
    - 静态资源服务场景
    - 静态资源服务配置
    - 客户端缓存
    - 静态资源压缩
    - 防盗链
    - 跨域访问
  - 代理服务
  - 负载均衡
  - 缓存服务
- 深度学习篇
  - 动静分离
  - rewrite 规则
  - 进阶模块配置
  - HTTPS 服务
    - HTTPS 协议
    - 配置语法
    - Nginx 的 https 服务
    - 苹果要求的 https 服务
  - Nginx 与 LUA 开发
- 架构篇
  - 常见问题
  - Nginx 中间件性能优化
    - 如何调试性能优化
    - 性能优化影响因素
    - 操作系统性能优化
    - Nginx 性能优化
  - Nginx 与安全
  - 新版本特性
  - 中间件架构设计

### 基于 Nginx 的中间件架构
#### 学习环境：
- 系统硬件：CPU >= 2Core, 内存 >= 256M。可以使用自己的服务器、[阿里云](aliyun.com)、vmware、docker
- 操作系统：CentOS>=7.0, 位数 X64、Redhat
环境调试确认：
- 四项确认
  - 确认系统网络
  - 确认 yum 可用
  - 确认关闭 iptables 规则
    - iptables -L 查看是否有规则
    - iptables -F 关闭规则
    - iptables -t nat -L 保险起见再次查看
    - iptables -t nat -F 有的话关闭
  - 确认停用 selinux
    - getenforce 查看是否开启着
    - setenforce 0 关闭
- 两项安装
  - yum -y install gcc gcc-c++ autoconf pcre pcre-devel make automake
  - yum -y install wget httpd-tools vim
- 一次初始化
  - cd /opt;mkdir app download logs work backup

#### 常见的 HTTP 服务
- HTTPD - Apache 基金会
- IIS - 微软
- GWS - Google

#### 为什么选择 nginx
- IO 多路复用 epoll  
2-1~11 6：03