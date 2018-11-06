# 02 使用 Azure DevOps Pipeline流水线完成持续集成配置（生成定义）
#### 通过此练习您将学习如何通过Azure DevOps Server配合Docker 快速搭建.Net Core应用程序的持续集成完成应用的编译打包。
## 创建构建定义
### 1. 点击 “版本和发布” | “生成” | “新定义”
![](images/createcidefinestep1.png)

### 2. 选择空模版，点击应用
![](images/createcidefinestep2.png)

### 3. 设置代理队列为 “Linux” （此代理已预装docker）
![](images/createcidefinestep3.png)

### 4. 构建步骤一：使用Docker命令编译应用并打包镜像
##### 添加任务，搜索“docker“，点击“添加” 
![](images/createcidefinestep4.png)

#####“Docker注册表连接”参数需要一个Docker Registry，在服务中添加：
![](images/createcidefinestep4info1.png)
![](images/createcidefinestep4info2.png)
##### 使用如下表格设置参数：
|参数|值|
|-|-|
|连接名称|acr|
|Docker Registry|azuredevops101.azurecr.cn|
|Docker ID|azuredevops101|
|Password|175iY+sEpx16pq0cF2Z0M/izY2DhUHgi|
![](images/createcidefinestep4info3.png)

##### 回到之前页面，点击Docker注册表连接后面的刷新，选择“acr”
![](images/createcidefinestep4info4.png)
按照如下参数配置：
|参数|值|
|-|-|
|版本|0.*|
|显示名称|Docker Images Package|
|Docker 注册表连接|acr|
|Docker Compose 文件|docker-compose-base.yml|
|指定映像名|否|
|操作|Build service images|
|其他映像标记|$(Build.BuildID)|
##### 其余参数维持原配置
![](images/createcidefinestep4info5.png)

### 5. 构建步骤二：使用Sed命令替换docker编排文件镜像版本
##### 添加任务，搜索“命令行“，点击“添加” ，请按照如下表格设置参数：
|参数|值|说明|
|-|-|-|
|版本：|2*（预览）|命令行版本|
|显示名称：|替换docker template镜像版本|构建步骤显示名称|
|脚本：|sed -i "s/%{Build.BuildId}%/$(Build.BuildId)/g" docker-compose-template.yml|使用sed命令替换docker-compose-template编排文件的部署镜像版本|
![](images/createcidefinestep5.png)

### 6. 构建步骤三：发布生成项目并回传发布文件到Azure DevOps Server
##### 添加任务，搜索“发布”，选择“发布生成项目“ 点击添加，如下图所示：
![](images/createcidefinestep6.png)
##### 请按照如下表格设置参数：
|参数|值|说明|
|-|-|-|
|显示名称：|发布项目:drop|构建步骤显示名称|
|要发布的路径：|docker-compose-template.yml|发布的文件|
|项目名称：|drop|设置文件夹名称|
|项目类型：|Server|回传到Azure DevOps Server|
![](images/createcidefinestep6info.png)

## 触发持续集成
### 1. 点击 “保存和排队
![](images/startcistep1.png)
### 2. 点击“队列”
![](images/startcistep2.png)
### 3. 点击#1，查看生成结果，如下图所示：
![](images/startcistep3.png)
### 4. 查看生成步骤：
##### Note：构建过程可能需要5～7分钟，建议大家在这段时间回顾下上面的练习。
![](images/startcistep4.png)
### 5. 构建完成，如下图所示，点击Build1 查看发布结果
![](images/startcistep5.png)
### 6. 点击 “项目” | “浏览” 查看发布结果
![](images/startcistep6buildresult.png)
##### Note：这里我们发布的包含最新镜像版本的docker-compose编排文件
![](images/startcistep6composefile.png)
##### 在linux服务器中输入 docker images查看持续集成打包好的镜像文件：
![](images/startcistep6images.png)
#### 恭喜，您已经成功完成了持续集成的搭建，持续集成的输出结果是打包好的镜像和yml编排文件，此镜像和yml文件将作为下一步持续部署的输入元素,在下一个练习将完成持续部署的搭建