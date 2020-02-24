# 2019-nCoV 利用pyecharts实现地图可视化

新型冠状病毒肺炎数据分析报告

数据来源：
腾讯新闻 新型冠状病毒肺炎 疫情实施追踪
 https://news.qq.com/zt2020/page/feiyan.htm#news

数据下载阶段
访问网站发现可以直接访问https://view.inews.qq.com/g2/getOnsInfo?name=disease_h5来获取json格式的数据

使用data.keys()查看数据是什么含义
dict_keys(['lastUpdateTime', 'chinaTotal', 'chinaAdd', 'isShowAdd', 'chinaDayList', 'chinaDayAddList', 'dailyNewAddHistory', 'dailyDeadRateHistory', 'confirmAddRank', 'areaTree', 'articleList’])

‘lastUpdateTime’-最后更新时间 
 'chinaTotal’-全国统计数包含确证、疑似、治愈、死亡
'chinaAdd’-全国较上日新增数
'isShowAdd’-是否 显示新增数
 'chinaDayList’-中国日报表
 'chinaDayAddList’-中国日报地址
'dailyNewAddHistory’-每日记录
'dailyDeadRateHistory’-每日死亡率历史
'confirmAddRank’-确认地址
'areaTree’-国内各地及海外疫情
'articleList’-文章列表

## 要求：处理数据 完成按照省为单位进行疫情分布图。

#获取国内各个 省份详细的数据  数据类型为list
df = data['areaTree'][0]['children’]

#各省份名称list
area = [item['name'] for item in df]

#各省份累计确诊数目list
num = [item['total']['confirm']  for item in df]

## 实现地图可视化
使用pyecharts实现地图可视化V1.0版本,参考https://pyecharts.org/#/zh-cn/geography_charts?id=bmap%ef%bc%9a%e7%99%be%e5%ba%a6%e5%9c%b0%e5%9b%be



- 脚本运行课自动下载当天数据，并保存到文件夹。
- map.html 网页可打开查看。
- Analysis.ipynb 是分析制作流程



