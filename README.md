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
