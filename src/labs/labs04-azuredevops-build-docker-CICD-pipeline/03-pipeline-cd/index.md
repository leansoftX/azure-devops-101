# 03 使用 Azure DevOps Pipeline流水线完成持续部署配置（发布定义）
#### 通过此练习您将学习如何通过Azure DevOps Server搭建项目快速交付流水线，完成.net core 项目的自动化部署。

## 创建发布定义
### 1. 点击 “版本和发布“，选择“发布”
![](images/createcddefinestep1.png)

### 2. 点击 “新建定义”
![](images/createcddefinestep2.png)

### 3. 选择“空” 模版 点击应用
![](images/createcddefinestep3.png)

### 4. 点击 “添加项目” ，选择源（生成定义）“Voting-CI”，点击添加
![](images/createcddefinestep4.png)

### 5. 修改环境名称为 “DEMO环境”
![](images/createcddefinestep5.png)

### 6. 点击环境的步骤任务
![](images/createcddefinestep6.png)

### 7. 设置代理阶段为 “Linux”
![](images/createcddefinestep7.png)

### 8. 进入“服务”添加SSH连接
![](images/createcddefinestep8.png)
![](images/createcddefinestep8-1.png)
![](images/createcddefinestep8-2.png)
#### 打开 http://devcloudx.com/Templates/29 进入可用环境
![](images/createcddefinestep8-3.png)
#### 双击复制Linux服务器hostname的值，注意不要使用后面的复制键
![](images/createcddefinestep8-4.png)
#### 填写到ssh连接的主机名处，其余参数如下：
|参数|值|
|-|-|
|连接名称|ssh连接|
|端口号|22|
|用户名|azureuser|
|密码或通行证|P2ssw0rd@123|
#### ![](images/createcddefinestep8-5.png)
#### 点击确定创建

### 9. 回到新建发布定义，添加任务“通过SSH复制文件”
![](images/createcddefinestep9.png)
#### 填写参数：
|参数|值|
|-|-|
|版本|0.*|
|显示名称|将文件安全复制到远程计算机|
|SSH 终结点|ssh连接|
|源文件夹|$(System.DefaultWorkingDirectory)/Voting-CI/drop|
|内容|docker-compose-template.yml|
|目标文件夹|/home/azureuser/publish|
#### ![](images/createcddefinestep9-1.png)

### 10. 添加任务“SSH”
![](images/createcddefinestep10.png)
#### 填写参数并保存：
|参数|值|
|-|-|
|版本|0.*|
|显示名称|在远程计算机上运行 shell commands|
|SSH 终结点|ssh连接|
|运行|Commands|
|命令|docker login azuredevops101.azurecr.cn -u azuredevops101 -p 175iY+sEpx16pq0cF2Z0M/izY2DhUHgi <br> docker-compose -f /home/azureuser/publish/docker-compose-template.yml up -d|
|高级-STDERR故障|否|
#### ![](images/createcddefinestep10-1.png)

## 触发持续部署
### 1. 点击“发布”| “创建发布”
![](images/startcdstep1.png)
### 2. 点击“排队”
![](images/startcdstep2.png)
### 3. 点击“Release-1” 查看发布日志：
![](images/startcdstep3click.png)
![](images/startcdstep3log.png)
![](images/startcdstep3status.png)

## 查看发布后的站点
### 1. 打开Linux Server，点击5000端口，如下图所示：
![](images/checkwebsitestep1.png)
### 2. 站点部署成功，如下图所示：
![](images/checkwebsitestep2.png)

## 启动持续编译
### 1. 点击“版本和发布” | “生成”
![](images/startcontinuebuildstep1.png)
### 2. 编辑生产定义
![](images/startcontinuebuildstep2.png)
### 3. 点击 “触发器” | 触发器状态设置为 “已启用” | 点击保存
![](images/startcontinuebuildstep3.png)

## 启动持续发布
### 1. 点击 发布 | 新建发布定义 | 编辑
![](images/startcontinuedeploystep1.png)
### 2. 启动 “持续部署触发器”| 保存
![](images/startcontinuedeploystep2.png)

## 验证持续发布
### 1. 修改master代码代码，验证持续发布
![](images/verifycontinuedeploystep1.png)
### 2. 修改代码，点击提交
![](images/verifycontinuedeploystep2.png)
### 3. 点击“提交”
![](images/verifycontinuedeploystep3.png)
### 4. 点击“版本和发布” | “生成“ | 查看生成进度
![](images/verifycontinuedeploystep4.png)
### 5. 查看部署结果
![](images/verifycontinuedeploystep5.png)
### 6. 刷新应用页面，查看结果
![](images/verifycontinuedeploystep6.png)

#### 恭喜，您已经成功完成了持续部署的搭建