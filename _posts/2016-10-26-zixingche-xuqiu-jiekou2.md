---
layout: post
title: 行践自行车项目后台接口需求
date: 2016-10-26
categories: work
tags: [接口需求]
---

 版本  | 修订内容                  | 修订日期    |
------|--------------------------|------------|
 V1.0 | 接口描述 | 2016-10-26 |

>优先级高的接口已确定，此文档解释优先级低的接口。

### 行业对比图

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_hangyeduibi.png)

一三五图片上显示真实数据，图可以不变，数据要变化，暂定每3个月统计一次。

第一张图24h文字稍微向上，24h文字下方显示真实数据“在租：xx％”。

第三张图柱状后空白处显示每个站点真实数据“活跃度：xx％”。

第五张图三处指示部分用真实数据替代。

---

### 管理人员－操作日志

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_caozuorizhi.png)

超级管理员功能部分，记录各公司管理员操作记录。

**页面所需字段：**

* 序号
* 时间
* 帐号
* 操作人（改为运营商管理中的运营商）
* 事务描述（事务记录类型：设备入库、设备出库、发卡）

**页面去掉字段：**

* 帐号角色（角色全部是运营商，可以去掉）
* 右上角“全部”选择条去掉

---

### 综合信息－热力图

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_relitu.png)

目前按图示四个级别体现自行车、用户、骑行时间情况，骑行时间单位采用天。

**地图点击效果说明：**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_relitu2.jpg)

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_relitu3.jpg)

类似百度统计地图效果，点击省后可进入省界面选择城市，点击城市后在城市上方弹出信息框，显示自行车、用户、骑行时长、设备使用率信息，点击信息框中的查看详情按钮可跳转热力图统计界面，看到更多数据。考虑到精确到区比较复杂，工作量较大，目前一期统计到市。

---

### 热力图－热力图统计

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_relitutongji.png)

* 车辆类型：环形图方式统计。车辆类型有自行车、助力车。
* 租用时间段：柱状图方式统计。每隔4小时一个跨度。例如6～9时，租车x辆、还车x辆，10～13时，租车x辆、还车x辆，14～17时，租车x辆、还车x辆。
* 租车常用地点：柱状图方式统计。统计借还车站点，体现借车数、还车数、活跃度。活跃度=每个站点车辆租还次数/锁桩数量。
* 人群类型：嵌套环形图方式统计。中间环形统计性别占比，外部环形统计各年龄段占比。**年龄段暂定四个梯度：<18、18～29、30～40、>40。**

---

### 综合信息－服务说明

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_fuwushuoming.png)

此界面功能在于以后为手机提供服务手册、服务说明、用户协议接口。此界面归公司管理员操作，公司管理员以纯文字方式录入。

**页面去掉字段：**

* 浏览量

---

### 用车统计－每日用车

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_meiriyongche.png)

展示所有站点的总体情况，显示当天起往前共7天数据，日期范围可修改再次搜索。

**页面去掉字段：**

* 站点

---

### 用车统计－储车分布图

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_chefenbu.png)

公司管理员在此页面统一设置所有站点报警比（按百分比设置，计算后结果小数部分舍去进1）。此页面设置的最低报警比可用于智能调度算法中的预警值，此页面设置的报警比不作为App站点状态判断依据。

---

### 用车统计－时段分析

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_shiduanfenxi.png)

不改变，体现出高峰期和低谷期即可。

---

### 调度统计

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_diaodutongji.png)

体现站点一年甚至多年来的调度变化，默认统计本年，日期范围可修改（格式：年／月）。

**页面去掉字段：**

* 统计方式（图中调入、调出已经有体现）

---

### 维修统计

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_weixiutongji.png)

自行车下架、上架不好理解，改为在库和在桩。

---

### 发卡统计

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_fakatongji.png)

不是站点发卡，根据发卡软件操作者信息获取到发卡单位。

---

### 调度管理－任务下达

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_diaoduxiada.png)

此页面根据调度算法算出的值生成调度任务，可智能调度也可人工调度。智能调度按算法计算结果每晚12时自动下发第二天的调度任务；人工调度可修改调度算法计算结果，后台调度人员每天早晨手动下发。

---

### 客服管理－任务处理

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_kefurenwu.png)

客服手动录入到系统中，客服任务交接、客服统计数据都源于此处。

事件主题暂定三种类型，保持与客服统计一致：

* 卡、租还异常
* 车辆、锁桩、站点故障举报
* 投诉

---

### 客服管理－我要交班

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_kefujiaoban.png)

交接重点手动填写，紧急事件可在“任务处理”列表中选择未完成的任务。

---

### 客服管理－我要接班

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_houtai_kefujieban.png)

一个小组交接到下一个小组，各组长负责交接，不会有多个小组交接到一个小组的情况。