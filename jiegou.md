

# ✅ 系统结构关键模块概览

```
cod-saas/
├── public/
│   ├── index.php                     ← 项目入口
│   ├── assets/                       ← 静态资源：JS/CSS/图片
│   ├── .htaccess                     ← Apache 伪静态配置
│   └── installer/                    ← 图形化安装器（仅首次安装用）

├── routes/
│   ├── web.php                       ← 前台商城路由
│   ├── admin.php                     ← 超级管理员后台路由
│   ├── company.php                   ← 公司后台路由
│   ├── employee.php                  ← 员工后台路由
│   └── installer.php                 ← 图形安装流程（仅首次）

├── app/
│   ├── Models/                       ← 数据模型
│   │   ├── User.php                  ← 用户模型（超管/公司/员工）
│   │   ├── Company.php              ← 公司
│   │   ├── Shop.php                 ← 商城
│   │   ├── Domain.php               ← 域名绑定
│   │   ├── Product.php              ← 商品
│   │   ├── Order.php                ← 订单
│   │   ├── FormField.php            ← 动态表单字段
│   │   ├── Employee.php             ← 员工
│   │   └── Permission.php           ← 权限（简化RBAC）

│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/               ← 超管功能控制器
│   │   │   ├── Company/             ← 公司功能控制器
│   │   │   ├── Employee/            ← 员工功能控制器
│   │   │   ├── Shop/                ← 商城前台控制器（表单页、商品页）
│   │   │   └── InstallerController.php ← 图形化安装器控制器
│   │   ├── Middleware/
│   │   │   ├── IdentifyShopFromDomain.php ← 根据域名识别商城
│   │   │   ├── RoleMiddleware.php         ← 按权限访问模块
│   │   └── Requests/                ← 表单验证

│   ├── Services/                    ← 核心服务模块（可选）
│   │   ├── InstallService.php       ← 安装过程逻辑封装
│   │   ├── ShopService.php          ← 商城创建、配置处理
│   │   ├── FormService.php          ← 表单字段处理
│   │   └── NotificationService.php  ← LINE/邮件通知服务

│   └── Helpers/                     ← 小工具/辅助类
│       └── SystemHelper.php

├── database/
│   ├── migrations/                  ← 数据表结构
│   ├── seeders/                     ← 初始管理员、套餐、功能模块
│   └── factories/

├── resources/
│   ├── views/
│   │   ├── installer/               ← 安装器页面
│   │   ├── admin/                   ← 超管后台界面
│   │   ├── company/                 ← 公司后台界面
│   │   ├── employee/                ← 员工后台界面
│   │   ├── shop/                    ← 前端商城页面（商品/表单）
│   │   └── components/              ← 可复用组件（header/footer/card）
│   ├── css/                         ← 页面样式（Tailwind 或纯 CSS）
│   └── js/                          ← 页面交互逻辑（Alpine.js/原生 JS）

├── config/
│   ├── app.php
│   ├── cod_saas.php                 ← 自定义项目配置
│   └── services.php

├── .env.example                     ← 环境配置模板
├── artisan                          ← Laravel 命令行入口
└── composer.json                    ← 项目依赖说明
```

---

# ✅ 模块职责简要说明

| 模块层级                           | 功能职责说明                                    |
| ------------------------------ | ----------------------------------------- |
| **Installer 安装器**              | 浏览器访问 `/install` 图形化安装（自动写 `.env`、建库、建账号） |
| **Admin 超管系统**                 | 管理所有公司、设置功能套餐、查看平台总订单、用量分析                |
| **Company 公司系统**               | 管理自家公司商城、员工、商品、订单、绑定域名、表单字段               |
| **Employee 员工系统**              | 按照权限访问商城数据，增删查改商品/订单                      |
| **Shop 商城前端**                  | 顾客可见的商品页 + 提交表单（COD）                      |
| **中间件 IdentifyShopFromDomain** | 通过访问域名识别商店并注入上下文                          |
| **动态表单字段系统**                   | 每个商品支持不同表单字段，支持选项、必填、排序等                  |
| **权限系统（轻RBAC）**                | 公司可控制员工看到的模块，如订单管理、商品管理、报表                |

