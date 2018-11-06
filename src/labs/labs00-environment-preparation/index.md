# Azure DevOps试用环境激活指南
## 激活试用环境
### 1. 打开DevOps实验室个人用户注册页面
- [个人注册页面 ](https://devcloudx.com/auth/Register/Personal?ClientId=labs&PostBackUrl=http%3A%2F%2Fdevcloudx.com%2Fapi%2Fuser&ClientLoginUrl=http%3A%2F%2Fdevcloudx.com%2Fusers%2Flogin)

### 2. 注册个人用户,点击注册

![](images/reg07.png)

### 3. 输入账号密码点击登录

![](images/reg09.png)

![](images/reg05.png)

### 4. 选择“TFS生产环境“ – 点击“立即获取”
![](images/preparestep2.png)

### 5. 输入邮件里提供给您的邀请码，点击“立即获取”
![](images/preparestep3.png)

### 6. 点击“获取”
![](images/preparestep4.png)

### 7. 点击“立即创建环境”
![](images/preparestep5.png)

### 8. 环境创建中，如下图所示（环境创建大概需要5分钟左右完成，请耐心等待）
![](images/preparestep6.png)

### 9. 创建完成后，点击“进入”
![](images/preparestep7.png)

### 10. 点击下面菜单可以进行环境管理
![](images/preparestep8.png)

### 11. 通过点击以下链接可以分别进入TFS 服务器以及Linux代理服务器
![](images/preparestep9.png)

### 12. TFS服务器进入后，如下图所示
![](images/preparestep10.png)

### 13. Linux服务器进入后，如下图所示：
![](images/preparestep11.png)

##### 恭喜您，您的环境已激活并可用了！接下来创建一个新的Azure DevOps项目。

## 打开已激活的Azure DevOps Server：
### 1.	打开DevOps魔盒：http://devcloudx.com, 使用管理员提供的账号密码登录系统
![](images/createprojectopenserverstep1.png)

### 2.	输入管理员提供的账号密码进行登录（桌子上的纸条）
![](images/createprojectopenserverstep2.png)

### 3.	点击“环境模版” | “TFS2018生产环境“，查看“已激活”的环境列表
![](images/createprojectopenserverstep3.png)

### 4.	选择可用环境，点击进入
![](images/createprojectopenserverstep4.png)

##### 当前页面列出了Azure DevOps Server的环境信息，包括服务器地址，用户名密码等信息，也可以直接通过此页面进行环境管理（开机、关机、销毁等操作）
![](images/createprojectopenserverstep4info.png)

### 5.	点击“远程连接” | “tfs2018”
![](images/createprojectopenserverstep5.png)

### 6.	点击黄色小尖头
![](images/createprojectopenserverstep6.png)

### 7.	点击tfs，打开tfs站点门户
![](images/createprojectopenserverstep7.png)

### 8.	输入Azure DevOps Server账号密码（默认账号:azureuser,默认密码: P2ssw0rd@123）
![](images/createprojectopenserverstep8.png)

## 创建Azure DevOps 项目

### 1. 输入项目项目名称 “TechSummit2018”，保持默认版本控制”Git”, 点击创建
##### 注意：由于环境刚刚启动成功，第一次可能会出现项目创建失败的可能，如出现失败，请重新创建, 错误如下所示：
![](images/createprojectcreatestep1error.png)<br/>![](images/createprojectcreatestep1.png)

### 2. 项目创建完成，如下图所示：
![](images/createprojectcreatestep2.png)

#### 恭喜，您已经成功的创建了一个Azure DevOps项目！