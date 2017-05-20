---
layout: post
title: Axure 高级功能
date: 2016-06-17
categories: blog
tags: [工具]
---

> 版本：Axure RP 8.0

## 自适应视图 — Adaptive Views

![](https://www.axure.com.cn/wp-content/uploads/2014/08/0-2.jpg)

来个实例，相信大家会有对这个功能会有更直观的感受。

![](http://www.axure.com.cn/wp-content/uploads/auto_save_image/2014/08/085615vWK.jpg)

大家用手机或iPad扫描下上图中的二维码，示例原型页面随设备屏幕大小自适应，PC上输入网址http://8inx6g.axshare.com 也支持集中分辨率的响应变化。

### 步骤演示

#### 1. 设置自适应视图

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views.png)

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views1.png)

#### 2. 启用自适应视图

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views2.png)

#### 3. 编辑每个自适应视图

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views3.png)

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views4.png)

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_adaptive_views5.png)

---

## 母版 — Masters

用Axure制作原型图的时候，有些部件是需要重复使用的。为了方便维护，可以将这些复用部件做成母版，需要调用的时候直接从母版菜单栏拖拽过来（也可以右键“Add to Pages”批量加入）。当你修改母版的时候，所有调用到该母版的页面或区域都会发生相应变动，省去了挨个修改的麻烦。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_masters.png)

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_masters1.png)

---

## 鼠标悬停动效 — 动态折叠菜单

##### 1. 画好菜单栏，并用一个透明的矩形将菜单弹出区域框选（这个矩形一定要有，先不说干什么用，后面你就懂了）。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu.png)

##### 2. 命名好菜单名，拖一个动态面板过来作为鼠标停留在菜单名字上时要弹出的子菜单，双击动态面板进入状态管理，设置好动态面板名和状态，双击状态“显示”。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu1.png)

##### 3. 设置好子菜单样式。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu2.png)

##### 4. 调整动态面板与子菜单大小一致，并隐藏。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu3.png)

##### 5. 选中“菜单1”，双击“OnMouseEnter”。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu4.png)

##### 6. 选中“Show”，选中子菜单动态面板。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu5.png)

##### 7. 选中最开始加的透明矩形，双击“OnMouseEnter”。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu6.png)

##### 8. 选中“Hide”，选中子菜单动态面板。

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_menu7.png)

---

## 鼠标悬停动效 — 文字高亮

##### 1. 在矩形中写好文字，右键设置交互样式

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang.png)

##### 2. 设置选中状态下改变背景色

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang1.png)

##### 3. 给控件添加鼠标移入监听

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang2.png)

##### 4. 鼠标移入控件状态为选中

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang3.png)

##### 5. 给控件添加鼠标移出监听

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang4.png)

##### 6. 鼠标移出控件状态为不选中

![](http://7xsv37.com1.z0.glb.clouddn.com/axure_gaoliang5.png)