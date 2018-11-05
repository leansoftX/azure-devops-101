# 01 启用分支保护
##### 通过在master分支上启动分支保护，保障master分支代码可用性。
## 1.点击“代码”| “分支”| master | “分支策略”
![](images/startbranchprotectionstep1.png)
## 2. 启动以下策略：
|策略|说明|
|-|-|
|需要至少数量的审阅者|要求必须经过至少几个人完成代码评审，才能完成此拉取请求|
|查看链接工作项|要求必须添加代码逻辑关联的功能需求，提高追溯性|
|生成验证|要求代码必须通过持续集成，构建成功，才能完成拉取请求合并，保证代码质量|
![](images/startbranchprotectionstep2.png)
## 3. 选择对应的生成定义 “TechSummit2018-CI“
![](images/startbranchprotectionstep3.png)
## 4. 保存更改
![](images/startbranchprotectionstep4.png)