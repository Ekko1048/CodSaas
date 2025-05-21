

# ✅ 系统结构关键模块概览

```
/project-root
│
├── /public                 # 入口目录，所有请求从这里来（伪静态规则指向index.php）
│   ├── index.php           # 前台商城请求入口
│   ├── admin.php           # 超管后台入口
│   ├── company.php         # 公司后台入口
│   ├── employee.php        # 员工后台入口
│   └── assets/             # 前端资源(js/css/img)
│
├── /config                 # 配置文件目录（数据库、系统配置）
│   └── config.php
│
├── /core                   # 核心类和公共函数库
│   ├── Database.php        # 数据库连接及操作类
│   ├── Auth.php            # 权限验证和登录管理
│   ├── Router.php          # 简单路由处理类
│   ├── Request.php         # 请求数据封装
│   └── Response.php        # 响应封装
│
├── /modules                # 各模块业务逻辑
│   ├── SuperAdmin/         # 超管模块（公司管理、套餐管理等）
│   ├── Company/            # 公司模块（商城管理、员工管理等）
│   ├── Employee/           # 员工模块（订单管理、商品管理等）
│   └── Shop/               # 商城前台模块（商品展示、下单）
│
├── /views                  # 视图文件（模板）
│   ├── admin/
│   ├── company/
│   ├── employee/
│   └── shop/
│
├── /logs                   # 日志文件
│
├── /install                # 安装脚本和流程文件
│
└── .htaccess               # 伪静态配置，所有请求转发到入口文件

```
