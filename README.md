# retrievedaod
    因为不同分辨率的产品在轨道方向和扫描线方向的观测点数不同，若把所有波段的数据都放在单一的科学数据集对象中的话，从数据存储角度而言效率是很低的，因此1B产品中只将分辨率相通、光谱性质相同的数据放在同一SDS对象内，称为波段组。
    
    http://blog.sina.com.cn/s/blog_7d9087650102vvyw.html
    
    1B产品中的各波段组
    
|                           名称 | 分辨率 | 波段数 | 光谱波段 |
| ------------------------ | ---- | ---- | ---- |
|EV_250_RefSB|250 m|2|1,2|
|EV_500_RefSB|500 m|5|3,4,5,6,7|
|EV_1KM_RefSB|1 km|15|8-19, 26|
|EV_1KM_Emissive|1 km|16|20-25, 27-36|

    “RefSB”指的是太阳光反射波段，而“Emissive”指的是热辐射波段。波段8-19实际上是14个波段，包括13lo, 13hi, 14lo, 14hi（若加上波段26则为15个波段）。
    
    
    表1 MODIS仪器特性和主要用途
|  通  道 | 光谱范围通道1-19(nm), 通道20-36(μm) | 信噪比NE△T | 主要用途 | 分辨率/m |
| ------------------------ | ---- | ---- | ---- | ---- |
| 1 | 620-670 | 128 | 陆地、云边界 | 250 |
| 2 | 841-876 | 201 | 陆地、云边界 | 250 |
| 3 | 459-479 | 243 | 陆地、云特性 | 500 |
| 4 | 545-565 | 228 | 陆地、云特性 | 500 |
| 5 | 1230-1250 | 74 | 陆地、云特性| 500 |
| 6 | 1628-1652 | 275 | 陆地、云特性| 500 |
| 7 | 2105-2135 | 110 | 陆地、云特性 | 500 |
| 8 | 405-420 | 880 | 海洋水色、浮游植物、生物地理、化学 | 1000 |
| 9 | 438-448 | 8380 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 10 | 483-493 | 802 | 海洋水色、浮游植物、生物地理、化学 | 1000 |
| 11 | 526-536 | 754 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 12 | 546-556 | 750 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 13 | 662-672 | 910 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 14 | 673-683 | 1087 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 15 | 743-753 | 586 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 16 | 862-877 | 516 | 海洋水色、浮游植物、生物地理、化学  | 1000 |
| 17 | 890-920 | 167 | 大气水汽  | 1000 |
| 18 | 931-941 | 57 | 大气水汽  | 1000 |
| 19 | 915-965 | 250 | 大气水汽  | 1000 |
| 20 | 3.660-3.840 | 0.05 | 表面、云温度  | 1000 |
| 21 | 3.929-3.989 | 2.00 | 表面、云温度  | 1000 |
| 22 | 3.929-3.989 | 0.07 | 海表面、云温度  | 1000 |
| 23 | 4.020-4.080 | 0.07 | 表面、云温度  | 1000 |
| 24 | 4.433-4.498 | 0.25 | 大气温度  | 1000 |
| 25 | 4.482-4.549 | 0.25 | 大气温度  | 1000 |
| 26 | 1.360-1.390 | 1504 | 卷云、水汽  | 1000 |
| 27 | 6.535-6.895 | 0.25 | 卷云、水汽  | 1000 |
| 28 | 7.175-7.475 | 0.25 | 卷云、水汽  | 1000 |
| 29 | 8.400-8.700 | 0.05 | 卷云、水汽  | 1000 |
| 30 | 9.580-9.880 | 0.25 | 臭氧  | 1000 |
| 31 | 10.780-11.280 | 0.05 | 表面、云温度  | 1000 |
| 32 | 11.770-12.270 | 0.05 | 表面、云温度  | 1000 |
| 33 | 13.185-13.485 | 0.25 | 云顶高度  | 1000 |
| 34 | 13.485-13.785 | 0.25 | 云顶高度  | 1000 |
| 35 | 13.785-14.085 | 0.25 | 云顶高度  | 1000 |
| 36 | 14.085-14.385 | 0.35 | 云顶高度  | 1000 |
# 基于MODIS数据气溶胶光学厚度卫星遥感反演
## 原理与处理流程
    搭载于TERRA和AQUA卫星上的MODIS传感器以其独特的通道设计(0.47um、0.66um、1.24um和2.12um),利用短红外通道(2.12um)数据获取可见通道(0.47um和   
    0.66um)地表反射率信息实现地气解耦,成功地应用了暗目标法(Kaufman et al., 1997a, 1997b, 1997c),并推出了相应的气溶胶产品。本节将以MODIS算法
    为基础,详细介绍暗目标法从MODIS反演陆地气溶胶的流程(王中挺等, 2008)
### 查找表的构建
    查找表是通过设定不同卫星观测几何参数,不同的大气气溶胶参数,考虑要观测数据所在的波段,并考虑不同地表类型等参数,使用6S软件(Kotchenova et al.,
    2006),进行辐射传输计算得出。其中观测参数包括: 9个太阳天顶角为0、6、12、24、35.2、48、54、60和66; 12个观测天顶角0~66, 每个观测角度相隔6;
    16个太阳与卫星之间的相对方位角取值为0~180, 每个方位角相隔12;大气气溶胶模式参数假设为大气气溶胶,并设立6个大气气溶胶光学厚度值(在波长0.55um处)
    ：即0、0.25、0.5、1、1.5、1.95;波长中心波长取0.47um、0.66um和2.1um;地表参数包括海拔为0,地表覆盖类型为植被。这样就组成了9×12×16×6×3=31104
    组不同ρ0、T(μs)T(μv)和S参数组合而成的查找表。
### 数据预处理
    在具体反演过程中, 从MODIS 1km表观反射率产品中读取0.47μm(蓝波段, 第3波段)、0.66μm(红波段, 第1波段)、2.1μm(短波红外波段, 第7波段, 计算NVDI
    需要)和1.24μm(第5波段, 计算NVDI需要)四个波段的表观反射率数据,以及相应的偏移量和定标系数。同时读取几何定标参数(如经纬度、海拔、太阳天顶角、
    太阳方位角、观测天顶角、观测方位角等数据),根据定标系数将相应的数据转换为真是物理值。然后利用海陆掩码文件实现海陆分离,并使用阈值剔除像元,进行
    气溶胶光学厚度的反演。
### 地表反射率函数的确定
    对于城市来说,确定暗像元及暗像元红蓝波段与短波红外波段地表反射率的关系是其中一个重要的技术环节。当像元波长在2.1μm处的表观反射率满足大于0.01
    小于0.4时,该像元可以认为是暗像元。已有研究表明,浓密植被在2.1μ波长处的反射率和在0.47μm、0.66μm波长处的反射率之间的关系,不仅与散射角相关
    (Remer et al., 2005),而且与植被的茂密程度相关。其中散射角可以由观测几何参数获得
            φ = cos-1(-cos)
