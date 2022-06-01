# OpenHarmony 3.1.1 Release


## 版本概述

当前版本在OpenHarmony 3.1 Release的基础上，更新支持以下能力：

**标准系统基础能力增强**

系统服务管理能力增强，新增添加群组校验机制；电源管理新增支持亮度调节和电池信息查询；Misc软件服务补齐兼容http文件下载接口能力。

位置服务支持基本定位接口能力；窗口支持窗口属性设置；媒体补齐音频焦点、音频解码能力相关接口能力。

网络管理支持以太网连接，新增WebSocket JS API，兼容\@system.fetch和\@system.network接口能力。

**标准系统分布式能力增强**

分布式数据管理支持兼容\@system.storage接口能力。

**标准系统应用程序框架能力增强**

包管理支持查询指定应用是否安装；事件通知实现通知发送和取消的接口能力。

元能力支持FA模型支持查询/设置组件横竖屏状态、组件锁屏显示和组件启动亮屏，新增ANR(Application Not Response)、应用主线程卡死检测等DFX功能，完善部分FA卡片基础能力。

**标准系统应用能力增强**

联系人支持第三方应用调用系统通话能力，提供用户基础通信能力。


## 配套关系

  **表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony | 3.1.1&nbsp;Release | NA | 
| SDK | Ohos_sdk&nbsp;3.1.1&nbsp;Release&nbsp;(API&nbsp;Version&nbsp;8) | NA | 
| HUAWEI&nbsp;DevEco&nbsp;Studio（可选） | 3.0&nbsp;Beta3&nbsp;for&nbsp;OpenHarmony | OpenHarmony应用开发推荐使用 | 
| HUAWEI&nbsp;DevEco&nbsp;Device&nbsp;Tool（可选） | 3.0&nbsp;Release | OpenHarmony智能设备集成开发环境推荐使用 | 


## 源码获取


### 前提条件

1. 注册码云gitee账号。

2. 注册码云SSH公钥，请参考[码云帮助中心](https://gitee.com/help/articles/4191)。

3. 安装[git客户端](https://gitee.com/link?target=https%3A%2F%2Fgit-scm.com%2Fbook%2Fzh%2Fv2%2F%25E8%25B5%25B7%25E6%25AD%25A5-%25E5%25AE%2589%25E8%25A3%2585-Git)和[git-lfs](https://gitee.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading)并配置用户信息。
   
   ```
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 安装码云repo工具，可以执行如下命令。
   
   ```
   curl -s https://gitee.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #如果没有权限，可下载至其他目录，并将其配置到环境变量中chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[码云帮助中心](https://gitee.com/help/articles/4191)）。


```
repo init -u git@gitee.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v3.1.1-Release --no-repo-verify
repo sync -c
repo forall -c 'git lfs pull'
```

**方式二**

通过repo + https 下载。


```
repo init -u https://gitee.com/openharmony/manifest.git -b refs/tags/OpenHarmony-v3.1.1-Release --no-repo-verify
repo sync -c
repo forall -c 'git lfs pull'
```


### 从镜像站点获取

*待补充*


## 更新说明

本版本在OpenHarmony 3.1 Release的基础上有如下变更。


### 特性变更

**表3** 版本新增特性表

  | 子系统名称 | 标准系统 | 轻量、小型系统 | 
| -------- | -------- | -------- |
| 系统服务管理 | 新增添加群组校验机制。<br/>主要涉及如下需求：<br/>I52G5Q&nbsp;添加群组校验机制 | NA | 
| 电源管理 | 实现兼容亮度调节和电池信息查询API接口能力。<br/>主要涉及如下需求：<br/>I526UP&nbsp;支持\@system.brightness亮度调节接口<br/>I526UP&nbsp;支持\@system.battery电池信息查询接口 | NA | 
| 包管理 | 实现查询指定应用是否安装接口能力。<br/>主要涉及如下需求：<br/>I56EWD&nbsp;支持对测试框架的配置<br/>I55RZJ&nbsp;查询指定应用是否安装 | NA | 
| 位置服务 | 实现兼容基本定位API接口能力。<br/>主要涉及如下需求：<br/>I53WFP&nbsp;支持基本定位能力，兼容system&nbsp;API | NA | 
| 元能力 | 实现FA模型支持查询/设置组件横竖屏状态、组件锁屏显示和组件启动亮屏。<br/>主要涉及如下需求：<br/>I56EH7&nbsp;FA模型支持查询/设置组件横竖屏状态<br/>I50D5Y&nbsp;FA模型支持组件锁屏显示<br/>I56EH7&nbsp;FA模型支持组件启动亮屏<br/>I55WB0&nbsp;卡片数据支持携带图片<br/>I55WB0&nbsp;FA卡片能力补齐-formManager重构<br/>I55WB0&nbsp;FA卡片能力补齐-支持卡片状态查询<br/>I55WB0&nbsp;FA卡片能力补齐-支持删除无效卡片<br/>I55WB0&nbsp;FA卡片能力补齐-支持卡片可见状态与更新状态单独设置<br/>I50D8H&nbsp;支持拦截uncatchedexception<br/>I50D91&nbsp;支持ANR(Application&nbsp;Not&nbsp;Response)处理 | NA | 
| 媒体 | 实现音频焦点、音频解码能力相关API接口能力。<br/>主要涉及如下需求：<br/>I56REO&nbsp;音频部件焦点/设备接口OH补齐<br/>I522W0&nbsp;支持amr格式音频编码枚举类型 | NA | 
| 窗口 | 支持对窗口属性进行设置。<br/>主要涉及如下需求：<br/>I56EH7&nbsp;支持窗口属性设置 | NA | 
| 网络管理 | 实现兼容WebSocket、fetch等API接口能力，支持以太网连接。<br/>主要涉及如下需求：<br/>I53CKH&nbsp;支持兼容\@system.fetch<br/>I53CJX&nbsp;支持兼容\@system.network<br/>I53CKT&nbsp;支持WebSocket<br/>I580PC&nbsp;支持以太网连接 | NA | 
| Misc软件服务 | 实现兼容http文件下载API接口能力。<br/>主要涉及如下需求：<br/>I56Q4X&nbsp;支持文件下载接口 | NA | 
| 事件通知 | 实现通知发送和取消的API接口能力。<br/>主要涉及如下需求：<br/>I50EEW&nbsp;通知发送和取消功能的接口能力补齐 | NA | 
| 分布式数据管理 | 实现兼容\@system.storage&nbsp;API接口能力。<br/>主要涉及如下需求：<br/>I56RF3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;支持\@system.storage接口 | NA | 
| 启动恢复 | 实现兼容\@system.device&nbsp;API接口能力。<br/>主要涉及如下需求：<br/>I56GBS&nbsp;支持\@system.device相关API | NA | 
| 应用 | 联系人支持第三方应用调用系统通话能力，提供用户基础通信能力。<br/>主要涉及如下需求：<br/>I58ZQ4&nbsp;联系人支持第三方应用调用系统通话能力 | NA | 

API变更


3.1.1 Release对比3.1 Release API接口无变更。



### 芯片及开发板适配

芯片及开发板适配状态请参考[SIG-Devboard](https://gitee.com/openharmony/community/blob/master/sig/sig-devboard/sig_devboard_cn.md)信息。


## 修复缺陷列表

*待补充*


## 遗留缺陷列表

*待补充*