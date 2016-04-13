---
layout: post
title: 金融指标算法
date: 2016-04-10
categories: blog
tags: [纪录,开发]
---


>去年公司的分析师给出了几项金融指标算法，比常规指标更加好用，受到了大部分用户的认可。可惜金融指标牌照太贵，最终并未能投入到商用，现拿出来分享。

![image-2016-04-10-1](http://7xsv37.com1.z0.glb.clouddn.com/current3.jpg)

此指标名叫双赢线，蓝色区域表示下跌趋势，红色区域表示上涨趋势。算法如下：

	E1:=EMA(CLOSE,3);
	E2:=EMA(CLOSE,5);
	E3:=EMA(CLOSE,8);
	E4:=EMA(CLOSE,10);
	E5:=EMA(CLOSE,12);
	E6:=EMA(CLOSE,20);
	E7:=EMA(CLOSE,30);
	E8:=EMA(CLOSE,35);
	E9:=EMA(CLOSE,40);
	E10:=EMA(CLOSE,45);
	E11:=EMA(CLOSE,50);
	E12:=EMA(CLOSE,60);
	DQ1:=MAX(MAX(MAX(MAX(MAX(E1,E2),E3),E4),E5),E6);
	DQ2:=MIN(MIN(MIN(MIN(MIN(E1,E2),E3),E4),E5),E6);
	CQ1:=MAX(MAX(MAX(MAX(MAX(E7,E8),E9),E10),E11),E12);
	CQ2:=MIN(MIN(MIN(MIN(MIN(E7,E8),E9),E10),E11),E12);
	KFL:=CQ2-DQ1;
	DFL:=DQ2-CQ1;
	DRAWLINE(DFL>=0,DQ2,DFL>=0,CQ1,1);
	DRAWLINE(KFL>=0,DQ1,KFL>=0,CQ2,2);

![image-2016-04-10-2](http://7xsv37.com1.z0.glb.clouddn.com/current4.jpg)

主图指标名叫斯拉瓦均线，副图指标名叫波段之星。斯拉瓦均线上算出了多空参考点；波段之星均线下穿上水平线表示跌势，上穿下水平线表示涨势。两个指标结合使用效果更佳。

斯拉瓦均线即多个周期（3,5,8,13,15,30,35,40,45,50,60）均线的组合，给出代码：

	/**
	 * 生成斯拉瓦均线
	 * @param range 周期
	 */
	public void generateSlav(int range) {
		List<Double> closeList = new ArrayList<Double>();
		for (DataKlineItem item : this.itemList) {
			closeList.add(item.last);
		}
		List<Double> list = this.calcEMA(closeList, range);
		for (int i = 0; i < list.size(); i++) {
			double doub = list.get(i);
			DataKlineItem item = this.itemList.get(i);
			item.indicatorDict.put(item.slavNAME(range), doub);
		}
	}

波段之星算法如下：

	VAR2:=(HIGH+LOW+CLOSE*2)/4;
	VAR3:=EMA(VAR2,21);
	VAR4:=STD(VAR2,21);
	VAR5:=((VAR2-VAR3)/VAR4*100+200)/4;
	VAR6:=(EMA(VAR5,5)-25)*1.56;
	AK: EMA(VAR6,2)*1.22;
	AD1: EMA(AK,2);
	AJ: 3*AK-2*AD1;
	AA:100;
	BB:0;
	CC:80;
	买进: IF(CROSS(AK,AD1),58,20);
	卖出: IF(CROSS(AD1,AK),58,20);