## 操作场景

Datahub 支持接入各种数据源产生的不同类型的数据，统一管理，再分发给下游的离线/在线处理平台，构建清晰的数据通道。

本文以 MongoDB 为例介绍如何在 CKafka 控制台创建数据异步拉取任务，并对任务进行修改配置，帮助您更好地了解数据接入功能。



## 操作步骤

### 创建数据接入任务

1. 登录 [CKafka 控制台](https://console.cloud.tencent.com/ckafka) 。
2. 在左侧导航栏单击**数据流入**，选择好地域后，单击**新建任务**。
3. 在弹窗中数据源类型选择 **异步拉取** > **MongoDB**。
   ![](https://qcloudimg.tencent-cloud.cn/raw/3a16d51db957c46bd2585f9922fb59cb.png)
4. 单击**下一步**，填写任务详情。
![](https://qcloudimg.tencent-cloud.cn/raw/7a6e9da722cbe156e93a15a8ec3d31d0.png)
 - 任务名称：只能包含字母、数字、下划线、"-"、"."。
 - CKafka 实例：选择 CKafka 实例。
 - 目标 CKafak topic：选择数据流入的目标 CKafka topic。
 - 源数据库类型：
    - 腾讯云 MongoDB：选择数据库实例。
    - 自建 MongoDB：选择用户 CLB 实例并指定端口。
 - 用户名：源 MongoDB 的用户名。
 - 密码：源 MongoDB 的密码。
 - database：源 MongoDB 的数据库名，不支持导入 MongoDB 默认数据库数据。
 - collection：源 MongoDB 的集合，默认是监听所有即可，即”“，也可以指定某个集合。
 - 复制存量数据：是否复试源 MongoDB 的存量数据。
5. 单击**提交**，完成任务创建。

   

### 更改数据源和数据目标

1. 登录 [CKafka 控制台](https://console.cloud.tencent.com/ckafka) 。
2. 在左侧导航栏单击**数据接入**，单击目标任务的**ID**，进入任务基本信息页面。
3. 单击**数据源**模块右上角的**更改数据源**，修改数据源信息。
![](https://qcloudimg.tencent-cloud.cn/raw/b2f518530cb7c2d441540d5d99f03869.png)
4. 单击**数据目标**模块右上角的**更改数据目标**，修改数据目标信息。



### 查看监控

1. 登录 [CKafka 控制台](https://console.cloud.tencent.com/ckafka) 。
2. 在左侧导航栏单击**数据接入**，单击目标任务的**ID**，进入任务基本信息页面。
3. 选择**监控**页签，可查看目标 Topic 监控数据。
<table>
    <tr>
        <th>图标</th>
        <th>说明</th>
    </tr>
    <tr>
        <td><img src ="https://main.qcloudimg.com/raw/9ba57bbd3b8ef3efc4f687d63d27a46d.png" style ="margin:0"></td>
        <td>单击可查看监控指标同环比。</td>
    </tr>
    <tr>
        <td><img src ="https://main.qcloudimg.com/raw/34bdbdbdabb7b5720bf17d78c636a4ad.png" style ="margin:0"></td>
        <td>单击可刷新获取最新的监控数据。</td>
    </tr>
    <tr>
        <td><img src ="https://main.qcloudimg.com/raw/8f2bf7f4df9ddd959f0ecb69fdda8e4c.png" style ="margin:0"></td>
        <td>单击可将图表复制到 Dashboard，关于 Dashboard 请参见 <a href="https://cloud.tencent.com/document/product/248/47161">什么是 Dashboard</a>。</td>
    </tr>
    <tr>
        <td><img src ="https://main.qcloudimg.com/raw/af20129df7be46f33ab7d3598f6e9213.png" style ="margin:0"></td>
        <td>勾选后可在图表上显示图例信息。</td>
    </tr>
</table>
 选择分区后，可以查看指定 Partition 的监控数据。
 <img src ="https://qcloudimg.tencent-cloud.cn/raw/3ee5cf22055038671f968749876c960c.png">  
   不选择时默认全部，展示现有的 Topic 级别的监控数据。
	 <img src ="https://qcloudimg.tencent-cloud.cn/raw/c06058596c2c093ba6a54bbe7397713d.png"> 	  


### 暂停任务

在 **[数据接入](https://console.cloud.tencent.com/ckafka/datahub-access)** 页面，单击目标任务的操作栏的**暂停**，可暂停任务。
> ?当您发现数据接入任务影响了 CKafka 正常服务时，可以暂停数据接入。

### 恢复任务

在 **[数据接入](https://console.cloud.tencent.com/ckafka/datahub-access)** 页面，单击目标任务的操作栏的**恢复**，可将暂停任务恢复。

>?处于暂停状态的任务可以重新启动，将继续转储数据。

### 删除任务

在  **[数据接入](https://console.cloud.tencent.com/ckafka/datahub-access)** 页面，单击目标任务的操作栏的**删除**，在二次确认弹窗中单击**确认**，可删除任务。

> ?
> - 删除任务表示停止数据接入并删除任务记录，不会影响到已经转储的数据和相关的 CKafka 实例。
> - 任务一旦删除不可恢复，请您谨慎操作。
