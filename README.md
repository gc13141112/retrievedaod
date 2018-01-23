# retrievedaod
    因为不同分辨率的产品在轨道方向和扫描线方向的观测点数不同，若把所有波段的数据都放在单一的科学数据集对象中的话，从数据存储角度而言效率是很低的，因此1B产品中只将分辨率相通、光谱性质相同的数据放在同一SDS对象内，称为波段组。
    
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
    搭载于TERRA和AQUA卫星上的MODIS传感器以其独特的通道设计(0.47um、0.66um、1.24um和2.12um),利用短红外通道(2.12um)数据获取可见通道(0.47um和0.66um)地表反射率信息实现地气解耦,成功地应用了暗目标法(Kaufman et al., 1997a, 1997b, 1997c)
